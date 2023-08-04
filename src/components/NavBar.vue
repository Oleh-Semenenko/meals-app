<template>
  <header class="bg-white shadow h-16 flex justify-between items-stretch gap-4 px-8">
      <RouterLink
        :to="{ name: 'home' }"
        class="inline-flex items-center h-full text-orange-500 text-lg"
      >
        Home
      </RouterLink>

      <div class="flex items-center gap-3 lg:gap-5">
        <RouterLink
          :to="{ name: 'byName' }"
          class="inline-flex items-center h-full transition-colors hover:bg-orange-300 hover:text-white"
          active-class="text-orange-500"
        >
          Meals by name
        </RouterLink>
        <RouterLink
          :to="{ name: 'byLetter' }"
          class="inline-flex items-center h-full transition-colors hover:bg-orange-300 hover:text-white"
          active-class="text-orange-500"
        >
          Meals by letter
        </RouterLink>
        <RouterLink
          :to="{ name: 'ingredients' }"
          class="inline-flex items-center h-full transition-colors hover:bg-orange-300 hover:text-white"
          active-class="text-orange-500"
        >
          Meals by ingredients
        </RouterLink>
      </div>
    </header>
</template>