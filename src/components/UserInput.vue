<template>
  <h1>{{ msg }}</h1>
  <button @click="reverseString">颠倒字符串</button>
  <button @click="appendSign">尾后添加!</button>
  <a @click.prevent="alertFn" href="https://cn.vuejs.org/">go vuejs homepage</a>
</template>

<script lang="ts" setup>
import { ref, reactive } from 'vue';
const msg = ref('abcde');

function reverseString() {
  msg.value = msg.value.split('').reverse().join('');
}
function appendSign() {
  const tempArr = msg.value.split('');
  tempArr.push('!');
  msg.value = tempArr.join('');
}
function alertFn() {
  alert(1111);
}
</script>

<style scoped>
h1 {
  margin-bottom: 6px;
}
button {
  display: block;
  margin-bottom: 10px;
}
a {
  color: blue;
}
</style>
