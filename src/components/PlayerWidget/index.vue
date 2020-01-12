<template>
  <transition name="fade">
    <div class="widget-wrapp" v-if="tracks.length">
      <player-widget-panel
        :tracks="tracks"
        :activeTrack="activeTrack"
        @prevTrack="
          activeTrackIndex === 0
            ? (activeTrackIndex = tracks.length - 1)
            : activeTrackIndex--
        "
        @nextTrack="
          activeTrackIndex === tracks.length - 1
            ? (activeTrackIndex = 0)
            : activeTrackIndex++
        "
        @togglePlaylist="showPlaylist = !showPlaylist"
        ref="player"
      />
      <player-widget-playlist
        :tracks="tracks"
        :open="showPlaylist"
        @togglePlaylist="showPlaylist = !showPlaylist"
        @chooseTrack="chooseTrack"
        ref="playlist"
      />
    </div>
  </transition>
</template>

<script>
import PlayerWidgetPanel from "@/components/PlayerWidget/PlayerWidgetPanel.vue";
import PlayerWidgetPlaylist from "@/components/PlayerWidget/PlayerWidgetPlaylist.vue";

export default {
  name: "PlayerWidget",
  components: {
    PlayerWidgetPanel,
    PlayerWidgetPlaylist
  },
  props: {
    tracks: Array
  },
  data() {
    return {
      activeTrackIndex: 0,
      showPlaylist: false
    };
  },
  computed: {
    activeTrack() {
      return this.tracks[this.activeTrackIndex];
    }
  },
  methods: {
    chooseTrack(obj) {
      this.activeTrackIndex = obj.index;
      this.showPlaylist = false;
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.widget-wrapp {
  width: 360px;
  height: 480px;
  background-color: #f3f4f8;
  border-radius: 30px;
  position: relative;
  box-shadow: 0px 33px 60px -25px rgba(0, 0, 0, 0.6);
  overflow: hidden;
}
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s, transform 0.5s;
}
.fade-enter,
.fade-leave-to {
  transform: translateY(-10px);
  opacity: 0;
}
</style>
