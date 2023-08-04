<template>
  <div>
    <Title>Meals by {{ route.params.ingredient }}</Title>
    <Meals :meals="meals" />
  </div>
</template>

<script setup>
import { onMounted, computed } from "vue";
import { useRoute } from "vue-router";
import Meals from "../components/Meals.vue";
import Title from "../components/Title.vue";
import store from "../store";

const route = useRoute();
const meals = computed(() => store.state.mealsByIngredient);

onMounted(() => {
  store.dispatch("searchMealsByIngredient", route.params.ingredient);
});
</script>
