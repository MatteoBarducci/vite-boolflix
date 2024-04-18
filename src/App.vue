<script>
  import axios from 'axios';
  import { store } from './store';
  import AppSearch from './components/AppSearch.vue';
  import MovieList from './components/MovieList.vue';
  import TvSeriesList from './components/TvSeriesList.vue';



  export default{
    components: {
      AppSearch,
      MovieList,
      TvSeriesList,
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
  <AppSearch @searchMovie="getMoviesFromApi, getSeriesFromApi"></AppSearch>
  <MovieList></MovieList>
  <TvSeriesList></TvSeriesList>
</template>

<style lang="scss">
  @use './style/generic.scss';


</style>