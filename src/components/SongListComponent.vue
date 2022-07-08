<template>
  <section>
    <div class="container">
      <div class="row row-cols-5">
        <div class="col">
          <div class="card-content gx-5">
            <img :src="songArr[0].author" alt="">
            {{songArr[0].author}}
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
  import axios from "axios";
  export default {
    name: "SongListComponent",
    props:{
    },
    data(){
      return{
        apiUrl: "https://flynn.boolean.careers/exercises/api/array/music",
        songArr: [],
      }
    },
    created(){
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
          console.log(err);    
        })
      }
    }
  }
</script>

<style lang="scss" scoped>
  @import "@/style/variables.scss";

  section{
    width: 80%;
    margin: 0px auto;
    padding: 60px 0;

    .card-content{
      background-color: $bg-color-secondary;
    }
  }
</style>