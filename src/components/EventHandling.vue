<script setup>
import { ref } from 'vue';

const cnt = ref(0);

function resetCnt(num) {
  cnt.value = num;
}
</script>

<template>
  <h1>이벤트 핸들링: {{ cnt }}</h1>
  <button type="button" @mousemove="cnt++">인라인 핸들러</button>
  <button type="button" @click="resetCnt(9)">메소드 핸들러</button>
  <input type="text" @keydown.a="cnt++" v-model="cnt">
</template>

<style>

</style>