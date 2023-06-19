<template>
  <div>{{ text2 }} {{ text }}</div>
</template>

<script setup lang="ts">
const props = withDefaults(
  defineProps<{
    text?: string;
    text2?: string;
  }>(),
  {
    text2: "งง",
  }
);
</script>

<style lang="scss" scoped></style>
