<script setup lang="ts">
import CRTScreen from './CRTScreen.vue';

defineProps<{
  name: string,
  roles: string[]
}>()
</script>

<template>
  <CRTScreen>
    <header>
      <div class="headline">
        <h1>{{ name }}</h1>
        <h2 v-for="(role, index) in roles" :key="index">
          {{ role }}
        </h2>
      </div>
      <div class="icon">
        <img src="../assets/Jadno.jpeg" alt="Foto de Jadno Barbosa">
      </div>
    </header>
  </CRTScreen>

  <CRTScreen>
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
  </CRTScreen>
</template>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  justify-content: space-around;
  height: 100%;
}

#top {
  border-radius: 1em 0 0 1em;
  
}

#bottom {
  border-radius: 1em 0 0 0;
}

header {
  display: flex;
  align-items: center;
  justify-content: space-around;
  height: 100%;
  width: 100%;
}

img {
    max-height: 80%;
    border-radius: 3%;
}

.icon {
  height: 100%;
  display: flex;
  align-items: center;
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

section {
  width: 100%;
  text-align: center;
  margin: 0;
}

li {
  list-style: none;
  width: 100%;
}

li:hover {
  background-color: blueviolet;
}
</style>