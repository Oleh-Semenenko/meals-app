<template>
  <header
    class="bg-white shadow h-16 flex justify-between items-stretch gap-4 px-8"
  >
    <RouterLink
      :to="{ name: 'home' }"
      class="inline-flex items-center h-full text-orange-500 text-lg"
    >
      Home
    </RouterLink>

    <div class="hidden sm:flex items-center gap-3 lg:gap-5">
      <Menu />
    </div>

    <MobMenuIcon
      class="inline-flex self-center hover:fill-orange-500 sm:hidden"
      @click="() => (isMobMenuOpen = true)"
    />
  </header>

  <!-- Mobile menu -->
  <teleport to="#app">
    <div
      v-if="isMobMenuOpen"
      class="fixed h-full w-full bg-[rgba(25,28,38,.7)] z-10 transition-opacity"
    >
      <div
        class="absolute top-0 right-0 z-20 flex flex-col justify-start gap-3 h-full w-1/2 bg-white ml-auto p-6 pr-8"
      >
        <CloseBtn @click="() => (isMobMenuOpen = false)" class="self-end" />
        <Menu />
      </div>
    </div>
  </teleport>
</template>

<script setup>
import { ref, watch } from "vue";
import { useRoute } from "vue-router";
import Menu from "./Menu.vue";
import MobMenuIcon from "../assets/icons/MobMenuIcon.vue";
import CloseBtn from "../assets/icons/CloseBtn.vue";

const isMobMenuOpen = ref(false);

const route = useRoute();
watch(
  () => route.path,
  () => {
    if (isMobMenuOpen.value === true) {
      isMobMenuOpen.value = false;
    }
  }
);
</script>
