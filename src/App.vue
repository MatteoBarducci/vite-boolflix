<script>
  import axios from 'axios';
  import { store } from './store';
  import AppSearch from './components/AppSearch.vue';

  export default{
    components: {
      AppSearch
    },
    data() {
      return {
        store,
      };
    },
    methods: {

    },
    mounted(){

    }
  }
</script>

<template>
  <AppSearch></AppSearch>
</template>

<style scoped lang="scss">
  @use './style/generic.scss';


</style>