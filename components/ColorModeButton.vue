<script setup lang="ts">
const colorMode = useColorMode();
const isDark = computed({
  get() {
    return colorMode.value === "dark"
  },
  set() {
    colorMode.preference = colorMode.value === "dark" ? "light" : "dark"
  }
});
</script>

<template>
  <ClientOnly>
    <UButton :icon="isDark ? 'i-heroicons-moon-20-solid' : 'i-heroicons-sun-20-solid'"
             color="gray"
             variant="ghost"
             :aria-label="`Use ${isDark ? 'light' : 'dark'} theme`"
             @click="isDark = !isDark"
             class="cursor-pointer" />

    <template #fallback>
      <div class="w-8 h-8" />
    </template>
  </ClientOnly>
</template>