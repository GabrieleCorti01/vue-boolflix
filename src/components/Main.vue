<template>
  <div class="row">
    <div>
      <SearchBar />
    </div>

    <div v-for="el in filmList" :key="el.id">
      <FilmCard :element="el"/>
    </div>
  </div>
</template>

<script>
import FilmCard from './FilmCard.vue'
import axios from 'axios';
import SearchBar from './SearchBar.vue'

export default {
  name: 'Main',
  components: {
    FilmCard,
    SearchBar
  },

  data: function(){
    return{
      filmList: []
    }
  },

  created: function(){
    axios.get('https://api.themoviedb.org/3/search/movie?api_key=47c1ea959a92449f222c88cc1b40ea56&query=zombie')
      .then(res => {
        this.filmList = res.data.results;
        console.log(this.filmList)
      
      });
  },

  methods:{
    searchInFilms: function(target){
      this.target = target;
    }
  },

  computed:{
    filteredFilmsList: function(){
      const newFilmslist = this.filmList.filter(
        (element) =>{
          return element.name.toLowerCase().includes(this.target.toLowerCase())
        }
      )
    }
  }
}
</script>


<style scoped lang="scss">

</style>
