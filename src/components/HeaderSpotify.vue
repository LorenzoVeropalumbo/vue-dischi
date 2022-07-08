<template>
  <header>
    <div class="img-container">
      <img src="./../assets/logo-small.svg" alt="">
    </div>
  </header>
</template>

<script>
  export default {
    name: 'HeaderSpotify',
  }
</script>

<style lang="scss" scoped>
  @import "@/style/variables.scss";
  
  header{
    background-color: $bg-color-secondary;
    
    .img-container{
      height: 60px;    
      display: flex;
      align-items: center;
      padding: 0 17px;
      
      img{
        width: 40px;
        height: 40px;
        color: red;      
      }
    }
  }
</style>