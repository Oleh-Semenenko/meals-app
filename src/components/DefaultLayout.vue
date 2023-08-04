<template>
  <div class="h-full">
    <NavBar />
    <main class="container mx-auto px-6"><RouterView /></main>
  </div>
</template>

<script setup>
import NavBar from "./NavBar.vue";
</script>
