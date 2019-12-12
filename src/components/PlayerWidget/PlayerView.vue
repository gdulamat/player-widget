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
      <div class="controls__progress-bar">
        <div class="controls__progress-bar-fill">
          <div class="controls__progress-bar-icon">
            <img :src="audioIcon" />
          </div>
        </div>
      </div>
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
            :size="'50px'"
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
import audioIcon from "@/assets/img/audio-icon.svg";

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
      burgerIcon,
      audioIcon
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
.player {
  position: relative;
  z-index: 100;
}
.cover-box {
  height: 340px;
  background: #eeeff5;
  position: relative;
  background-position: center;
  background-size: cover;
  &::before {
    content: "";
    width: 100%;
    height: 100%;
    background-color: #544282;
    position: absolute;
    top: 0;
    left: 0;
    opacity: 0.26;
    z-index: 110;
    pointer-events: none;
  }

  &:hover .cover-box__top,
  &:hover .cover-box__bot {
    opacity: 1;
  }
  &__top {
    width: 100%;
    height: 65px;
    background-color: rgba(#2a224d, 0.6);
    display: flex;
    justify-content: center;
    align-items: center;
    position: absolute;
    top: 0;
    z-index: 120;
    opacity: 0;
    transition: opacity 0.3s ease-out;
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
    z-index: 120;
    opacity: 0;
    transition: opacity 0.3s ease-out;
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
    margin: 38px 0 0 0;
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
  &__progress-bar {
    height: 7px;
    background-color: #ed5e74;
    cursor: pointer;
    &-fill {
      width: 250px;
      height: 7px;
      background-color: #ffffff;
      position: relative;
      cursor: pointer;
    }
    &-icon {
      width: 22px;
      height: 22px;
      border-radius: 50%;
      background-color: #ffffff;
      display: flex;
      justify-content: center;
      align-items: center;
      position: absolute;
      right: -11px;
      top: 50%;
      transform: translateY(-50%);
      z-index: 120;
      filter: drop-shadow(0px 2px 2px rgba(0, 0, 0, 0.1));
      pointer-events: none;
      cursor: pointer;
    }
  }
}
</style>
