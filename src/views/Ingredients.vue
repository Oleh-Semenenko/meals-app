<template>
  <div>
    <Title>Ingredients</Title>

    <input
      type="text"
      class="rounded border-gray-200 w-full mb-4"
      placeholder="Search for ingredients"
      v-model="keyword"
    />
    <RouterLink
      v-for="ingredient of computedIngredients"
      :key="ingredient.idIngredient"
      :to="{
        name: 'byIngredient',
        params: { ingredient: ingredient.strIngredient },
      }"
      class="block bg-white rounded p-3 mb-3 shadow"
    >
      <h3 class="text-2xl font-bold mb-2">{{ ingredient.strIngredient }}</h3>
      <p>{{ ingredient.strDescription }}</p>
    </RouterLink>
  </div>
</template>

<script setup>
import { onMounted, ref, computed } from "vue";
import axiosClient from "../axiosClient";
import Title from "../components/Title.vue";

const ingredients = ref([]);
const keyword = ref("");
const computedIngredients = computed(() => {
  if (!computedIngredients) return ingredients;

  return ingredients.value.filter((i) =>
    i.strIngredient.toLowerCase().includes(keyword.value.toLowerCase())
  );
});

onMounted(() => {
  axiosClient.get("/list.php?i=list").then(({ data }) => {
    ingredients.value = data.meals;
  });
});
</script>
