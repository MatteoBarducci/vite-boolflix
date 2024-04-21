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
        <img :src="getImageUrl(cardInfo.poster_path)">
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
        height: 100%;
    }
}

</style>