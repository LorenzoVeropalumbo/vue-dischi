<template>
  <section>
    <div class="container">
      <div v-if="isLoad" class="row row-cols-5">
        <div  class="col gy-3" v-for="song,index in songArr" :key="index">
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
  import axios from "axios";
  export default {
    name: "SongListComponent",
    components:{
      SingleSong,
      LoadingComponent,
    },
    data(){
      return{
        apiUrl: "https://flynn.boolean.careers/exercises/api/array/music",
        songArr: [],
        isLoad: false,
      }
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