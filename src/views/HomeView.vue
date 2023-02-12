<template>
  <button @click="LoadUser()">ดูรายชื่อสินค้า</button>
  <ul>
    <li v-for="data,i in Data" :key="i">
      {{ data.id }} <br> {{ data.brand }} <br> {{ data.name }}
    </li>
  </ul>
</template>
<script setup lang="ts">
import axios from"axios";
import { ref } from "vue";
const Data = ref();
const url = ref('https://makeup-api.herokuapp.com/api/v1/products.json?brand=maybelline')
function LoadUser() {
    axios
    .get(url.value)
    .then((Response)=>{
        Data.value = Response.data;
    })
    .catch((err) => {
        console.log(err);
    })
}




</script>

<style>
ul{
  margin-left: -40px;

}
ul li{
  border: 1px solid rgb(151, 53, 53);
  list-style: none;

}
</style>
