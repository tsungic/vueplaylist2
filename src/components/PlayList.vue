<template>
    <div>
        <h3>Playlist</h3>
        <div id="playlist-container">
            <div v-for="song in songs" 
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
#playlist.container{
    width: 40vw;
    margin-left: 5vw;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));

}
.song {
  box-shadow: 3px 3px 3px grey;
  min-width: 100px;
  min-height: 100px;
}


</style>