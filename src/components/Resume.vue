<template>
  <CRTScreen>
    <div class="text" ref="text" v-html="markdownToHtml"></div>
  </CRTScreen>
</template>

<script lang="ts">
import CRTScreen from "@/components/CRTScreen.vue";
import { marked } from "marked";
import type { RendererObject } from "marked";

const renderer: RendererObject = {
  heading({tokens , depth}): string {
    const text = this.parser.parseInline(tokens);
    const id = text
      .toLowerCase()
      .normalize("NFD")
      .replace(/[\u0300-\u036f]/g, "")
      .replace(/[^\w-]+/g, '-')
      .replace(/^-+|-+$/g, '');

    // if(depth >= 3) return `<p style="font-weight: bold; font-size: ${3 - (depth/4)}vw">${text}</p>`;

    return `
      <h${depth} style="text-align: center; font-weight: bold; font-size: max(${2.5 - (depth/4)}vw, ${Math.max(18 - depth * 2, 14)}px); word-wrap: break-word; overflow-wrap: break-word; hyphens: auto; white-space: normal; max-width: 100%;" id="${id}">
        ${text}
      </h${depth}>
    `;
  },
  paragraph({tokens}): string {
    const text = this.parser.parseInline(tokens);

    return `
      <p style="font-size: max(1.5vw, 14px); word-wrap: break-word; overflow-wrap: break-word; hyphens: auto; white-space: normal; max-width: 100%;">
        ${text}
      </p>
    `;
  },
  link({href, title, text}): string {
    const isExternal = href.startsWith('http') && !href.includes('meusite.com');
    const target = isExternal ? ' target="_blank" rel="noopener noreferrer"' : '';
    return `<a href="${href}"${target}${title ? ` title="${title}"` : ''}>${text}</a>`;
  }
};

marked.use({ renderer });

export default {
  name: "Resume",
  props: {
    updateTopics: {
      type: Function,
      required: true
    },
    currentTopic: {
      type: String,
      required: true
    }
  },
  components: {
    CRTScreen,
  },
  data() {
    return {
      markdown: "# Portfolio",
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
        const response = await fetch('/markdown/Portfolio.md');
        if (!response.ok) throw new Error('Falha ao carregar arquivo');
        const text = await response.text();
        return text;
      } catch (error) {
        console.error('Erro:', error);
        return '';
      }
    },
    async extractTopics() {
      const parser = new DOMParser();
      const text = await this.markdownToHtml;
      const parsedText = parser.parseFromString(text, 'text/html');
      const result: Topic[] = [];

      const h1Elements = parsedText.querySelectorAll('h1');
      h1Elements.forEach( h => {
        if(h.id) {
          result.push({
            id: h.id,
            text: h.textContent?.trim() || ''
          });
        }
      });

      this.updateTopics(result);
    },
    scrollToTopic(topic: string) {
      const element = document.getElementById(topic);
      element?.scrollIntoView({ behavior: "smooth"});
    }
  },
  async mounted() {
    this.markdown = await this.loadTextFile();
    await this.extractTopics();
  },
  watch: {
    currentTopic(newValue, oldValue) {
      if(newValue === oldValue) return;
      this.scrollToTopic(newValue);
    }
  }
}

</script>
   
<style scoped>
.container {
  padding: 2%;
  display: flex;
  flex-direction: column;
  /* border-radius: 1em; */
}

.text {
  padding: 5%;
  overflow-y: auto;
  scrollbar-width: thin;
  scrollbar-color: #570000 transparent;
  height: 100%;
  word-wrap: break-word;
  overflow-wrap: break-word;
  hyphens: auto;
  white-space: normal;
}

/* Force text wrapping on all elements inside .text */
.text * {
  word-wrap: break-word !important;
  overflow-wrap: break-word !important;
  hyphens: auto !important;
  white-space: normal !important;
  max-width: 100% !important;
  box-sizing: border-box !important;
}

.text p, .text h1, .text h2, .text h3, .text h4, .text h5, .text h6 {
  word-break: break-word !important;
  overflow-wrap: anywhere !important;
  white-space: pre-wrap !important;
}

@media (max-width: 1125px) {
  .text {
    height: auto;
    max-height: 60vh;
  }
  
  .text * {
    word-break: break-word !important;
  }
}

@media (max-width: 714px) {
  .text {
    padding: 3%;
    max-height: 50vh;
    overflow-y: auto;
  }
  
  .text * {
    word-break: break-word !important;
    overflow-wrap: anywhere !important;
  }
}

/* Global styles for mobile text wrapping */
@media (max-width: 714px) {
  .text h1, .text h2, .text h3, .text h4, .text h5, .text h6 {
    word-break: break-word !important;
    overflow-wrap: break-word !important;
    hyphens: auto !important;
  }
  
  .text p {
    word-break: break-word !important;
    overflow-wrap: break-word !important;
    hyphens: auto !important;
    line-height: 1.4 !important;
  }
}
</style>