<template>
  <div id="app">
    <Home />
  </div>
</template>

<script>
import Home from "@/components/Home.vue";
export default {
  name: "App",
  components: {
    Home,
  },
};
</script>

<style>
#app {
  width: 100vw;
  height: 100vh;
  background-color: #53B690;
  display: grid;
  grid-template-columns: repeat(12, 1fr);
  grid-template-rows: repeat(17, 1fr);
}
</style>
