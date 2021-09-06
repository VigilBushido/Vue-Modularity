<template>
  <div id="app">
    <Greeting greeting="Hey" who="JavaScript"/>
  </div>
</template>

<script>
import Greeting from "./components/Greeting";

export default {
  name: "App",
  components: {
    Greeting,
  },
};
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
