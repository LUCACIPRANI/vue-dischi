<template>
    <div class="main-container d-flex flex-column align-items-center">
        <h1 
          v-if="(userSelection != '')">Genre: {{userSelection}}
        </h1>
        <div 
          v-if="(!loading)"  
          class="container row d-flex justify-content-center mt-3">
            <div 
              v-for="(song, index) in filteredSongList" 
              :key="index" 
              class="card">
                <Discs 
                :singleSong='song'/>
            </div>
        </div>
        <Loader v-else/>
    </div>
</template>

<script>
import axios from 'axios';
import Discs from './Discs.vue';
import Loader from './Loader.vue';
export default {
  name: 'Main',
  props: ['userSelection'],
  components:{
    Discs,
    Loader,
  },
  data(){
    return{
        APIurl: 'https://flynn.boolean.careers/exercises/api/array/music',
        songs: [],
        genresArray: [],
        loading: true,
    }
  },
  created() {
    this.getDisc()
    this.getGenres()
  },
  methods: {
    getDisc(){
      axios
        .get(this.APIurl)
        .then(result =>{
          let arraySongs = result.data.response;
          this.songs = arraySongs;
          console.log(this.songs);
          this.loading = false;
        })
    },
    getGenres(){
      axios
        .get(this.APIurl)
        .then(res =>{
          for(let i = 0; i < this.songs.length; i++){
            let genre = res.data.response[i].genre;
            if(!this.genresArray.includes(genre)){
              this.genresArray.push(genre)
            }
          }
          console.log(this.genresArray);
          this.$emit('createdGenres', this.genresArray)
        })
    },
  },
  computed:{
    filteredSongList(){
      if(this.userSelection == ''){
        return this.songs;
      } else{
        let filteredSongs = this.songs.filter(element =>{
          if(element.genre == this.userSelection){
            return element;
          }
        })
        return filteredSongs;
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
@import '@/styles/general.scss';
.main-container{
  width: 100%;
  height: 70vh;
  background: $primarycolor;
  .card{
      flex-basis: calc((100% / 5) - 30px);
      max-width: 210px;
      margin: 10px;
      cursor: pointer;
      transition: 0.3s;
      background-color: $thirdcolor;
      @include center();
      &:hover{
          filter: brightness(1.2);
          transform: scale(1.1);
      }
  }
}
</style>