<script setup>
import { ref, watch } from 'vue';

// 반응형 속성이 변경될 때 마다 감지하고 특정 로직을 실행
const email = ref('');
const flgEmail = ref(true);
const flgIsExcuted = ref(false);

watch(email, () => {
  if(email.value.includes('@')) {
    flgEmail.value = true;
  } else {
    flgEmail.value = false;
  }
  flgIsExcuted.value = true;
});

const pw = ref('');
const pwClass = ref('');

watch(pw, () => {
  if(pw.value.includes('@')) {
    pwClass.value = 'outline-green';
  } else {
    pwClass.value = 'outline-red';
  }
});
</script>

<template>
  <h1>감시자</h1>
  <div v-if="flgIsExcuted">
    <span v-if="flgEmail">O</span>
    <span v-else>X</span>
  </div>
  <input type="text" v-model="email">
  <input type="text" v-model="pw" :class="pwClass">
</template>

<style>
input {
  outline: none;
}

.outline-green {
  border: 2px solid green;
}

.outline-red {
  border: 2px solid red;
}
</style>