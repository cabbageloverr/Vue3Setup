<script lang="ts" setup>
// const props = defineProps(['modelValue'])
const props = defineProps<{
  modelValue: string
  // bar?: number
}>()

const emit = defineEmits<{
  (e: 'update:modelValue', value: string): void
}>()
</script>

<template>
  <input
    :value="modelValue"
    @input="$emit('update:modelValue', $event.target.value)"
  />
</template>
