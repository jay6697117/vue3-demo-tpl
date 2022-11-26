<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router';
</script>

<template>
  <div class="nav">
    <img alt="Vue logo" class="logo" src="@/assets/images/logo.svg" />
    <div class="link">
      <RouterLink class="link-item" to="/">Home</RouterLink>
      <RouterLink class="link-item" to="/about">About</RouterLink>
    </div>
  </div>

  <RouterView />
</template>

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
  width: 80px;
  height: 80px;
}

.nav .link {
  margin-right: 10px;
}

.nav .link .link-item {
  margin-right: 10px;
}
.nav .link .link-item:last-child {
  margin-right: 0;
}
</style>
