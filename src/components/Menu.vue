<template>
  <RouterLink
    :to="{ name: 'byName' }"
    class="inline-flex items-center transition-colors hover:text-orange-500"
    active-class="text-orange-500"
  >
    Meals by name
  </RouterLink>
  <RouterLink
    :to="{ name: 'byLetter' }"
    class="inline-flex items-center transition-colors hover:text-orange-500"
    active-class="text-orange-500"
  >
    Meals by letter
  </RouterLink>
  <RouterLink
    :to="{ name: 'ingredients' }"
    class="inline-flex items-center transition-colors hover:text-orange-500"
    active-class="text-orange-500"
  >
    Meals by ingredients
  </RouterLink>
</template>
