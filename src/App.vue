<template>
  <div id="app">
    <player-widget msg="Welcome to Your Vue.js App" />
  </div>
</template>

<script>
import PlayerWidget from "@/components/PlayerWidget";

export default {
  name: "app",
  components: {
    PlayerWidget
  }
};
</script>

<style lang="scss">
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
