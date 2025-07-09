<script setup lang="ts">
import CRTScreen from './CRTScreen.vue';
import External from './External.vue';
import Headline from './Headline.vue';
import { Carousel, Slide, Navigation, Pagination } from 'vue3-carousel';

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
        <External/>
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
        <div class="item"><h2>{{ topic.text }}</h2></div>
      </li>
    </ul>
  </CRTScreen>
</template>

<script lang="ts">
import 'vue3-carousel/dist/carousel.css'

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
  components: {
    Carousel,
    Slide,
    Pagination,
    Navigation
  }
}
</script>

<style>
.container {
  display: flex;
  flex-direction: column;
  justify-content: space-around;
  height: 100%;
}

#bottom {
  /* border-radius: 1em 0 0 0; */
  padding: 0;
}

.carousel-container {
  max-width: 1200px;
  margin: 0 auto;
  height: 100%;
}

.carousel-item {
  padding: 2em;
  width: inherit; 
  height: inherit;
}

.carousel__prev,
.carousel__next {
  color: #FFFFFF;
}

.carousel__prev--disabled,
.carousel__next--disabled {
  display: none;
}

.carousel__prev:hover,
.carousel__next:hover {
  color: #570000;
}

.carousel__pagination-button {
  background-color: #570000;
}

.carousel__pagination-button--active {
  background-color: #FFFFFF;
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
  /* background-color: blueviolet; */
  background-color: #570000;
}

#bottom li:hover .icon {
  visibility: visible;
}

@media (max-width: 1125px) {
  #bottom {
    display: none;
  }
  
  .carousel-container {
    height: 100%;
    width: 100%;
  }
  
  .carousel-item {
    height: 100%;
  }
}
</style>