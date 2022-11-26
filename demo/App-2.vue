<template>
  <form @submit.stop.prevent="addTodo">
    <input v-model="newTodo" />
    <button>Add Todo1</button>
  </form>
  <div>
    <ul v-if="filterTodos && filterTodos.length > 0">
      <li v-for="(todo, index) in filterTodos" :key="todo.id">
        <input type="checkbox" v-model="todo.done" />
        <span :class="{ done: todo.done }">{{ index }} - {{ todo.text }}</span>
        <button @click="removeTodo(todo)">X</button>
      </li>
    </ul>
    <div v-else>空数据～～～</div>
  </div>
  <div>
    <button @click="hideDone">{{ !isHideDone ? '隐藏完成' : '展示所有' }}</button>
    <button @click="doneAll" v-if="filterTodos && filterTodos.length">{{ !isAllDone ? '全选' : '反选' }}</button>
  </div>
</template>

<script setup lang="ts">
import { nanoid } from 'nanoid';
import { reactive, ref, computed } from 'vue';
interface Todos {
  id: string;
  text: string;
  done: boolean;
}

let newTodo = ref('');
let isHideDone = ref(false);
let isAllDone = ref(false);
console.log('newTodo', newTodo);
console.log('isHideDone', isHideDone)
console.log('isAllDone', isAllDone)

let todos = ref([
  { id: nanoid(), text: 'Learn HTML', done: true },
  { id: nanoid(), text: 'Learn JavaScript', done: true },
  { id: nanoid(), text: 'Learn Vue', done: false }
]);
const filterTodos = computed(() => {
  return isHideDone.value
    ? todos.value.filter((item) => {
        return !item.done;
      })
    : todos.value;
});
function addTodo() {
  todos.value.unshift({ id: nanoid(), text: newTodo.value, done: false });
  newTodo.value = '';
}
function removeTodo(todo: Todos) {
  console.log('todo', todo, todo.id);
  todos.value = todos.value.filter((item) => {
    return item.id !== todo.id;
  });
}
function hideDone() {
  isHideDone.value = !isHideDone.value;
}
function doneAll() {
  isAllDone.value = !isAllDone.value;
  isHideDone.value = false;
  todos.value.forEach((element) => {
    isAllDone.value ? (element.done = true) : (element.done = false);
  });
}
</script>

<style>
.done {
  text-decoration: line-through;
}
</style>
