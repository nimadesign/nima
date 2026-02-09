<script setup lang="ts">
import type { NavigationMenuItem } from '@nuxt/ui'

defineProps<{
  links: NavigationMenuItem[]
}>();

function scrlFn() {
  if (document.body.scrollTop > 50 || document.documentElement.scrollTop > 50) {
    document.getElementById("header")!.style.width = "calc(var(--spacing) * 76)";
  } else {
    document.getElementById("header")!.style.width = "calc(var(--spacing) * 160)";
  }
}

addEventListener("scroll", scrlFn);
</script>

<template>
  <div id="header" class="fixed top-2 sm:top-4 mx-auto left-1/2 transform -translate-x-1/2 z-10 max-w-fit md:max-w-full" style="width: calc(var(--spacing) * 160); transition: 0.4s;">
    <UNavigationMenu
      :items="links"
      variant="link"
      color="neutral"
      class="bg-muted/80 backdrop-blur-sm rounded-full px-2 sm:px-4 border border-muted/50 shadow-lg shadow-neutral-950/5"
      :ui="{
        link: 'px-2 py-1',
        linkLeadingIcon: 'hidden'
      }"
    >
      <template #list-trailing>
        <ColorModeButton />
      </template>
    </UNavigationMenu>
  </div>
</template>
