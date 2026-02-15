<script setup lang="ts">
const fluidCursor = ref(true);
</script>

<template>
  <div>
    <UContainer class="sm:border-x border-default pt-10">
      <AppHeader :links="navLinks" />
      <slot />
      <AppFooter v-model:fluid="fluidCursor" />
    </UContainer>
    <FluidCursor v-if="fluidCursor" class="opacity-85" />
  </div>
</template>
