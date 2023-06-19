<script setup lang="ts">
import { ref } from "vue";
import UserTable from "./components/UserTable.vue";
import type { User } from "../src/interface/user";




</script>

<template>
  <div id="app">
    <!-- <HelloWorld/> -->
    <UserTable></UserTable>
  </div>
</template>

<style scoped>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  justify-content: center;
 
}
</style>
