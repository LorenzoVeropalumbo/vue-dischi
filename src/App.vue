<template>
  <div id="app">
    <HeaderSpotify />

    <main>
     {{songArr}} 
    </main>
        
  </div>
</template>

<script>
  import axios from "axios";
  import HeaderSpotify from "@/components/HeaderSpotify.vue"

  export default {
    name: 'App',
    components: {
      HeaderSpotify,
    },
    data(){
      return{
        apiUrl: "https://flynn.boolean.careers/exercises/api/array/music",
        songArr: [],
      }
    },
    mounted(){
      this.GetApiSongList();
    },
    methods:{
      GetApiSongList(){
        axios.get(this.apiUrl).then(response => {
          console.log(response)
          this.songArr = response.data.response  
        })
        .catch((err) =>{
          // has failed
          console.log(err)     
        })
      }
    }
  }
</script>

<style lang="scss">
  @import "./style/common";
  @import "@/style/variables.scss";
  main{
    height: calc(100vh - 60px);
    width: 100%;
    background-color: $main-bg-color;
  }

</style>
