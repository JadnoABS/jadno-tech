<script setup lang="ts">
</script>

<template>
  <CRTScreen>
    <div class="text" v-html="markdownToHtml"></div>
  </CRTScreen>
</template>

<script lang="ts">
import CRTScreen from "@/components/CRTScreen.vue";
import { marked } from "marked";

export default {
  name: "App",
  components: {
    CRTScreen,
  },
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
  padding: 2%;
  display: flex;
  flex-direction: column;
  border-radius: 1em;
}

.text {
  padding: 5%;
  overflow-y: auto;
  scrollbar-width: thin;
  scrollbar-color: #02012b transparent;
}
</style>