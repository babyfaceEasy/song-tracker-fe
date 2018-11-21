<template>
    <v-layout>
        <v-flex xs6>
            <div class="white elevation-2">
                <v-toolbar flat dense class="cyan" dark>
                    <v-toolbar-title class="white--text">Song Metadata</v-toolbar-title>
                </v-toolbar>

                
                <div class="pl-4 pr-4 pt-2 pb-2">
                    <v-layout row>
                        <v-flex xs6>
                            <div class="song-title">{{song.title}}</div>
                            <div class="song-artist">{{song.artist}}</div>
                            <div class="song-genre">{{song.genre}}</div>
                        </v-flex>
                        <v-flex xs6>
                            <img class="album-image" :src="song.albumImage" /> <br>
                            {{song.album}}
                        </v-flex>
                </v-layout>
                </div>
            </div>
        </v-flex>
        <v-flex xs6 class="ml-2">
            <div class="white elevation-2">
                <v-toolbar flat dense class="cyan" dark>
                    <v-toolbar-title class="white--text">Tab</v-toolbar-title>
                </v-toolbar>

                
                <div class="pl-4 pr-4 pt-2 pb-2">
                    <textarea v-model="song.tab" readonly></textarea>
                </div>
            </div>
        </v-flex>
    </v-layout>
</template>
<script>
import SongsService from '@/services/SongsService'
//import Panel from '@/components/Panel'
export default {
    data () {
        return {
            song: null
        }
    },
    async mounted() {
        const songId = this.$store.state.route.params.songId
        this.song = (await SongsService.show(songId)).data

    },
    components : {
        //Panel,
    }
    
}
</script>

<style scoped>
.song{
    padding: 20px;
}
.song-title{
    font-size: 30px;
}
.song-artist{
    font-size: 24px;
}
.song-genre{
    font-size: 18px;
}
.album-image{
    width:70%;
    margin: 0 auto;
}
textarea{
    width: 88%;
    font-family: monospace;
    border: none;
    height: 600px;
    border-style: none;
    border-color: transparent;
    overflow: auto;
    padding: 20px;
}
</style>
