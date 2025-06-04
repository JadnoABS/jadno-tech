<script setup lang="ts">
import { height } from '@fortawesome/free-brands-svg-icons/fa42Group';
import CRTScreen from './CRTScreen.vue';
import Headline from './Headline.vue';
import { Carousel, Slide, Navigation, Pagination } from 'vue3-carousel';

import 'vue3-carousel/carousel.css'
const carouselConfig = {
  itemsToShow: 1,
  mouseWheel: true
}

</script>

<template>
  <CRTScreen class="carousel-container" id="top">
    <Carousel class="carousel-item" v-bind="carouselConfig">
      <template #slides>
      <Slide>
        <Headline/>
      </Slide>
      <Slide>
        <Headline/>
      </Slide>
      <Slide>
        <Headline/>
      </Slide>
      </template>

      <template #addons>
        <Navigation/>
        <Pagination/>
      </template>
    </Carousel>
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

.carousel-container {
  max-width: 1200px;
  margin: 0 auto;
}

.carousel-item {
  width: inherit; 
  height: inherit;
}

#bottom ul {
  display: flex;
  flex-direction: column;
  text-align: center;
  width: 100%;
  height: 100%;
  margin: 0;
  padding: 0;
}

#bottom li {
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

#bottom li:hover {
  background-color: blueviolet;
}

#bottom li:hover .icon {
  visibility: visible;
}
</style>