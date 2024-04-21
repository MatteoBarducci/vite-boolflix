<script>
  import axios from 'axios';
  import { store } from './store';
  import AppHeader from './components/AppHeader.vue';
  import Results from './components/Results.vue';




  export default{
    components: {
      AppHeader,
      Results,
    },
    data() {
      return {
        store,
      };
    },
    methods: {
      getMoviesFromApi(){
        const apiUrl = 'https://api.themoviedb.org/3/search/movie';
        let queryParams = {
          api_key : 'e4248d98725290d3fc86ce4ddabdd358',
        };
        if (store.searchedMovie !== ''){
          queryParams.query = store.searchedMovie
        }

        axios.get(apiUrl, {params: queryParams})
        .then((response) => {
          store.MoviesInfo = response.data.results
        })
      },
      getSeriesFromApi(){
        const apiUrl = 'https://api.themoviedb.org/3/search/tv';
        let queryParams = {
          api_key : 'e4248d98725290d3fc86ce4ddabdd358',
        };

        if (store.searchedMovie !== ''){
          queryParams.query = store.searchedMovie
        }

        axios.get(apiUrl, {params: queryParams})
        .then((response) => {
          store.TvSeriesInfo = response.data.results
        })
      },
    },
    mounted(){
    }
  }
</script>

<template>
  <div id="main-bg">
    <header>
      <AppHeader @searchMovie="getMoviesFromApi(); getSeriesFromApi()"></AppHeader>
    </header>
    <main>
      <Results></Results>
    </main>
  </div>
</template>

<style lang="scss">
  @use './style/generic.scss';

#main-bg{
  background-color: black;
  height: 100%;
  min-height: 100vh;
  padding-bottom: 50px;
}


</style>