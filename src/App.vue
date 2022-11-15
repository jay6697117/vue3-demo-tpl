<template>
  <HelloWorld :msg="msg" />
</template>

<script setup lang="ts">
import { nanoid } from 'nanoid';
import { ref } from 'vue';
import HelloWorld from './components/HelloWorld.vue';
const msg = ref('Hello from parent' + ' - ' + nanoid());
</script>

<style scoped></style>
