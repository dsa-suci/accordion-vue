<template>
  <img alt="Vue logo" src="./assets/logo.png" />
  <p>Select Device</p>
  <AccordionView />
</template>

<script>
import AccordionView from "./components/AccordionView.vue";

export default {
  name: "App",
  components: {
    AccordionView,
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
