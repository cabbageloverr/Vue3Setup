<script setup lang="ts">
import CardStyle from "./CardStyle.vue"
import type { User} from "@/interface/user"

const props = withDefaults(defineProps<{
  user : User
}>(),{
}) 

</script>
<template>
<div>
<CardStyle class="card-user">
    <p class="name">{{ user.name }}</p>
    <p class="phone">
      Phone: {{ user.phones[0] }}
      <span  alt="plsplspls" class="border tiny" v-if="user.phones.length > 1">
        +{{ user.phones.length - 1 }}</span
      >
    </p>
    <p class="email">Email: {{ user.email }}</p>
  </CardStyle></div>

</template >

<style scoped>
.name {
  font-weight: bold;
  font-size: 12px;
}

.phone {
  font-size: 12px;
  color: rgb(140, 145, 150);
}

.email {
  font-size: 12px;
  color: rgb(140, 145, 150);
  width: 120px;
  overflow: hidden;
  text-overflow: ellipsis; 
}

.tiny {
  border-radius: 2px;
  justify-content: center;
  align-items: center;
  padding: 0px 4px 1px;
  background: #efedff;
  border-radius: 4px;
  color: #5119f0;
}
  
</style>
