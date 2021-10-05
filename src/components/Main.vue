<template>
  <!-- Sezione ricerca Film -->
  <div class="row">
    <h2>Film trovati:</h2>
    <FilmCard v-for="movie in movies" :key="movie.id" :movie="movie"/>
    <h2>Serie trovate:</h2>
    <FilmCard v-for="serie in series" :key="serie.id" :movie="serie"/>
  </div>

  <!-- Sezione ricerca Series -->

</template>

<script>
import FilmCard from './FilmCard.vue'

export default {
  name: 'Main',
  props: {
    "movies" : Array,
    "series" : Array,
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