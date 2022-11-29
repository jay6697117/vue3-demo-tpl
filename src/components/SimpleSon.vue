<template>
  <div class="son-wrap">
    <h1>我是子组件</h1>
    <div class="item" v-for="item in arr" :key="item.id">
      {{ item.text }}
    </div>
  </div>
</template>
<script lang="ts" setup>
import { ref } from 'vue';
const arr = ref([
  { id: '001', text: 'Vegetables' },
  { id: '002', text: 'Cheese' },
  { id: '003', text: 'Whatever else humans are supposed to eat' }
]);
</script>

<style lang="scss" scoped>
.son-wrap {
  box-sizing: border-box;
  border: 1px solid #aaa;
  padding: 20px;
  background-color: skyblue;

  h1{
    margin-bottom: 10px;
  }

  .item{
    margin-bottom: 10px;
    background-color: rgba(128, 0, 128, 0.6);
  }
}
</style>
