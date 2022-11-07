<template>
  <h1>
    fullPath: {{ $route.fullPath }}
    <span class="text-danger">(Not found)</span>
  </h1>
</template>

<style scoped>
.text-danger {
  color: red;
}
</style>
