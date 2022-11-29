<template>
  <div class="wrap">
    <h1>我是父组件</h1>
    <SimpleSon />
  </div>
</template>
<script lang="ts" setup>
import { ref } from 'vue';
import SimpleSon from './SimpleSon.vue';
</script>

<style lang="scss" scoped>
.wrap {
  padding: 40px;
  background-color: darkcyan;

  h1{
    margin-bottom: 20px;
  }
}
</style>
