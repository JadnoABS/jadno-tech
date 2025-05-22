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
       name="Jadno Barbosa"
       :roles="['Software Engineer', 'Information Systems Bachelor', 'Musician']"
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
	padding: 2em;
}

header {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  max-width: 40%;
}
</style>