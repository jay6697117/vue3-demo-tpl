<template>
  <div class="container">
    <div>{{ msg }}</div>
    <div class="red" @click="toggleRed" :class="isRed ? 'isRed' : ''">222</div>
    <div>isRed:{{ isRed }}</div>
    <div class="margin-top-bottom bg" @click="toggleColor" :style="{ color: color }">333</div>
    <div>color:{{ color }}</div>
    <div class="margin-top-bottom" @click="toggleColor1" :style="colorStyle">444</div>
    <div>colorStyle:{{ colorStyle }}</div>
  </div>
</template>

<script lang="ts" setup>
import { ref, reactive } from 'vue';
const msg = ref('hello world');
const isRed = ref(true);
const colorBool = ref(false);
const color = ref('green');
let colorStyle = reactive({ color: 'white', 'background-color': 'purple' });
function toggleRed() {
  isRed.value = !isRed.value;
}
function toggleColor() {
  colorBool.value = !colorBool.value;
  color.value = color.value === 'green' ? 'blue' : 'green';
}
function toggleColor1() {
  colorBool.value = !colorBool.value;
  if (colorBool.value) {
    colorStyle.color = 'blue';
    colorStyle['background-color'] = 'darkcyan';
  } else {
    colorStyle.color = 'white';
    colorStyle['background-color'] = 'purple';
  }
}
</script>

<style lang="scss" scoped>
.container {
  min-height: 200px;
  border: 1px solid #eee;
  border-radius: 20px;
  padding: 20px;
  color: rgba(0, 0, 0, 0.459);

  .margin-top-bottom {
    margin: 10px 0;
  }

  .bg {
    background-color: #ccc;
  }

  .isRed {
    color: red;
    background-color: skyblue;
  }

  .color {
    background-color: #eee;
    font-size: 30px;
  }
}
</style>
