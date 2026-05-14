<script setup lang="ts">
</script>

<template>
  <div class="container crt-screen">
    <slot></slot>
    <div class="scanlines crt"></div>
    <div class="glow"></div>
  </div>
</template>

<script lang="ts">
export default {
  name: "CRTScreen",
}
</script>

<style scoped>
.container {
  padding: 10%;
  display: flex;
  flex-direction: column;
  overflow-y: auto;
  /* border-radius: 1em; */
}

@media (max-width: 1125px) {
  .container {
    padding: 5%;
  }
}

@media (max-width: 714px) {
  .container {
    padding: 3%;
  }
}

.crt-screen {
  position: relative;
  width: 100%;  /* Ajuste conforme necessário */
  height: 100%; /* Ajuste conforme necessário */
  /* background-color: #570000; */
  color: antiquewhite; /* Cor do texto estilo terminal */
  padding: 20px;
  overflow: hidden;
  box-shadow: 0 0 10px rgba(255, 0, 0, 0.5);
    background-image: 
    linear-gradient(rgba(255, 0, 0, 0.1) 1px, transparent 1px),
    linear-gradient(90deg, rgba(255, 0, 0, 0.1) 1px, transparent 1px);
  background-size: 10px 10px;
}

/* Efeito de brilho/glow */
.glow {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: radial-gradient(
    circle at center,
    rgba(0, 255, 0, 0.05) 0%,
    rgba(0, 0, 0, 0) 70%
  );
  pointer-events: none;
  z-index: 5;
  animation: flicker 0.15s infinite alternate;
}
</style>