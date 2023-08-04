<template>
  <div class="max-w-[800px] mx-auto pb-8">
    <Title>{{ meal.strMeal }}</Title>
    <!-- <h1 class="text-4xl font-bold mb-5">{{ meal.strMeal }}</h1> -->
    <img :src="meal.strMealThumb" :alt="meal.strMeal" class="max-w-full"/>

    <div class="grid grid-cols-1 sm:grid-cols-3 text-lg py-2">
      <div>
        <strong class="font-bold text-orange-500">Category:</strong> {{ meal.strCategory }}
      </div>
      <div><strong class="font-bold text-orange-500">Area:</strong> {{ meal.strArea }}</div>
      <div><strong class="font-bold text-orange-500">Tags:</strong> {{ meal.strTags }}</div>
    </div>

    <div class="my-3">{{ meal.strInstructions }}</div>

    <div class="grid grid-cols-1 sm:grid-cols-2">
      <div>
        <h2 class="text-2xl font-semibold mb-2 text-orange-500">Ingredients</h2>
        <ul>
          <template v-for="(el, idx) of new Array(20)">
            <li v-if="meal[`strIngredient${idx + 1}`]">
              {{ idx + 1 }}. {{ meal[`strIngredient${idx + 1}`] }}
            </li>
          </template>
        </ul>
      </div>
      <div>
        <h2 class="text-2xl font-semibold mb-2 text-orange-500">Measures</h2>
        <ul>
          <template v-for="(el, idx) of new Array(20)">
            <li v-if="meal[`strMeasure${idx + 1}`] && meal[`strMeasure${idx + 1}`] !== ' '">
              {{ idx + 1 }}. {{ meal[`strMeasure${idx + 1}`] }}
            </li>
          </template>
        </ul>
      </div>

      <div class="mt-5">
        <YouTubeButton :href="meal.strYoutube">Go to Youtube</YouTubeButton>
        <a
          :href="meal.strSource"
          target="_blank"
          class="px-3 py-2 ml-3 rounded border-2 border-transparent text-indigo-600 hover:bg-indigo-600 hover:text-white transition-colors"
        >
          View original source
        </a>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from "vue";
import { useRoute } from "vue-router";
import axiosClient from "../axiosClient";
import Title from "../components/Title.vue";
import YouTubeButton from "../components/YouTubeButton.vue";

const route = useRoute();
const meal = ref({});

onMounted(() => {
  axiosClient.get(`/lookup.php?i=${route.params.id}`).then(({ data }) => {
    (meal.value = data.meals[0]) || {};
  });
});
</script>
