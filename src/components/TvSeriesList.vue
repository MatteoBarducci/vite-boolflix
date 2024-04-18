<script>
    import { store } from '../store';
    import Card from './Card.vue'


    export default{
        name: 'TvSeriesList',
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
        <Card v-for="tvSerie in store.TvSeriesInfo" :tvInfo="tvSerie"></Card>
    </div>
</template>

<style scoped lang="scss">
@use '../style/partials/variables.scss' as *;

.main-container{
    display: flex;
    flex-wrap: wrap;
}

</style>