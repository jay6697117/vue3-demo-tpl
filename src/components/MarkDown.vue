<template>
  <div class="editor">
    <textarea class="input" :value="input" @input="handleInput"></textarea>
    <div class="output" v-html="output"></div>
  </div>
</template>

<script setup lang="ts">
import { marked } from 'marked';
import { debounce } from 'lodash-es';
import { ref, computed } from 'vue';

const input = ref('# hello');
const output = computed(() => {
  return marked(input.value);
});
const handleInput = debounce((e: { target: { value: string } }) => {
  input.value = e.target.value;
  console.log('input.value 1:', input.value);
  console.log('marked(input.value) 2:', marked(input.value));
  console.log('output.value 3:', output.value);
}, 100);
</script>

<style lang="scss">
code {
  color: blue;
}
</style>

<style lang="scss" scoped>
body {
  margin: 0;
}

.editor {
  height: 100vh;
  display: flex;

  .input,
  .output {
    overflow: auto;
    width: 50%;
    height: 100%;
    box-sizing: border-box;
    padding: 0 20px;
  }

  .input {
    border: none;
    border-right: 1px solid #ccc;
    resize: none;
    outline: none;
    background-color: #f6f6f6;
    font-size: 14px;
    font-family: 'Monaco', courier, monospace;
    padding: 20px;
  }
}
</style>
