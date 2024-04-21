<script>
    import { store } from '../store';

    export default{
        name: 'AppHeader',
        data() {
            return{
                store
            }
        },
    }
</script>

<template>
    <header>
        <div class="main-container">
            <div>
                <img src="https://upload.wikimedia.org/wikipedia/commons/7/7a/Logonetflix.png" alt="Logo netflix">
            </div>
            <nav>
                <input type="text" placeholder="Cerca il nome del film" v-model="store.searchedMovie">
                <button @click="$emit('searchMovie')">Search</button>
            </nav>
        </div>
    </header>
</template>

<style scoped lang="scss">
@use '../style/partials/variables.scss' as *;

header{
    height: 100px;

    .main-container{
        height: 100%;
        display: flex;
        align-items: center;
        justify-content: space-between;

        input, button{
            padding: 10px;
            margin-right: 15px;
            border: none;
            background-color: white;
            border-radius: 30px;
        }

        img{
            height: 80px;
        }
    }
}

</style>