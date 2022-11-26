<template>
  <div class="nav">
    <img alt="Vue logo" class="logo" src="@/assets/images/logo.svg" />
    <div class="link">
      <RouterLink
        :style="currentStr === 'home' ? styleObject : ''"
        @click="handleClick('home')"
        class="link-item"
        to="/"
        >Home</RouterLink
      >
      <RouterLink
        :style="currentStr === 'about' ? styleObject : ''"
        @click="handleClick('about')"
        class="link-item"
        to="/about"
        >About</RouterLink
      >
    </div>
  </div>
  <RouterView />
</template>

<script setup lang="ts">
import { ref, reactive } from 'vue';
import { RouterLink, RouterView } from 'vue-router';

const currentStr = ref('home');
const styleObject = reactive({
  color: 'red',
  backgroundColor: '#ccc'
});
function handleClick(val: string) {
  currentStr.value = val;
}
</script>

<style scoped>
.nav {
  margin-bottom: 20px;
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
}

.nav .logo {
  display: block;
  margin-right: 10px;
  width: 60px;
  height: 60px;
}

.nav .link {
  margin-right: 10px;
}

.nav .link .link-item {
  margin-right: 10px;
  padding: 8px 10px;
  border-radius: 4px;
}
.nav .link .link-item:last-child {
  margin-right: 0;
}
</style>
