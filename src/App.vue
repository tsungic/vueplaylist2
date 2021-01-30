<template>
  <div id="app">
    <h2>Welcome</h2>
    <div id="list-container">
      <song-list
        :songs="songlistSongs" 
        @songClicked="songlistSongClicked"></song-list>

      <play-list 
        :songs="playlistSongs"
        @songClicked="playlistSongClicked"></play-list>
      
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
    console.log(artist)
    for(let i=0; i<this.songlistSongs.length; i++) {
      if(this.songlistSongs[i].artist == artist) {
        this.playlistSongs.push(this.songlistSongs[i])
        this.songlistSongs.splice(i,1);
      }
    }
    },
  playlistSongClicked(artist) {
    console.log(artist)
    for(let i=0; i<this.playlistSongs.length;i++) {
      if(this.playlistSongs[i].artist == artist) {
        this.songlistSongs.push(this.playlistSongs[i])
        this.playlistSongs.splice(i,1);
      }
    }
  },
  },
  data() {
    return {
      songlistSongs: [
        {
          artist: 'Beyonce',
          song: 'Dangerously in Love',
        },
        {
          artist: 'U2',
          song: 'One',
        },
        {
          artist: 'Corinne Bailey Rae',
          song: 'Put Your Records On ',
        },
        {
          artist: 'Natalie Cole',
          song: 'This Will Be',
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
