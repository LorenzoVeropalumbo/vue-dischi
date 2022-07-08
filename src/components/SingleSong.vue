<template>
  <div class="card-content gx-5">
    <img :src="singleSong.poster" :alt="singleSong.title"
    onerror="this.src = 'https://www.frosinonecalcio.com/wp-content/uploads/2021/09/default-placeholder.png'">
    <span class="text-tile">{{singleSong.title}}</span>           
      <div class="cont-subtitle">
        <span class="subtitle">{{singleSong.author}}</span>
        <span class="subtitle">{{singleSong.year}}</span>
      </div>          
  </div>
</template>

<script>
export default {
  props:{
    singleSong: Object,
  },
}
</script>

<style lang="scss" scoped>
  
  @import "@/style/variables.scss";
  
  .card-content{
    background-color: $bg-color-secondary;
    padding: 15px 15px;
    width: 100%;
    height: 100%;

    img{
      margin: 0 auto;
    }

    .text-tile{
      padding-top: 20px;
      text-align: center;
      display: block;
      font-weight: 900;
      text-transform: uppercase;
      line-height: 1.1;
      font-size: 22px;
    }

    .cont-subtitle{
        padding-top: 20px;
        
      .subtitle{
        text-align: center;
        display: block;
        font-size: 14px;
        color: $text-subtitle;
      }
    }     
  }
</style>