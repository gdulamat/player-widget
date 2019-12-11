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
@import url("https://fonts.googleapis.com/css?family=Rambla:400,700&display=swap");

#app {
  font-size: 16px;
  color: #2f1a4b;
  font-family: "Rambla", sans-serif;
  margin-top: 60px;
}
</style>
