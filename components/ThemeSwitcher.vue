<script setup lang="ts">
import { computed } from "vue";

const colorMode = useColorMode();

const isDark = computed({
  get() {
    return colorMode.value === "dark";
  },
  set() {
    colorMode.preference = colorMode.value === "dark" ? "light" : "dark";
  },
});
</script>

<template>
  <ClientOnly>
    <UButton
      class="h-8 w-8 p-0 flex items-center justify-center"
      color="gray"
      variant="ghost"
      aria-label="Theme"
      @click="isDark = !isDark"
    >
      <UIcon v-if="isDark" name="i-heroicons-sun-20-solid" class="size-5" />
      <UIcon v-else name="i-heroicons-moon-20-solid" class="size-5" />
    </UButton>
    <template #fallback>
      <div class="w-8 h-8" />
    </template>
  </ClientOnly>
</template>
