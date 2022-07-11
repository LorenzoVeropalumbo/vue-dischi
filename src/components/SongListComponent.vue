<template>
  <section>
    <SearchBarComponent 
    @selectGenere="searchGenere" 
    @selectCantante="searchAuthor"  
    :Albumobj="filterSongList"/>

    <div class="container">
      <div v-if="isLoad" class="row row-cols-5">
        <div  class="col gy-3" v-for="song,index in filterSongList" :key="index">
          <SingleSong :singleSong="song" />
        </div>  
      </div>
      <LoadingComponent v-else />
    </div>
  </section>
</template>

<script>
  import LoadingComponent from "./LoadingComponent.vue";
  import SingleSong from "./SingleSong.vue";
  import SearchBarComponent from "./SearchBarComponent.vue";
  import axios from "axios";
  export default {
    name: "SongListComponent",
    components:{
      SingleSong,
      LoadingComponent,
      SearchBarComponent,
    },
    data(){
      return{
        apiUrl: "https://flynn.boolean.careers/exercises/api/array/music",
        songArr: [],
        isLoad: false,
        valueGenre: "",
        valueAuthor: "",
      }
    },
    computed:{
      filterSongList(){
        if (this.valueGenre === "All" && this.valueAuthor === "All") {
          return this.songArr;
        } else if (this.valueGenre !== "All" && this.valueAuthor === "All"){ 
          return this.songArr.filter(word => {
            return word.genre.includes(this.valueGenre)         
          });
        } else if (this.valueGenre === "All" && this.valueAuthor !== "All"){ 
          return this.songArr.filter(word => {
            return word.author.includes(this.valueAuthor)         
          });
        } else {
          return this.songArr.filter(word => {
            return word.author.includes(this.valueAuthor) && word.genre.includes(this.valueGenre)       
          });
        }      
      },
    },
    mounted(){
      this.GetApiSongList();
    },
    methods:{
      GetApiSongList(){
        axios.get(this.apiUrl).then(response => {
          console.log(response.data.response)
          this.songArr = response.data.response;
        })
        .catch((err) =>{
          // has failed
          alert(err)    
        })

        this.isLoad = true;
      },
      searchGenere(world){
        console.log(world)
        this.valueGenre = world;
      },
      searchAuthor(worlds){
        this.valueAuthor = worlds;
        console.log(worlds)
      }
    }
  }
</script>

<style lang="scss" scoped>
  section{
    width: 60%;
    margin: 0px auto;
    padding: 60px 0;
  }
</style>