<template>
  <button
    class="btn"
    :class="[size === 'l' ? 'l-size' : '']"
    :style="{ backgroundColor: color }"
  >
    <img :src="icon" />
  </button>
</template>

<script>
export default {
  name: "ControlBtn",
  props: {
    icon: String,
    size: String,
    color: {
      type: String,
      default: "#ffffff"
    }
  },
  methods: {
    comoon: function() {
      console.log("click");
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.btn {
  width: 36px;
  height: 36px;
  border-radius: 50%;
  display: flex;
  justify-content: center;
  align-items: center;
  filter: drop-shadow(0px 2px 2px rgba(0, 0, 0, 0.1));
  cursor: pointer;
  transition: transform 0.3s ease-out;
  &:hover {
    transform: scale(1.1);
  }
  &.l-size {
    width: 50px;
    height: 50px;
  }
}
</style>
