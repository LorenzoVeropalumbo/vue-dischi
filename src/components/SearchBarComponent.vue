<template>
  <div class="container">
    <select 
      id="stand" 
      @change="switchSelectGen($event)" 
      value="0"
    >
      <option value="All">All</option>
      <option value="Metal">Metal</option>
      <option value="Rock">Rock</option>
      <option value="Jazz">Jazz</option>
      <option value="Pop">Pop</option>
    </select>

    <select 
      id="stand" 
      @change="switchSelectArt($event)" 
    >
      
      <option v-for="song,index in Albumobj" :key="index" :value="song.author">{{song.author}}</option>
      <option value="All">All</option>
    </select>
  </div>
</template>

<script>
  export default {
    name: 'SearchBarComponent',
    
    props:{
      Albumobj: Array,
    },
    methods: {
      switchSelectGen(select){       
        this.$emit("selectGenere", select.target.value);
      },
      switchSelectArt(select){       
        this.$emit("selectCantante", select.target.value);
      }
    }
  }
</script>

<style lang="scss" scoped>
  select{
    margin: 0 10px;
    padding: 5px 90px 5px 5px;
    border-radius: 20px;
  }
</style>