<template>
  <button
    class="btn"
    :style="{ backgroundColor: bgColor, width: size, height: size }"
  >
    <img :src="icon" />
  </button>
</template>

<script>
export default {
  name: "ControlBtn",
  props: {
    icon: String,
    size: {
      type: String,
      default: "36px"
    },
    bgColor: {
      type: String,
      default: "#ffffff"
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.btn {
  border: none;
  border-radius: 50%;
  display: flex;
  justify-content: center;
  align-items: center;
  filter: drop-shadow(0px 2px 2px rgba(0, 0, 0, 0.1));
  cursor: pointer;
  transition: box-shadow 0.3s ease-out;
  &:hover,
  &:focus {
    box-shadow: 0px 4px 5px 4px rgba(0, 0, 0, 0.3);
  }
  & img {
    min-width: 15px;
    min-height: 15px;
  }
}
</style>
