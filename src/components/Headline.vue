
<template>
  <header>

    <div class="headline">
      <h1>Jadno Barbosa</h1>
      <h2 v-for="(role, index) in roles" :key="index">
          {{ role }}
      </h2>
    </div>
    <div class="profile-image">
      <img src="../assets/Jadno.jpg" alt="Foto de Jadno Barbosa">
    </div>
  </header>
</template>

<script lang="ts">
export default {
  name: "Headline",
  data() {
    return {
      roles: ['Engenheiro de Software', 'Bel. em Sistemas de Informação', 'Músico']
    }
  }
}
</script>

<style scoped>

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

.profile-image {
  height: 100%;
  display: flex;
  align-items: center;
}

.headline {
  text-align: center;
  margin: 2%;
  max-width: 100%;
  white-space: wrap;
}

h1 {
  font-weight: 500;
  font-size: 2.6rem;
  text-align: center;
}

h2 {
  font-size: 1.2rem;
  margin: 0.5rem 0;
}

@media (max-width: 1125px) {
  header {
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: space-between;
    height: 100%;
    width: 100%;
    gap: 1rem;
  }

  .headline {
    flex: 1;
    text-align: center;
    margin: 0;
  }

  .profile-image {
    flex: 1;
    height: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  img {
    max-width: 50%;
    height: auto;
    border-radius: 3%;
    object-fit: contain; 
  }
}

@media (max-width: 714px) {
  h1 {
    font-size: 1.5rem;
  }
  
  h2 {
    font-size: 0.9rem;
  }
}
</style>