<script setup lang="ts">
import Board from '../components/Board.vue';
import Resume from '../components/Resume.vue';
</script>

<template>
	<div class="page">
    <header>
      <Board
      :topics="topics"
      :scroll-to="scrollTo"
      />
    </header>

	  <div class="resume">
        <Resume :update-topics="updateTopics" :current-topic="currentTopic"/>
	  </div>
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
  }
  
  .resume {
    order: 2;
    flex: 1;
    min-height: 0;
  }
}

@media (max-width: 714px) {
  header {
    height: auto;
  }
  
  .resume {
    min-height: 0;
  }
}
</style>