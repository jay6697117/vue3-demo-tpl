<template>
  <p>todoId: {{ todoId }}</p>
  <button @click="todoIdAdd">todoId add</button>
  <p v-if="!todoData">Loading...</p>
  <pre v-else>{{ todoData }}</pre>
</template>

<script setup lang="ts">
import { nanoid } from 'nanoid';
import { ref } from 'vue';
let todoId = ref(1);
const todoData = ref(null);

function todoIdAdd(): void {
  todoId.value = Math.floor(Math.random()*10+1);
  fetchData();
}
async function fetchData(): Promise<void> {
  todoData.value = null;
  const res = await fetch(`https://jsonplaceholder.typicode.com/todos/${todoId.value}`);
  todoData.value = await res.json();
}
fetchData();
</script>

<style scoped></style>
