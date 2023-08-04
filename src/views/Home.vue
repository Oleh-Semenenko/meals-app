<template>
  <Title>Random meals</Title>
  <Meals :meals="meals" />
</template>

<script setup>
import { onMounted, ref } from "vue";
import axiosClient from "../axiosClient";
import Meals from '../components/Meals.vue'
import Title from "../components/Title.vue";

const meals = ref([]);

onMounted(async () => {
  for (let index = 0; index < 10; index++) {
    axiosClient
      .get("/random.php")
      .then(({ data }) => meals.value.push(data.meals[0]));
  }
});
</script>
