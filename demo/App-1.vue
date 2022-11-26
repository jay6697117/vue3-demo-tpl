<template>
  <!-- <h1 :class="titleClass">{{ title }}</h1> -->
  <!-- <button @click="handleClick">count is : {{ count }}</button> -->
  <!-- <input @input="handleInput" :value="msg" type="text" placeholder="hello world" />
  <h1>msg : {{ msg }}</h1>
  <br>
  <input v-model="msg1" type="text" placeholder="hello world 1" />
  <h1>msg1 : {{ msg1 }}</h1> -->
  <!-- <button @click="toggle">toggle</button><span>&nbsp;{{awesome}}</span>
  <h1 class="yes-awesome" v-if="awesome">Vue is awesome!</h1>
  <h1 class="no-awesome" v-else>Oh no 😢</h1> -->
  <form @submit.stop.prevent="addTodo">
    <input v-model="newTodo" />
    <button>Add Todo</button>
  </form>
  <ul v-if="todos && todos.length >0">
    <li v-for="(todo,index) in todos" :key="todo.id">
      <input type="checkbox">
      {{index}} - {{ todo.text }}
      <button @click="removeTodo(todo)">X</button>
    </li>
  </ul>
  <div v-else>空数据～～～</div>
</template>

<script setup lang="ts">
import { nanoid } from 'nanoid';
import { reactive, ref } from 'vue';
/*
1.v-bind
const title = ref('Make me red ～～～');
const titleClass = ref('title');
*/

/*
2.v-ons
const count = ref(0);
function handleClick() {
  count.value += 1;
} */
/*
3.v-models
const msg = ref('');
const msg1 = ref('');
function handleInput(e: any) {
  msg.value = e.target.value;
}
*/
/*
4.条件渲染
const awesome = ref(true);
function toggle() {
  awesome.value = !awesome.value;
}
*/
// 5.列表渲染
// 给每个 todo 对象一个唯一的 id

interface Todos {
  id: string;
  text: string;
}

let newTodo = ref('');
// let todos = reactive([
//   { id: nanoid(), text: 'Learn HTML' },
//   { id: nanoid(), text: 'Learn JavaScript' },
//   { id: nanoid(), text: 'Learn Vue' }
// ]);
let todos = ref([
  { id: nanoid(), text: 'Learn HTML' },
  { id: nanoid(), text: 'Learn JavaScript' },
  { id: nanoid(), text: 'Learn Vue' }
]);

// function addTodo() {
//   todos.unshift({ id: nanoid(), text: newTodo.value });
// }
function addTodo() {
  todos.value.unshift({ id: nanoid(), text: newTodo.value });
  newTodo.value = '';
}

// function removeTodo(todo: Todos) {
//   console.log('todo', todo, todo.id);
//   for (let index = 0; index < todos.length; index++) {
//     const element = todos[index];
//     if(todo.id === element.id){
//       todos.splice(index,1)
//     }
//   }
// }
function removeTodo(todo: Todos) {
  console.log('todo', todo, todo.id);
  todos.value =  todos.value.filter((item) => {
    return item.id !== todo.id;
  })
}
</script>

<style>
/* .title {
  color: red;
  background-color: blue;
  padding: 20px;
  border-radius: 20px;
} */

/* button {
  padding: 8px 20px;
  font-size: 20px;
  border-radius: 10px;
} */

/* .yes-awesome {
  margin-top: 10px;
  padding: 10px;
  color: yellow;
  background-color: rgba(0, 0, 255, 0.4);
  border-radius: 10px;
}
.no-awesome {
  margin-top: 10px;
  padding: 10px;
  color: darkgreen;
  background-color: rgba(255, 0, 0, 0.4);
  border-radius: 10px;
} */

.done {
  text-decoration: line-through;
}
</style>
