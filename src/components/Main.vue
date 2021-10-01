<template>
  <div class="row">
    <div v-for="el in filmList" :key="el.id">
      <FilmCard :element="el"/>
    </div>
  </div>
</template>

<script>
import FilmCard from './FilmCard.vue'
import axios from 'axios';


export default {
  name: 'Main',
  components: {
    FilmCard,
  },

  data: function(){
    return{
      filmList: []
    }
  },

  created: function(){
    axios.get('https://api.themoviedb.org/3/search/movie?api_key=47c1ea959a92449f222c88cc1b40ea56&query=futuro')
      .then(res => {
        this.filmList = res.data.results;
        console.log(this.filmList)
      
      });
      // console.log(res.data.results[1].original_title);
  }
}
</script>


<style scoped lang="scss">

</style>
