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
        <h2>Film</h2>
        <div class="main-container">
            <Card v-for="movie in store.MoviesInfo" :cardInfo="movie"></Card>
        </div>
    </section>

    <section>
        <h2>Serie tv</h2>
        <div class="main-container">
            <Card v-for="tvSerie in store.TvSeriesInfo" :cardInfo="tvSerie"></Card>
        </div>
    </section>
</template>

<style scoped lang="scss">
@use '../style/partials/variables.scss' as *;

.main-container{
    display: flex;
    flex-wrap: wrap;

}

h2{
    margin-bottom: 20px;
    text-align: center;
}
</style>