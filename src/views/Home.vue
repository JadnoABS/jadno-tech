<script setup lang="ts">
import Board from '../components/Board.vue';
import Resume from '../components/Resume.vue';
</script>

<template>
	<div class="page">
	  <div class="resume">
        <Resume :update-topics="updateTopics" :current-topic="currentTopic"/>
	  </div>

    <header>
      <Board
      :topics="topics"
      :scroll-to="scrollTo"
      />
    </header>
	</div>
</template>

<script lang="ts">
export default {
    name: 'Home',
    data() {
			return {
				topics: [] as Topic[],
				currentTopic: ""
			}   
    },
		methods: {
			updateTopics(topics: Topic[]) {
				this.topics = topics;
			},
			scrollTo(id: string) {
				this.currentTopic = id;
			}
		}
}
</script>

<style scoped>
.page {
	display: flex;
  width: 100%;
  height: 100%;
  flex-direction: row;
}

.resume {
  flex: 1;
  min-height: 0;
}

header {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  max-width: 40%;
  height: 100%;
}

@media (max-width: 1125px) {
  .page {
    display: flex;
    width: 100%;
    flex-direction: column;
    height: auto;
  }
  
  header {
    max-width: 100%;
    order: 1;
    height: auto;
    aspect-ratio: 16/9;
  }
  
  .resume {
    order: 2;
    flex: 1;
    min-height: 60vh;
  }
}

@media (max-width: 714px) {
  header {
    aspect-ratio: 16/9;
    min-height: 50vh;
  }
  
  .resume {
    min-height: 50vh;
  }
}
</style>