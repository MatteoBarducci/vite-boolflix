<script>

    export default{
        name: 'Card',
        props:{
            cardInfo: Object
        },
        data() {
            return {
                imgUrl: 'https://image.tmdb.org/t/p/w342',
                supportedFlags: [
                    'fr',
                    'it',
                    'en',
                    'es',
                    'ja',
                    'cn',
                    'zh'
                ]
            };
        },
        methods: {
            getFlag(){
                let flag;

                if(this.cardInfo.original_language === 'en'){
                    flag = '🇬🇧';
                } else if (this.cardInfo.original_language === 'it'){
                    flag = '🇮🇹';
                } else if (this.cardInfo.original_language === 'es'){
                    flag = '🇪🇸';
                } else if (this.cardInfo.original_language === 'fr'){
                    flag = '🇫🇷';
                } else if (this.cardInfo.original_language === 'ja'){
                    flag = '🇯🇵';
                } else if (this.cardInfo.original_language === 'cn'||'zh'){
                    flag = '🇨🇳';
                }
                return flag
            },
            getImageUrl(imagePath) {
                return new URL('https://image.tmdb.org/t/p/w342'+imagePath, import.meta.url).href
            },
            getRoundedVote(vote){
                let halfVote = vote/2
                return Math.round(halfVote)
            },
        }
    }
</script>

<template>
    <div class="card-container">
        <!-- Immagine -->
        <div class="img-container">
            <img :src="getImageUrl(cardInfo.poster_path)" v-if="cardInfo.poster_path">
            <div class="no-img" v-else>Immagine non disponibile</div>
        </div>

        <!-- Info -->
        <div class="info">
            <!-- Titoli -->
            <div><strong>Titolo: </strong>{{ cardInfo.title ? cardInfo.title : cardInfo.name }}</div>
            <div><strong>Titolo originale: </strong>{{  cardInfo.title ? cardInfo.original_title : cardInfo.original_name }} </div>
            <!-- Lingua originale -->
            <div>
                <strong>Lingua originale: </strong>
                <span v-if="supportedFlags.includes(cardInfo.original_language)">{{ getFlag() }}</span>
                <span v-else>{{ cardInfo.original_language }}</span>
            </div>
            <!-- Voto -->
            <div><strong>Media dei voti: </strong>{{ getRoundedVote(cardInfo.vote_average) }} </div>
        </div>
    </div>
</template>

<style scoped lang="scss">
@use '../style/partials/variables.scss' as *;

.card-container{
    display: flex;
    margin-right: 20px;
    width: 240px;
    height: 300px;
    flex-shrink: 0;
    position: relative;
    border-radius: 10px;

    .info{
        padding: 10px;
        display: flex;
        flex-direction: column;
        gap: 15px;
    }

    
    .img-container{
        position: absolute;
        opacity: 1;
        transition: 0.5s;
        
        .no-img{
            width: 240px;
            height: 300px;
            text-align: center;
            background-color: black;
        }

        &:hover{
            opacity: 0;
            transition: 0.5s;
        }
    }

    img{
        width: 240px;
        height: 300px;
        border-radius: 10px;
    }
}

</style>