<script setup lang="ts">
import CRTScreen from './CRTScreen.vue';

// defineProps<{
//   name: string,
//   roles: string[]
// }>()
</script>

<template>
  <CRTScreen id="top">
    <header>
      <div class="headline">
        <h1>{{ name }}</h1>
        <h2 v-for="(role, index) in roles" :key="index">
          {{ role }}
        </h2>
      </div>
      <div class="profile-image">
        <img src="../assets/Jadno.jpeg" alt="Foto de Jadno Barbosa">
      </div>
    </header>
  </CRTScreen>

  <CRTScreen id="bottom">
    <ul>
      <li v-for="(topic, index) in topics" :key="topic.id" @mouseover="scrollTo(topic.id)">
        <div class="icon"><font-awesome-icon :icon="['fas', 'angle-right']" /></div>
        <div class="item">{{ topic.text }}</div>
      </li>
    </ul>
  </CRTScreen>
</template>

<script lang="ts">

export default {
  name: "Board",
  props: {
    name: {
      type: String,
      required: true
    },
    roles: {
      type: Array<String>,
      required: true
    },
    topics: {
      type: Array<Topic>,
      required: true
    },
    scrollTo: {
      type: Function,
      required: true
    }
  },
}
</script>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  justify-content: space-around;
  height: 100%;
}

#bottom {
  border-radius: 1em 0 0 0;
  padding: 0;
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

.profile-image {
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

ul {
  display: flex;
  flex-direction: column;
  text-align: center;
  width: 100%;
  height: 100%;
  margin: 0;
  padding: 0;
}

li {
  display: flex;
  list-style: none;
  align-items: center;
  justify-content: flex-start;
  width: 100%;
  height: 100%;
}

.icon {
  margin-left: 1em;
  visibility: hidden;
}

.item {
  text-align: center;
  width: 100%;
}

li:hover {
  background-color: blueviolet;
}

li:hover .icon {
  visibility: visible;
}
</style>