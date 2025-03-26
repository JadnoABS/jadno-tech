<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
import Board from './components/Board.vue';
</script>

<template>
  <main>
    <div class="page">
      <RouterView/>
    </div>

    <header>
      <Board name="Jadno Barbosa" role="Software Developer"/>
    </header>
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

.page {
  margin: 2%;
  margin-bottom: 0;
}

header {
  line-height: 1.5;
  padding-top: 2%;
  overflow-y: auto;
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
