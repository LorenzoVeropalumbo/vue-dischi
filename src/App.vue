<template>
  <div id="app">
    <HeaderSpotify />

    <main>
     <SongListComponent/> 
    </main>
        
  </div>
</template>

<script>
  import HeaderSpotify from "@/components/HeaderSpotify.vue"
  import SongListComponent from "@/components/SongListComponent.vue"

  export default {
    name: 'App',
    components: {
      HeaderSpotify,
      SongListComponent,
    },
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
