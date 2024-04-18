<script>

    export default{
        name: 'Card',
        props:{
            movieInfo : Object,
            tvInfo: Object,
        }
    }
</script>

<template>
    <div class="card-container">
        <div><strong>Titolo: </strong>{{ movieInfo.title }} {{ tvInfo.name }}</div>
        <div><strong>Titolo originale: </strong>{{ movieInfo.original_title }} {{ tvInfo.original_name }}</div>
        <div><strong>Lingua originale: </strong>{{ movieInfo.original_language }} {{ tvInfo.original_language }}</div>
        <div><strong>Media dei voti: </strong>{{ movieInfo.vote_average }} {{ tvInfo.vote_average }}</div>
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
}

</style>