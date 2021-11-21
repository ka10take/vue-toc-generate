<script setup lang="ts">
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://v3.vuejs.org/api/sfc-script-setup.html#sfc-script-setup
import Title from "./components/Title.vue";
import Toc from "./components/Toc.vue";
</script>

<template>
  <div class="container">
    <Toc class="toc" />
    <Title />
  </div>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  /* -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px; */
}

.container {
  display: flex;
  margin: 0 auto;
  max-width: 860px;
  position: relative;
}

.toc {
  position: fixed;
  transform: translate(-100%, 20%);
  padding-right: 3rem;
}
</style>
