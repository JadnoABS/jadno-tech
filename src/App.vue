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
  height: 100vh;
  width: 100%;
  padding: 0;
  justify-content: space-between;
}

@media (max-width: 1125px) {
  main {
    flex-direction: column;
    height: auto;
    min-height: 100vh;
  }
}

@media (max-width: 714px) {
  main {
    min-height: 100vh;
  }
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
