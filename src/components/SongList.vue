<template>
  <div>
    <h3>Songlist</h3>
    <div id="song-container">
      <!-- //we dont have a real key yet =song.artist to uniquely identify -->
      <div
        v-for="song in songs"
        :key="song.artist"
        class="song"
        @click="moveSong(song.artist)"
      >
        <h4>{{ song.artist }}</h4>
        <h5>{{ song.song }}</h5>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    songs: {
      type: Array,
      required: true,
    },
  },

  methods: {
    moveSong(artist) {
      this.$emit("songClicked", artist);
    },
  },
};
</script>

<style scoped>
#song-container {
  width: 40vw;
  margin-left: 5vw;
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
}

.song {
  box-shadow: 3px 3px 3px grey;
  min-width: 100px;
  min-height: 100px;
}
</style>