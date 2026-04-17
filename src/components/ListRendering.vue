<script setup>
import axios from 'axios';
import { reactive, ref } from 'vue';

const arr = [3, 4, 2, 5];

const data = ref([]);

async function getPicsum() {
  try { 
    const url = 'https://picsum.photos/v2/list?page=5&limit=10';
    const res = await axios.get(url);
    data.value.push(...res.data);
  } catch(error) {
    console.log(error);
  }
}

</script>

<template>
  <h1>리스트 렌더링</h1>
  <button type="button" @click="getPicsum">추가</button>
  <div class="container">
    <div class="card" v-for="item in data" :key="item.id">
      <div class="card-img" :style="{backgroundImage: `url('${item.download_url}')`}"></div>
      <span>{{ item.author }}</span>
    </div>
  </div>

  <div v-for="(val, key) in arr" :key="key">
    <p>{{ val }}</p>
  </div>
  
  <div v-for="value in 5">
    <p>{{ value }}회</p>
  </div>
</template> 

<style scoped>
  .container  {
    padding: 20px;
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