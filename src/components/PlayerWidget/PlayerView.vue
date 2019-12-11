<template>
  <div class="player">
    <div
      class="cover-box"
      :style="{ backgroundImage: 'url(' + activeTrack.image + ')' }"
    >
      <div class="cover-box__top">
        <control-btn :icon="loopIcon" :bgColor="'transparent'" />
        <control-btn :icon="shuffleIcon" :bgColor="'transparent'" />
        <control-btn :icon="playAgainIcon" :bgColor="'transparent'" />
        <div class="cover-box__burger">
          <control-btn
            :icon="burgerIcon"
            :bgColor="'transparent'"
            @click.native="$emit('togglePlaylist', '')"
          />
        </div>
      </div>
      <div class="cover-box__bot">
        <div>
          <h5>{{ activeTrack.artist }}</h5>
          <h6>{{ activeTrack.title }}</h6>
        </div>
      </div>
    </div>
    <div class="controls">
      <div class="controls__panel">
        <control-btn :icon="shareIcon" />
        <div class="controls__wrapp">
          <control-btn
            :icon="prevIcon"
            :bgColor="'#60558f'"
            @click.native="$emit('prevTrack', '')"
          />
          <control-btn
            @click.native="handlePlayPause"
            :icon="isPlaying ? playIcon : pauseIcon"
            :size="'l'"
            :bgColor="'#60558f'"
          />
          <control-btn
            :icon="nextIcon"
            :bgColor="'#60558f'"
            @click.native="$emit('nextTrack', '')"
          />
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
import burgerIcon from "@/assets/img/burger-icon.svg";

export default {
  name: "PlayerView",
  components: {
    ControlBtn
  },
  props: {
    activeTrack: Object
  },
  data() {
    return {
      isPlaying: false,
      loopIcon,
      shuffleIcon,
      playAgainIcon,
      shareIcon,
      prevIcon,
      nextIcon,
      pauseIcon,
      playIcon,
      favoriteIcon,
      burgerIcon
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
h5,
h6 {
  font-size: 18px;
  font-weight: 700;
  color: #fff;
  text-align: center;
}
h6 {
  margin: 6px 0 0 0;
  font-size: 14px;
  font-weight: 400;
}
.cover-box {
  height: 340px;
  background: violet;
  position: relative;
  background-position: center;
  background-size: cover;
  &__top {
    width: 100%;
    height: 65px;
    background-color: rgba(#2a224d, 0.6);
    display: flex;
    justify-content: center;
    align-items: center;
    position: absolute;
    top: 0;
  }
  &__icon {
    margin: 0 10px;
  }
  &__bot {
    width: 100%;
    height: 65px;
    background-color: rgba(#2a224d, 0.6);
    display: flex;
    justify-content: center;
    align-items: center;
    position: absolute;
    bottom: 0;
  }
  &__burger {
    position: absolute;
    right: 20px;
    top: 50%;
    transform: translateY(-50%);
  }
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
