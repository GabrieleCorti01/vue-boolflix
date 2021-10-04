<template>

  <div class="row">
    <h2>Film trovati:</h2>
    <FilmCard v-for="movie in movies" :key="movie.id" :movie="movie"/>
  </div>
</template>

<script>
import FilmCard from './FilmCard.vue'

export default {
  name: 'Main',
  props: {
    "movies" : Array
  },
  components: {
    FilmCard,
  },
  data : function(){
    return {

    }
  }
}
</script>

<style>

</style>