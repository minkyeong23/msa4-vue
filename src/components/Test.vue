<script setup>
import axios from 'axios';
import { ref } from 'vue';

const photo = ref([]);
const baseUrl = 'https://picsum.photos/v2/list';
let page = 1;
const limit = 3;
const loading = ref(false);

async function picSum() {
  if(loading.value) return;
  loading.value = true;
  try {
    const url = `${baseUrl}?page=${page}&limit=${limit}`;
    const res = await axios.get(url);
    photo.value.push(...res.data);
    page++;
  } catch(error) {
    console.log(error);
    } finally {
      loading.value = false;
    }
};
  
function reset() {
  photo.value = [];
  page = 1;
  loading.value = false;
  };
  
</script> 

<template>
<button type="button" @click="picSum">다음</button>
<button type="button" @click="reset">초기화</button>
<div class="container">
  <div class="card" v-for="item in photo" :key="item.id">
    <div class="card-img" :style="{backgroundImage: `url('${item.download_url}')`}"></div>
    <span>{{ `${item.id}: ${item.author}` }}</span>
  </div>
</div>

</template>

<style>

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.container {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
  gap: 10px;
}

.card {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  gap: 10px;
}

.card-img {
  padding-top: 60%;
  background-repeat: no-repeat;
  background-position: center;
  background-size: cover;
}

</style>