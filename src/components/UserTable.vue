<script setup lang="ts">
import { ref, watch, reactive, onMounted, computed  } from "vue";
import type { User } from "@/interface/user";
import CardStyle from "./CardStyle.vue";
import CardUser from "./CardUser.vue";
import Input from "./input/Input.vue"
import Button from "./button/Button.vue"



async function getData() {
  const res = await fetch("http://localhost:3000/users");
  const finalRes = await res.json();
  users.value = finalRes;
  console.log("load sucsess")
}


async function loadData() {
  await getData();
  result.value = search();
}
const users = ref<User[]>([])
const result = ref<User[]>([])
const text = ref('')


function findInArr(array: string[], keyword: string) {
  for (let i = 0; i < array.length; i++) {
    const item = array[i];
    if (item.startsWith(keyword)) {
      return true;
    }
  }
  return false;
}


  const search = () => {
    return users.value.filter(
      (item) =>
        findInArr(item.phones, text.value) ||
        item.name.toLowerCase().includes(text.value.toLowerCase()) ||
        item.email.toLowerCase().includes(text.value.toLowerCase())
    );
  };


watch(
  () => text.value,
  () => {
    result.value = search();
    
  },{
  }
);

loadData()

</script>

<template>
  <div>
  
  <CardStyle class="container con1">
  <Input v-model="text" />
  <Button @click="search" v-model="text">Search</Button>
    <h3 class="result">
      Result <span class="text_gray">({{ result.length }})</span>
    </h3>

    <div class="row gap-4">
      <CardUser
        :user="user"
        v-for="user in result"
        :key="user.name"
        class="col-3 user-table"
      >
      </CardUser>
    </div>
 
  </CardStyle>
</div>
</template>

<style scoped>
.con1 {
  position: absolute;
  width: 1096px;
  height: auto;
  left: 5%;
  top: 86px;
  background: #ffffff;
  box-shadow: 1px 1px 6px rgba(69, 73, 87, 0.12) !important;
  border-radius: 8px;
  padding: 24px !important;
}



.s_bt:hover {
  background-color: rgb(135, 108, 230) !important;
}

.result {
  margin-top: 1rem;
  font-weight: bold;
}

.row {
  margin-left: 0 !important;
}
.text_gray {
  color: #646d78;
}

.user-table {
  width: 22% !important;
  
  line-height: 10px !important;
}




</style>
