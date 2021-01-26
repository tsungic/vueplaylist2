<template>
  <div id="app">
    <h2>Welcome</h2>
    <div id="list-container">
      <song-list
        :songs="songlistSongs" 
        @songCliked="songlistSongClicked"></song-list>
      <play-list :songs="playlistSongs"></play-list>
      
    </div>
  </div>
</template>

<script>
import PlayList from './components/PlayList.vue'
import SongList from './components/SongList.vue'

export default {
  name: 'App',
  components: {
    PlayList,
    SongList,
   
  },
  methods: {
  songlistSongClicked(artist) {
    for(let i=0; i<this.songlistSongs.length; i++) {
      if(this.songlistSongs[i].artist == artist) {
        this.playlistSongs.push(this.songlistSongs[i])
        this.songlistSongs.splice(i,1);
      }
    }
    },

  },
  data() {
    return {
      songlistSongs: [
        {
          artist: 'A',
          song: '1',
        },
        {
          artist: 'B',
          song: '2',
        },
        {
          artist: 'C',
          song: '3',
        },
        {
          artist: 'D',
          song: '4',
        },
      ],
      playlistSongs:[],
    }
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

#list-container {
  display:grid;
  grid-template-columns: 1fr 1fr;
}
</style>
