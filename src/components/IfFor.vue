<template>
  <div class="container">
    <div class="btns">
      <button @click="toggleList" :disabled="!(list && list.length)">切换列表</button>
      <button @click="pushList">加入一个数字</button>
      <button @click="popList">去掉一个数字</button>
      <button @click="reverseList">倒序排序</button>
    </div>
    <div class="result">list: {{ list }}</div>
    <div class="list" v-if="isShow && list && list.length">
      <p v-for="(item, index) in list" :key="index">
        {{ item }}
      </p>
    </div>
    <div v-else class="list-null">列表为空呢～～～</div>
  </div>
</template>

<script lang="ts" setup>
import { ref } from 'vue';
const isShow = ref(true);
const list = ref([1, 2, 3]);

function toggleList() {
  isShow.value = !isShow.value;
}
function pushList() {
  isShow.value = true;
  const tempArr = list.value;
  tempArr.push(list.value.length + 1);
  list.value = tempArr;
}
function popList() {
  isShow.value = true;
  const tempArr = list.value;
  tempArr.pop();
  list.value = tempArr;
}
function reverseList() {
  isShow.value = true;
  const tempArr = list.value;
  tempArr.reverse();
  list.value = tempArr;
}
</script>

<style lang="scss" scoped>
.container {
  .btns {
    button {
      margin-right: 10px;
      padding: 2px 10px;
    }
  }
  .result {
    margin: 20px 0;
    background-color: #ccc;
    padding: 6px 10px;
  }
  .list {
    p {
      margin-bottom: 10px;
      background-color: rgba(0, 139, 139, 0.5);
      padding: 6px 10px;
    }
  }
}
</style>
