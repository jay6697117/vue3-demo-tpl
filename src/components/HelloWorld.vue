<template>
  <div class="greetings">
    <h1 class="green">{{ msg }}</h1>
  </div>
</template>

<script setup lang="ts">
const props = defineProps({
  msg: {
    type: String,
    required: false,
    default: 'default string'
  }
});
const emitFn = defineEmits(['response']);
console.log('props 0:', props);
// console.log('props.msg 1:', props.msg);
emitFn('response', 'response msg hahaha');
</script>

<style scoped>
h3 {
  font-size: 1.2rem;
}

.greetings {
  background-color: #ccc;
  border-radius: 40px;
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
}

.greetings h1,
.greetings h3 {
  text-align: center;
}

.greetings .green {
  font-weight: 500;
  font-size: 32px;
  padding: 10px 40px;
  border-radius: 20px;
}

@media (min-width: 1024px) {
  .greetings h1,
  .greetings h3 {
    text-align: left;
  }
}
</style>
