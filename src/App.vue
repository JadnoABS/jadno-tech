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
      <Board
       name="Jadno Barbosa"
       :roles="['Software Engineer', 'Information Systems Bachelor', 'Musician']"
      />
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
  margin: 0 5vh;
}

header {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  max-width: 40%;
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
