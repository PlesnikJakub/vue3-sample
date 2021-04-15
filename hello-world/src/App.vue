<template>
  <img alt="Vue logo" src="./assets/logo.png" />
  <TopPanel />
  <GifSearch />
</template>

<script>
import GifSearch from "./components/GifSearch.vue";
import TopPanel from "./components/TopPanel.vue";

export default {
  name: "App",
  components: {
    GifSearch,
    TopPanel
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
