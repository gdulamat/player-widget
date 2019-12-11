<template>
  <div class="player">
    <div class="cover-box"></div>
    <div class="controls">
      <div class="controls__panel">
        <control-btn :icon="shareIcon" />
        <div class="controls__wrapp">
          <control-btn :icon="prevIcon" :color="'#60558f'" />
          <control-btn
            @click.native="handlePlayPause"
            :icon="isPlaying ? playIcon : pauseIcon"
            :size="'l'"
            :color="'#60558f'"
          />
          <control-btn :icon="nextIcon" :color="'#60558f'" />
        </div>
        <control-btn :icon="favoriteIcon" />
      </div>
    </div>
  </div>
</template>

<script>
import ControlBtn from "@/components/PlayerWidget/ControlBtn.vue";
import loopIcon from "@/assets/img/loop-icon.svg";
import shuffleIcon from "@/assets/img/shuffle-icon.svg";
import playAgainIcon from "@/assets/img/playagain-icon.svg";
import shareIcon from "@/assets/img/share-icon.svg";
import prevIcon from "@/assets/img/prev-icon.svg";
import nextIcon from "@/assets/img/next-icon.svg";
import pauseIcon from "@/assets/img/pause-icon.svg";
import playIcon from "@/assets/img/play-icon.svg";
import favoriteIcon from "@/assets/img/favorite-icon.svg";

export default {
  name: "PlayerView",
  components: {
    ControlBtn
  },
  data() {
    return {
      tracks: [],
      isPlaying: false,
      loopIcon,
      shuffleIcon,
      playAgainIcon,
      shareIcon,
      prevIcon,
      nextIcon,
      pauseIcon,
      playIcon,
      favoriteIcon
    };
  },
  methods: {
    handlePlayPause() {
      this.isPlaying = !this.isPlaying;
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.cover-box {
  height: 340px;
  background: violet;
}
.controls {
  height: 140px;
  background-color: #eeeff5;
  &__panel {
    margin: 45px 0 0 0;
    padding: 0 20px;
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
  &__wrapp {
    width: 160px;
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
}
</style>
