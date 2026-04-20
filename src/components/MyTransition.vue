<script setup>
import { ref, Transition } from 'vue';

const flg = ref(false);

</script>

<template>
  <h1>MyTransition 트랜지션</h1>
  <button type="button" @click="flg = !flg">토글</button>
  <Transition name="box">
    <div class="box" v-if="flg"></div>
  </Transition>
</template>

<style>
.box {
  width: 200px;
  height: 200px;
  background-color: #9f9fff;
}

/* 등장 애니매이션 */
.box-enter-from {
  opacity: 0;
}

.box-enter-active {
  transition: opacity 2s ease;
}

.box-enter-to {
  opacity: 1;
}

/* 퇴장 애니매이션 */
.box-leave-from {
  transform: translateX(0);
}

.box-leave-active {
  transition: all 2s;
}

.box-leave-to {
  transform: translateX(150vw);
}
</style>