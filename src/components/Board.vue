<script setup lang="ts">
defineProps<{
  name: string,
  role: string
}>()
</script>

<template>
  <div class="container">
    <header>
      <div class="headline">
        <h1>{{ name }}</h1>
        <h2>{{ role }}</h2>
      </div>
      <img src="../assets/Jadno.jpeg" alt="Foto de Jadno Barbosa">
    </header>

    <section>
      <li>Sobre</li>
      <li>Sobre</li>
      <li>Sobre</li>
      <li>Sobre</li>
      <li>Sobre</li>
      <li>Sobre</li>
      <li>Sobre</li>
      <li>Sobre</li>
      <li>Sobre</li>
      <li>Sobre</li>
    </section>
  </div>
</template>

<style scoped>
.container {
  border-radius: 3% 0 0 0;
  display: flex;
  flex-direction: column;
}

header {
  display: flex;
  max-height: 50%;
  max-width: 100%;
}

img {
    max-height: 100%;
    margin: 2%;
    border-radius: 3%;
}

.headline {
  text-align: center;
  margin: 2%;
  max-width: 100%;
  white-space: nowrap;
}

h1 {
  font-weight: 500;
  font-size: 2.6rem;
  text-align: center;
}
</style>