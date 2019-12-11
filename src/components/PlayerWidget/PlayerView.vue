<template>
  <div class="player">
    <div class="cover-box"></div>
    <div class="controls-panel">
      <div class="controls-wrapp">
        <control-btn />
      </div>
    </div>
  </div>
</template>

<script>
import ControlBtn from "@/components/PlayerWidget/ControlBtn.vue";

export default {
  name: "PlayerView",
  components: {
    ControlBtn
  },
  data() {
    return {
      tracks: []
    };
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.cover-box {
  height: 340px;
  background: violet;
}
.controls-panel {
  height: 140px;
  background-color: #eeeff5;
}
.controls-wrapp {
  margin: 45px 0 0 0;
  padding: 0 20px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}
</style>
