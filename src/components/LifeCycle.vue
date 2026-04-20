<script setup>
import { onBeforeMount, onBeforeUnmount, onBeforeUpdate, onMounted, onUnmounted, onUpdated, ref } from 'vue';

const cnt = ref(0);

onBeforeMount(() => {
  console.log('onBeforeMount', cnt.value);
});

onMounted(() => {
  cnt.value++;
  console.log('onMounted', cnt.value);
});

onBeforeUpdate(() => {
  console.log('onBeforUpdate')
});
onUpdated(() => {
  console.log('onUpdated')
});

onBeforeUnmount(() => {
  console.log('onBeforeUpdate')
})

onUnmounted(() => {
  console.log('onUnMounted')
})
</script>

<template>
  <h1>라이프 사이클: {{ cnt }}</h1>
  <button type="button" @click="cnt++">증가</button>
</template>

<style>

</style>