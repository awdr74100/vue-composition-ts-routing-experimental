<template>
  <h1>fullPath: {{ $route.fullPath }}</h1>
</template>

<!-- <route lang="json5">
{
  meta: {
    requiresAuth: true,
  },
}
</route> -->

<script setup lang="ts">
import { _definePage as definePage } from 'unplugin-vue-router/runtime';

definePage({
  meta: {
    requiresAuth: true,
    role: 'admin',
  },
});
</script>
