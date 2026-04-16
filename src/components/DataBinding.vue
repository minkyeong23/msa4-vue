<script setup>
import { reactive, ref } from 'vue';
// 데이터 타입
// HTML요소와 Vue 인스턴스의 테이터를 동적으로 연결하는 기능

// ref()
// 타입제한 없이 사용할 수 있으나, 프라미티브 타입에 반응적 참조를 위해 사용
// 프라이미티브 타입에 좀 더 나은 성능을 제공
const cnt = ref(0);
// ref 객체의 경우 js에서 접근시, 해당 값은 ref.value프로퍼티로 접근
console.log(cnt. value);

function add() {
  cnt.value++;
}

// reactive()
// 객체만 사용 가능하고, 해당 객체의 반응적 참조를 위해 사용
const info = reactive({
  name: 'hong',
  age: 20
});
console.log(info.name);

const color = ref('blue');

function btnToggle() {
  if(color.value === 'red') {
    color.value = 'blue';
  } else {
    color.value ='red';
  }
}

const id = ref('');
</script>

<template>
  <!-- 하지만 template에서는 해당 객체명 만으로 값에 접근 가능하다 -->
  <h1>데이터 바인딩 {{ cnt }}</h1>
  <button type="button" @click="add">증가</button>
  <button type="button" @click="cnt--">감소</button>
  <h3>{{ `${info.name} : ${info.age}` }}</h3>

  <!-- 태그 속성명 앞에 `:`을 붙이고, 속성값에 데이터 바인딩 객체를 사용 -->
  <h3 class="test" :class="color">태그 속성 값 데이터 바인딩</h3>
  <button type="button" @click="btnToggle">색깔 토글</button>

  <!-- 양방향 데이터 바인딩 -->
   <input type="text" v-model="id">
   <p>{{ id }}</p>
</template>

<style>

.red {
  color: #ff0000;
}
.blue {
  color: #0000ff;
}
.test {
  background-color: beige;
}

</style>

