<template>
  <!-- Sezione ricerca Film -->
  <div class="row">
    <h2>Film trovati:</h2>
    <FilmCard v-for="movie in movies" :key="movie.id" :movie="movie"/>
    <SeriesCard v-for="show in series" :key="show.id" :show="show"/>
  </div>

  <!-- Sezione ricerca Series -->

</template>

<script>
import FilmCard from './FilmCard.vue'
import SeriesCard from './SeriesCard.vue'

export default {
  name: 'Main',
  props: {
    "movies" : Array,
    "series" : Array,
  },
  components: {
    FilmCard,
    SeriesCard,
  },
  data : function(){
    return {

    }
  }
}
</script>

<style>

</style>