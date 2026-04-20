<script setup>
// Rrops 프롭스:
// 부모 컴포넌트에서 자식 컴포넌트로 데이터를 전달하는 사용자 정의 속성
// 기본 Readonly, 단방향 데이터 바인딩을 형성
import { ref } from 'vue';
import PropsChild from './PropsChild.vue';

const cnt = ref(0);

// Component Event 컴포넌트 이벤트:
// `$emit` 메소드를 사용해서 부모 컴포넌트와 자식 컴포넌트 간에 이벤트를 수신 or 발신
// - 부모 컴포넌트는 `v-on`을 사용하여 수신
//  - `@이벤트명="실행할 js 코드"` 자식 컴포넌트 태그 속성으로 추가
// - 자식 컴포넌트에서는 `$emit('이벤트명')`으로 발신
//  - 아규먼트가 복수일 경우 가변 파라미터로 작성 `$emit('이벤트명'[...아규먼트])`
function minusCnt(num) {
  cnt.value -= num;
}
</script>

<template>
  <h1>프롭스: {{ cnt }}</h1>
  <button type="button" @click="cnt++">증가(부모쪽)</button>

  <!-- 자식 컴포넌트에 `:키="값" 으로 이루어진 props 속성을 부여 -->
  <PropsChild :cnt="cnt" :page="1" @minusCnt="minusCnt"/>
</template>

<style scoped>

</style>