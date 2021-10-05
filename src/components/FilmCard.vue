<template>
      <div class="col-3 p-3 mb-4">
          <h2>{{ movie.title }}</h2>
          <h4>{{ movie.original_title }}</h4>
          <p>{{ movie.vote_average }}</p>
          <!-- DA RIVEDERE -->
          <img v-if="movie.original_language == 'it'" src="https://upload.wikimedia.org/wikipedia/commons/thumb/0/03/Flag_of_Italy.svg/1599px-Flag_of_Italy.svg.png" alt="">
          <img v-else-if="movie.original_language == 'en'" src="https://upload.wikimedia.org/wikipedia/commons/thumb/8/83/Flag_of_the_United_Kingdom_%283-5%29.svg/1600px-Flag_of_the_United_Kingdom_%283-5%29.svg.png" alt="">
          <p v-else>{{ movie.original_language }}</p>
      </div>
</template>

<script>
export default {
    name: 'FilmCard',
    props: ["movie"]

}
</script>

<style scoped lang="scss">
img{
    height: 20px;
}

</style>