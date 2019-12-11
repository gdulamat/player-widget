<template>
  <div class="playlist">
    <div class="playlist__top">
      <h5>Playlist</h5>
      <div class="playlist__back-arrow">
        <control-btn
          :icon="backIcon"
          :bgColor="'transparent'"
          @click.native="$emit('togglePlaylist', '')"
        />
      </div>
    </div>
    <ul>
      <li v-for="(track, i) in tracks" :key="i">
        {{ track.title }}
      </li>
    </ul>
  </div>
</template>

<script>
import ControlBtn from "@/components/PlayerWidget/ControlBtn.vue";
import backIcon from "@/assets/img/back-arrow-icon.svg";

export default {
  name: "PlaylistView",
  components: {
    ControlBtn
  },
  props: {
    tracks: Array
  },
  data() {
    return {
      backIcon
    };
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
h5 {
  font-size: 18px;
  color: #60558f;
  font-family: "Rambla";
  font-weight: 700;
  text-align: center;
}
.playlist {
  height: 480px;
  background-color: #f3f4f8;
  &__top {
    height: 65px;
    display: flex;
    justify-content: center;
    align-items: center;
    position: relative;
  }
  &__back-arrow {
    position: absolute;
    left: 20px;
    top: 50%;
    transform: translateY(-50%);
  }
}
</style>
