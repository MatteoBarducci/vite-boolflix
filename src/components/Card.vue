<script>

    export default{
        name: 'Card',
        props:{
            movieInfo : Object,
            tvInfo: Object,
        },
        data() {
            return {
                imgUrl: 'https://image.tmdb.org/t/p/w342'
            };
        },
        methods: {
            getImageUrl(name) {
                return new URL(`${name}`, import.meta.url).href
            }
        }
    }
</script>

<template>
    <div class="card-container">
        <div><strong>Titolo: </strong>{{ movieInfo ? movieInfo.title : tvInfo.name }}</div>
        <div><strong>Titolo originale: </strong>{{  movieInfo ? movieInfo.original_title : tvInfo.original_name }} </div>
        <div><strong>Lingua originale: </strong>{{ movieInfo ? movieInfo.original_language : tvInfo.original_language }} </div>
        <div><strong>Media dei voti: </strong>{{ movieInfo ? movieInfo.vote_average : tvInfo.vote_average }} </div>
    </div>
</template>

<style scoped lang="scss">
@use '../style/partials/variables.scss' as *;

.card-container{
    display: flex;
    flex-direction: column;
    gap: 10px;
    width: calc((100% / 4) - 20px);
    margin: 30px 10px;
    border: dashed;
    height: 300px

    img{
        width: 100%;
    }
}

</style>