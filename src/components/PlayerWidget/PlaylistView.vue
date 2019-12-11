<template>
  <div class="playlist"></div>
</template>

<script>
export default {
  name: "PlaylistView",
  props: {
    url: String
  },
  data() {
    return {
      tracks: []
    };
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss"></style>
