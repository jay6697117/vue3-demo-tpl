<template>
  <h1>Latest Vue Core Commits</h1>
  <template v-for="branch in branches">
    <input type="radio" :id="branch" :value="branch" name="branch" v-model="currentBranch" />
    <label :for="branch">{{ branch }}</label
    >&nbsp;
  </template>
  <p>选中分支:&nbsp;&nbsp; {{ currentBranch }}</p>
  <ul>
    <li v-for="{ html_url, sha, author, commit} in (commits as any)">
      <a :href="html_url" target="_blank" class="commit">{{ sha.slice(0, 7) }}</a>
      - <span class="message">{{ truncate(commit.message) }}</span
      ><br />
      by
      <span class="author">
        <a :href="author.html_url" target="_blank">{{ commit.author.name }}</a>
      </span>
      at <span class="date">{{ formatDate(commit.author.date) }}</span>
    </li>
  </ul>
</template>

<script lang="ts" setup>
import { ref, watchEffect } from 'vue';

const API_URL = `https://api.github.com/repos/vuejs/core/commits?per_page=3&sha=`;
const branches = ['main', 'v2-compat', '3.2', 'pnpm'];

const currentBranch = ref(branches[0]);
const commits = ref(null);
console.log('commits.value 1:', commits.value);

watchEffect(async () => {
  // 该 effect 会立即运行，
  // 并且在 currentBranch.value 改变时重新运行
  const url = `${API_URL}${currentBranch.value}`;
  commits.value = await (await fetch(url)).json();
  console.log('commits.value 2:', commits.value);
});

function truncate(v: string | string[]) {
  const newline = v.indexOf('\n');
  return newline > 0 ? v.slice(0, newline) : v;
}

function formatDate(v: string) {
  return v.replace(/T|Z/g, ' ');
}
</script>

<style lang="scss" scoped>
a {
  text-decoration: none;
  color: #42b883;
}

li {
  line-height: 1.5em;
  margin-bottom: 20px;
}

.author,
.date {
  font-weight: bold;
}
</style>
