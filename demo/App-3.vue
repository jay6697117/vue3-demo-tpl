<template>
  <div ref="p">hello p</div>
  <div ref="q">hello q</div>
</template>

<script setup lang="ts">
import { nanoid } from 'nanoid';
import { ref, onMounted } from 'vue';
const p = ref(null);
const q = ref(null);
console.dir(p.value);
console.dir(q.value);
onMounted(() => {
  console.dir(p.value);
  console.dir(q.value);
  console.log('p.value.textContent:', p.value.textContent);
  console.log('q.value.textContent:', q.value.textContent);
  p.value.textContent = 'hello p 111';
  p.value.style.backgroundColor = '#ccc';
  q.value.textContent = 'hello q 222';
  q.value.style.backgroundColor = 'skyblue';
});
</script>

<style scoped></style>
