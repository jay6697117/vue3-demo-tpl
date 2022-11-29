
<template>
  <div class="wrap">
    <h2>Text Input</h2>
  <input v-model="text"> {{ text }}

  <h2>Checkbox</h2>
  <input type="checkbox" id="checkbox" v-model="checked">
  <label for="checkbox">Checked: {{ checked }}</label>

  <!--
    多个复选框可以绑定到
    相同的 v-model 数组
  -->
  <hr>
  <h2>Multi Checkbox</h2>
  <input type="checkbox" id="Jack" value="Jack" v-model="checkedNames">
  <label for="jack">Jack</label>
  <input type="checkbox" id="John" value="John" v-model="checkedNames">
  <label for="john">John</label>
  <input type="checkbox" id="Mike" value="Mike" v-model="checkedNames">
  <label for="mike">Mike</label>
  <p>Checked names: <pre>{{ checkedNames }}</pre></p>
  <hr>

  <h2>Radio</h2>
  <input type="radio" id="One" value="One" v-model="picked">
  <label for="one">One</label>
  <br>
  <input type="radio" id="Two" value="Two" v-model="picked">
  <label for="two">Two</label>
  <br>
  <span>Picked: {{ picked }}</span>
  <hr>

  <h2>Select</h2>
  <select v-model="selected">
    <option disabled value="">Please select one</option>
    <option>A</option>
    <option>B</option>
    <option>C</option>
  </select>
  <span>Selected: {{ selected }}</span>
  <hr>

  <h2>Multi Select: 要按住shift</h2>
  <select v-model="multiSelected" multiple style="width:100px">
    <option>A</option>
    <option>B</option>
    <option>C</option>
  </select>
  <span>Selected: {{ multiSelected }}</span>
  <hr>
  </div>

</template>
<script lang="ts" setup>
import {ref} from 'vue';

const text = ref('111')
const checked = ref(true)
const  checkedNames = ref(['Jack','Mike'])
const picked = ref('One')
const selected = ref('B')
const multiSelected =ref(['A','B'])
</script>

<style lang="scss" scoped>
.wrap {
  padding: 20px;
  background-color: #eee;
}
</style>
