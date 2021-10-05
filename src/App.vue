<template>
  <div id="app">
    <Header @searching="cerca" />
    <Main :movies="films" :series="tvSeries"/>
  </div>
</template>

<script>
import Main from './components/Main.vue'
import Header from './components/Header.vue'
import axios from 'axios'


export default {
  name: 'App',
  components: {
    Main,
    Header,
  },
  methods:{
    cerca: function(needle){
      if(needle.length > 1){
        axios.get(this.apiUrl, {
        params: {
          api_key: this.apiKey,
          query: needle,
          language: 'it_IT'
        }
      }).then (
        (risposta) =>{
          this.films = [...risposta.data.results];
          console.log(this.films)
        })
        .catch(
          (errore) =>{
            console.warn("Errore nella richiesta!", errore)
          })
  // RICERCA SERIE TV
          axios.get(this.apiUrlSeries, {
          params: {
            api_key: this.apiKey,
            query: needle,
            language: 'it_IT'
          }
        }).then(
          (response) =>{
            this.tvSeries = [...response.data.results];
            console.log(this.tvSeries)
            
          })
          .catch(
            (errore) =>{
              console.warn("Errore nella richiesta!", errore)
            })
      }        
    }
  },
  data: function(){
    return{
      apiUrlSeries: 'https://api.themoviedb.org/3/search/tv',
      apiUrl: 'https://api.themoviedb.org/3/search/movie',
      apiKey: '47c1ea959a92449f222c88cc1b40ea56',
      films: [],
      tvSeries: []
    }
  }
}
</script>

<style lang="scss">
@import "~bootstrap/scss/bootstrap.scss";

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
