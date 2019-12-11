<template>
  <div id="app">
    <player-widget :url="endpoint" />
  </div>
</template>

<script>
import PlayerWidget from "@/components/PlayerWidget";

export default {
  name: "app",
  components: {
    PlayerWidget
  },
  data() {
    return {
      endpoint: "http://18.185.121.3:5000/"
    };
  }
};
</script>

<style lang="scss">
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
