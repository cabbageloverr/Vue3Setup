<script setup lang="ts"></script>
<template>
  <button class="bt_blue">
    <slot />
  </button>
</template>

<style scoped>
.bt_blue {
  margin-left: 12px;
  padding: 3px 12px;
  width: 110px;
  color: white;
  border: transparent;
  background: #5119f0 !important;
  border-radius: 4px !important;
  transition-duration: 0.4s;
}

.bt_blue:hover {
  background-color: #ffffff !important;
  color: #5119f0 !important;
  border: solid #5119f0 !important;
}
</style>
