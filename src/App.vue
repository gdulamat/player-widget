<template>
  <div id="app">
    <player-widget :tracks="tracks" />
  </div>
</template>

<script>
import PlayerWidget from "@/components/PlayerWidget";

export default {
  name: "app",
  components: {
    PlayerWidget
  },
  data() {
    return {
      tracks: [
        {
          artist: "Tame Impala",
          image:
            "https://upload.wikimedia.org/wikipedia/en/9/9b/Tame_Impala_-_Currents.png",
          time: "5:54",
          title: "The Less I Know the Better"
        },
        {
          artist: "Tame Impala",
          image:
            "https://upload.wikimedia.org/wikipedia/commons/thumb/7/76/Tame_Impala-3760_%2818222291464%29.jpg/320px-Tame_Impala-3760_%2818222291464%29.jpg",
          time: "4:46",
          title: "Eventually"
        },
        {
          artist: "Tame Impala",
          image:
            "https://upload.wikimedia.org/wikipedia/en/9/9b/Tame_Impala_-_Currents.png",
          time: "6:03",
          title: "New Person, Same Old Mistakes"
        },
        {
          artist: "Tame Impala",
          image:
            "https://upload.wikimedia.org/wikipedia/commons/thumb/7/76/Tame_Impala-3760_%2818222291464%29.jpg/320px-Tame_Impala-3760_%2818222291464%29.jpg",
          time: "4:20",
          title: "The Moment"
        },
        {
          artist: "Still Corners",
          image:
            "https://upload.wikimedia.org/wikipedia/en/8/89/Strange_Pleasures_album_cover.jpg",

          time: "6:12",
          title: "The Trip"
        },
        {
          artist: "Still Corners",
          image:
            "https://upload.wikimedia.org/wikipedia/commons/thumb/a/a3/Still_Corners_by_Chona_Kasinger.JPG/320px-Still_Corners_by_Chona_Kasinger.JPG",
          time: "4:51",
          title: "The Message"
        }
      ]
    };
  }
};
</script>

<style lang="scss">
@import url("https://fonts.googleapis.com/css?family=Rambla:400,700&display=swap");

#app {
  font-size: 16px;
  color: #2f1a4b;
  font-family: "Rambla", sans-serif;
  margin-top: 60px;
}
</style>
