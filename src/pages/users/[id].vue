<template>
  <h1>fullPath: {{ $route.fullPath }}</h1>
  <!-- <h2>params.id: {{ $route.name === '/users/[id]' && $route.params.id }}</h2> -->
  <!-- <h2>params.id: {{ route.params.id }}</h2> -->
  <p v-if="isFetching">Loading...</p>
  <p v-else-if="error">{{ error }}</p>
  <ul v-else-if="user">
    <li>
      <p>id: {{ user.id }}</p>
      <p>name: {{ user.name }}</p>
      <p>email: {{ user.email }}</p>
      <p>phone: {{ user.phone }}</p>
    </li>
  </ul>
</template>

<script setup lang="ts">
import { ref, watch } from 'vue';
import { useRoute } from 'vue-router/auto';
import { useFetch } from '@vueuse/core';
import type { User } from '@/types';

const route = useRoute('/users/[id]');

const url = ref(`${import.meta.env.VITE_BACKEND_URL}/users/${route.params.id}`);
const {
  isFetching,
  error,
  data: user,
} = useFetch(url, { refetch: true }).get().json<User>();

watch(
  () => route.params.id,
  (newId) => {
    if (newId === undefined) return;
    url.value = `${import.meta.env.VITE_BACKEND_URL}/users/${newId}`;
  },
);
</script>

<style scoped>
li {
  padding: 6px 0px;
}

h1 + p {
  margin-top: 6px;
}
</style>
