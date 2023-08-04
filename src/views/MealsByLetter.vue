<template>
  <Title>Meals by letter</Title>

  <div>
    <div class="flex flex-wrap gap-2 justify-center">
      <RouterLink
        v-for="letter of letters"
        :key="letter"
        :to="{ name: 'byLetter', params: { letter } }"
        class="hover:text-orange-500 hover:scale-150 hover:rotate-45 hover:origin-center transition-all"
      >
        {{ letter }}
      </RouterLink>
    </div>

    <Meals :meals="meals" />
  </div>
</template>

<script setup>
import { computed, onMounted, watch } from "vue";
import { useRoute } from "vue-router";
import Meals from "../components/Meals.vue";
import Title from "../components/Title.vue";
import store from "../store";

const route = useRoute();
const letters = "ABCDEFGHIJKLMNOPQRSTUVWXYZ".split("");

const meals = computed(() => store.state.mealsByLetter);

watch(route, () => {
  store.dispatch("searchMealsByLetter", route.params.letter);
});
onMounted(() => {
  store.dispatch("searchMealsByLetter", route.params.letter);
});
</script>
