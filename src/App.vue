<script setup lang="ts">
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://v3.vuejs.org/api/sfc-script-setup.html#sfc-script-setup
import Title from "./components/Title.vue";
import Toc from "./components/Toc.vue";
</script>

<template>
  <div class="body">
    <div class="header">
      <span>Toc Generator</span>
    </div>

    <div class="container">
      <Toc class="toc" />
      <Title />
    </div>

    <div class="space"></div>
  </div>
</template>

<style>
* {
  margin: 0;
  padding: 0;
  color: #2e2e2e;
}

h2 {
  margin-top: 2rem;
}

h3 {
  margin-top: 1.5rem;
}

h4 {
  margin-top: 1rem;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  /* -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px; */
}

.body {
  padding-top: 60px;
}

.header {
  width: 100%;
  height: 60px;
  background-color: white;
  position: fixed;
  z-index: 1;
  top: 0;
  text-align: center;
  font-size: 1.5rem;
  display: flex;
  align-items: center;
  justify-content: space-around;
  box-shadow: 0px 4px 10px 4px rgb(0 0 0 / 4%);
}

.container {
  display: flex;
  margin: 0 auto;
  max-width: 860px;
  position: relative;
  padding-top: 3rem;
}

.toc {
  position: fixed;
  transform: translate(-100%, 0);
  padding-right: 3rem;
}

.space {
  height: 1000px;
  width: 100%;
}
</style>
