<template>
  <div class="btn">
    <img :src="icon" />
  </div>
</template>

<script>
export default {
  name: "ControlBtn",
  props: {
    icon: String,
    size: String
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss"></style>
