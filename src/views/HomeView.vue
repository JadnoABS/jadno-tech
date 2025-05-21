<script setup lang="ts">
</script>

<template>
  <div class="container">
    <div v-html="markdownToHtml"></div>
  </div>
</template>

<script lang="ts">
import { marked } from "marked";

export default {
  name: "App",
  data() {
    return {
      markdown: "# Portfolio"
    }
  },
  computed: {
    markdownToHtml() {
      return marked(this.markdown);
    }
  },
  methods: {
    async loadTextFile() {
      try {
        const response = await fetch('/public/markdown/Portfolio.md');
        if (!response.ok) throw new Error('Falha ao carregar arquivo');
        const text = await response.text();
        return text;
      } catch (error) {
        console.error('Erro:', error);
        return '';
      }
    }
  },
  async mounted() {
    this.markdown = await this.loadTextFile();
  }
}
</script>

<style scoped>
.container {
  padding: 10%;
  display: flex;
  flex-direction: column;
  overflow-y: auto;
  border-radius: 1em;
}
</style>