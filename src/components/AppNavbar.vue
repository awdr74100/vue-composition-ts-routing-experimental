<template>
  <ul>
    <li>
      <RouterLink to="/" v-slot="{ href }">{{ href }}</RouterLink>
    </li>
    <li>
      <RouterLink :to="'/news'" v-slot="{ href }">{{ href }}</RouterLink>
    </li>
    <li>
      <RouterLink :to="{ path: '/about' }" v-slot="{ href }">{{
        href
      }}</RouterLink>
    </li>
    <li>
      <RouterLink :to="{ name: '/users/' }" v-slot="{ href }">{{
        href
      }}</RouterLink>
    </li>
    <li v-for="num in 2" :key="num">
      <RouterLink
        :to="{ name: '/users/[id]', params: { id: num } }"
        v-slot="{ href }"
        >{{ href }}</RouterLink
      >
    </li>
    <li>
      <RouterLink :to="{ path: '/users/3' }" v-slot="{ route }"
        >/users/{{
          (route as RouteLocationResolved<'/users/[id]'>).params.id
        }}</RouterLink
      >
    </li>
    <li>
      <RouterLink :to="{ path: '/users/4/profile' }" v-slot="{ href }">{{
        href
      }}</RouterLink>
    </li>
    <li>
      <RouterLink
        :to="{ name: '/admin', query: { id: '4K6H' } }"
        v-slot="{ href }"
        >{{ href }}</RouterLink
      >
    </li>
  </ul>
</template>

<script setup lang="ts">
import { type RouteLocationResolved, useLink } from 'vue-router/auto';

const { isActive } = useLink({
  to: '/users/3',
});
const { isExactActive } = useLink({
  to: { path: '/users' },
});
const { navigate } = useLink({
  to: { name: '/users/[id]', params: { id: 6 } },
});

// import { type RouteLocationNormalizedLoaded, useLink } from 'vue-router/auto';

// const { isActive } = useLink({
//   to: { name: '/users/[id]', params: { id: 1 } },
// });

// const { isExactActive } = useLink({
//   to: { path: '/users/2' },
// }).route.value.params.;

// const { href, route } = useLink({
//   to: '/admin',
// });

// const paths = [
//   '/',
//   '/news',
//   '/about',
//   '/users',
//   '/users/1',
//   '/users/2',
//   '/users/3/profile',
//   '/admin',
// ];
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
