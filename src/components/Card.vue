<script>

    export default{
        name: 'Card',
        props:{
            movieInfo : Object
        }
    }
</script>

<template>
    <div class="card-container">
        <div>{{ movieInfo.title }}</div>
        <div>{{ movieInfo.original_title }}</div>
        <div>{{ movieInfo.original_language }}</div>
        <div>{{ movieInfo.vote_average }}</div>
    </div>
</template>

<style scoped lang="scss">
@use '../style/partials/variables.scss' as *;

.card-container{
    display: flex;
    flex-direction: column;
    width: calc((100% / 4) - 20px);
    margin: 30px 0;
    border: dashed;
    height: max-content
}

</style>