<template>
  <h1>🎉 Congratulations!</h1>
  <div class="btn-wrap">
    <button @click="showConfetti">喝彩</button>
  </div>
</template>

<script setup lang="ts">
import { nanoid } from 'nanoid';
import JSConfetti from 'js-confetti';
import { ref } from 'vue';
const confetti = new JSConfetti();

function showConfetti() {
  confetti.addConfetti();
}

showConfetti();
</script>

<style scoped>
h1 {
  text-align: center;
  cursor: pointer;
  margin-top: 3em;
}

.btn-wrap {
  width: 100%;
  text-align: center;
}

button {
  margin-top: 100px;
  padding: 2px 20px;
}
</style>
