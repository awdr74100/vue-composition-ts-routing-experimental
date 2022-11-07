<template>
  <h1>fullPath: {{ $route.fullPath }}</h1>
  <p v-if="isFetching">Loading...</p>
  <p v-else-if="error">{{ error }}</p>
  <ul v-else-if="users">
    <li
      v-for="(user, index) in users.slice(0, 4)"
      :key="index"
      @click.prevent="
        $router.push({ name: '/users/[id]', params: { id: user.id } })
      "
    >
      <p>id: {{ user.id }}</p>
      <p>name: {{ user.name }}</p>
      <p>email: {{ user.email }}</p>
      <p>phone: {{ user.phone }}</p>
    </li>
  </ul>
</template>

<script setup lang="ts">
import { useFetch } from '@vueuse/core';
import type { User } from '@/types';

const url = `${import.meta.env.VITE_BACKEND_URL}/users`;
const { isFetching, error, data: users } = useFetch(url).get().json<User[]>();
</script>

<style scoped>
li {
  cursor: pointer;
  padding: 6px 0px;
  transition: all 0.15s;
}

li:hover {
  background-color: rgb(245, 245, 245);
}

h1 + p {
  margin-top: 6px;
}
/* div p */

/* li{
  margin: 6px 0px;
} */

/* div {
  margin: 6px 0px;
}

div > p {
  padding-top: 6px;

}

li {
  padding: 6px 0px;
  background-color: rgb(202, 202, 202);
} */
</style>
