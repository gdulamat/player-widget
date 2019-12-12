<template>
  <transition name="fade">
    <div class="widget-wrapp" v-if="tracks.length">
      <player-view
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
      <playlist-view
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
import PlayerView from "@/components/PlayerWidget/PlayerView.vue";
import PlaylistView from "@/components/PlayerWidget/PlaylistView.vue";

export default {
  name: "PlayerWidget",
  components: {
    PlayerView,
    PlaylistView
  },
  props: {
    url: String
  },
  data() {
    return {
      tracks: [],
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
  },
  created() {
    fetch("https://cors-anywhere.herokuapp.com/" + this.url, {
      mode: "cors"
    })
      .then(res => res.json())
      .then(res => {
        this.tracks = [...this.tracks, ...res];
        this.tracks = [...this.tracks, ...res];
        this.tracks = [...this.tracks, ...res];
      });
    //.then(res => this.tracks = res);
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
