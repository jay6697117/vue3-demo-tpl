<template>
  <!-- <HelloWorld :msg="msg" @response="handleResponse" /> -->
  <HelloWorld :msg="msg" @response="val => (msg = val)" />
</template>

<script setup lang="ts">
import { nanoid } from 'nanoid';
import { ref } from 'vue';
import HelloWorld from './components/HelloWorld.vue';
const msg = ref('Hello from parent' + ' - ' + nanoid());
// function handleResponse(val) {
//   console.log('handleResponse val :', val);
//   msg.value = val;
// }
</script>

<style scoped></style>
