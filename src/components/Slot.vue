<script setup>
// 템플릿 컨텐츠를 부모 컴포넌트에서 자식 컴포넌트에 전달하고, 자식 컴포넌트에서 렌더링
import { ref } from 'vue';
import SlotChild from './SlotChild.vue';

const cnt = ref(0);
</script>

<template>
  <h1>슬롯</h1>
  <SlotChild>
    <div>
      <h2>보내줄 슬롯: {{ cnt }}</h2>
      <h3>아아아</h3>
    </div>
  </SlotChild>  
</template>

<style>

</style>