<template>
  <ChildComp>信息: {{ msg }}</ChildComp>
</template>

<script setup lang="ts">
import { nanoid } from 'nanoid';
import { ref } from 'vue';
import ChildComp from '@/components/ChildComp.vue';

let msg = ref(nanoid());
</script>

<style scoped></style>
