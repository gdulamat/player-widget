<template>
  <div class="widget-wrapp" v-if="tracks.length">
    <player-view
      v-if="showPlayer"
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
      @togglePlaylist="showPlayer = !showPlayer"
    />
    <playlist-view
      v-else
      :tracks="tracks"
      @togglePlaylist="showPlayer = !showPlayer"
    />
  </div>
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
      showPlayer: true
    };
  },
  computed: {
    activeTrack() {
      return this.tracks[this.activeTrackIndex];
    }
  },
  created() {
    fetch("https://cors-anywhere.herokuapp.com/" + this.url, {
      mode: "cors"
    })
      .then(res => res.json())
      .then(res => (this.tracks = res));
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
a {
  color: #42b983;
}

.widget-wrapp {
  width: 360px;
  height: 480px;
  background-color: #f3f4f8;
  border-radius: 30px;
  box-shadow: 0px 33px 60px -25px rgba(0, 0, 0, 0.6);
  overflow: hidden;
}
</style>
