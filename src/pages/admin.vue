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
import { definePage } from 'vue-router/auto';

definePage({
  meta: {
    requiresAuth: true,
    role: 'admin',
  },
});
</script>
