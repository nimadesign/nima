<script setup lang="ts">
import { computed } from "vue";

const props = defineProps<{ fluid: boolean }>();
const emit = defineEmits<(e: "update:fluid", value: boolean) => void>();

const fluidModel = computed({
  get: () => props.fluid,
  set: (v: boolean) => emit("update:fluid", v),
});

const { footer } = useAppConfig();
</script>

<template>
  <UFooter class="z-10 bg-default" :ui="{ left: 'text-muted text-xs' }">
    <template #left>
      {{ footer.credits }}
    </template>

    <template #right>
      <template v-if="footer?.links">
        <UButton
          v-for="(link, index) of footer?.links"
          :key="index"
          v-bind="{ size: 'xs', color: 'neutral', variant: 'ghost', ...link }"
        />
        <USwitch
          v-model="fluidModel"
          label="Fluid Cursor"
          color="neutral"
          variant="ghost"
          class="ml-2"
          unchecked-icon="i-lucide-x"
          checked-icon="i-lucide-check"
        />
      </template>
    </template>
  </UFooter>
</template>
