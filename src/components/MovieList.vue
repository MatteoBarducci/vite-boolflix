<script>
    import { store } from '../store';
    import Card from './Card.vue'


    export default{
        name: 'MovieList',
        components: {
            Card,
        },
        data() {
            return{
                store
            }
        },
    }
</script>

<template>
    <div class="main-container">
        <Card v-for="movie in store.MoviesInfo" :movieInfo="movie"></Card>
    </div>
</template>

<style scoped lang="scss">
@use '../style/partials/variables.scss' as *;

.main-container{
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
}

</style>