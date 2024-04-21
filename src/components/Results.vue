<script>
    import { store } from '../store';
    import Card from './Card.vue'


    export default{
        name: 'Results',
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
    <section>
        <h1>Film</h1>
        <div class="main-container">
            <Card v-for="movie in store.MoviesInfo" :cardInfo="movie"></Card>
        </div>
    </section>

    <section>
        <h1>Serie tv</h1>
        <div class="main-container">
            <Card v-for="tvSerie in store.TvSeriesInfo" :cardInfo="tvSerie"></Card>
        </div>
    </section>
</template>

<style scoped lang="scss">
@use '../style/partials/variables.scss' as *;

.main-container{
    display: flex;
    flex-wrap: nowrap;
    color: white;
    overflow-x: auto;
}

h1{
    margin: 30px 0 18px;
    text-align: center;
    color: white;
    font-size: 30px;
}
</style>