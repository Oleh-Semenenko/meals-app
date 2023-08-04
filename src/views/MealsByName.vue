<template>
  <Title>Meals by name</Title>
  
  <div class="mb-4 max-w-[1280px] mx-auto">
    <input
      type="text"
      class="rounded border-gray-200 w-full"
      placeholder="Search for meals"
      v-model="keyword"
      @change="searchMeals"
    />
  </div>

  <Meals :meals="meals" />
</template>

<script setup>
import { ref, computed, onMounted } from "vue";
import { useRoute } from "vue-router";
import Meals from "../components/Meals.vue";
import Title from "../components/Title.vue";
import store from "../store";

const route = useRoute();

const keyword = ref("");
const meals = computed(() => store.state.searchedMeals);

function searchMeals() {
  if (keyword.value) {
    store.dispatch("searchMeals", keyword.value);
  } else {
    store.commit("setSearchedMeals", []);
  }
  
}

onMounted(() => {
  keyword.value = route.params.name;
  if (keyword.value) {
    searchMeals();
  }
});
</script>
