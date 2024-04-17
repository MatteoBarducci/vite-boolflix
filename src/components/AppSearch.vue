<script>
    import { store } from '../store';

    export default{
        name: 'AppSearch',
        data() {
            return{
                store
            }
        },
    }
</script>

<template>
    <section class="main-container">
        <input type="text" placeholder="Cerca il nome del film" v-model="store.searchedMovie">
        <button @click="$emit('searchMovie')">Search</button>
    </section>
</template>

<style scoped lang="scss">
@use '../style/partials/variables.scss' as *;

</style>