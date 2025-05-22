<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
import Home from './views/Home.vue';
</script>

<template>
  <main>
    <Home />
  </main>
</template>

<style scoped>
main {
  display: flex;
  height: 100%;
  width: 100%;
  padding: 0;
  justify-content: space-between;
}

::-webkit-scrollbar {
  width: 8px;
}

::-webkit-scrollbar-track {
  background: #f1f1f1;
}

::-webkit-scrollbar-thumb {
  background: #888;
  border-radius: 4px;
}

::-webkit-scrollbar-thumb:hover {
  background: #555;
}
</style>
