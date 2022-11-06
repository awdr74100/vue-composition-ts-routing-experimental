<template>
  <header>
    <AppNavbar />
  </header>
  <main>
    <RouterView />
  </main>
</template>

<script setup lang="ts">
import { RouterView } from 'vue-router/auto';
import AppNavbar from '@/components/AppNavbar.vue';
</script>

<style scoped>
header {
  border: 1px solid black;
  padding: 12px;
  margin-top: 12px;
}

main {
  border: 1px solid black;
  padding: 12px;
  margin-top: 12px;
  margin-bottom: 12px;
}
</style>
