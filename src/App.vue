<template>
  <div id="app">
    <crontab/>
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld";
import crontab from "./components/crontab";
export default {
  name: "App",
  components: {
    HelloWorld,
    crontab
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
