<template>
  <div id="app">
    <Header @searchText="searchMovies"/>
    <Main :movieArray="movies" :serieArray="series"/>
  </div>
</template>

<script>
import axios from 'axios';
import Header from './components/Header.vue';
import Main from './components/Main.vue';

export default {
  name: 'App',
  components: {
    Header,
    Main
  },
  data() {
    return {
      apiUrl: 'https://api.themoviedb.org/3/search/',
      apiKey: 'api_key=55d1f55576628785ddb97e8351b254a0',
      movies: [],
      series: [],
    }
  },
  methods: {
    searchMovies(searchText) {
      axios
          .get(this.apiUrl + 'movie?' + this.apiKey + "&query=" + searchText)
          .then(response => {
            console.log(response.data.results)
            this.movies = response.data.results
          })
          
      axios
          .get(this.apiUrl + 'tv?' + this.apiKey + "&query=" + searchText)
          .then(response => {
            console.log(response.data.results)
            this.series = response.data.results
          })
    },
  }
}
</script>

<style lang="scss">
@import './style/general.scss';
</style>
