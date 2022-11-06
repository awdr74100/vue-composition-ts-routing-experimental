<template>
  <ul>
    <li v-for="(path, index) in paths" :key="index">
      <RouterLink :to="path">{{ path }}</RouterLink>
    </li>
  </ul>
</template>

<script setup lang="ts">
import { RouterLink } from 'vue-router/auto';

const paths = ['/', '/about', '/users', '/users/1', '/users/2'];
</script>

<style scoped>
ul {
  display: flex;
}

a {
  text-decoration: none;
  background-color: rgb(87, 87, 87);
  color: #fff;
  padding: 6px 12px;
  display: inline-block;
  border-radius: 5px;
  margin-right: 12px;
  transition: all 0.15s;
}

a:hover {
  background-color: rgb(56, 56, 56);
}
</style>
