<template>
     <div
        class="movie-card">
                <img 
                :src="`https://image.tmdb.org/t/p/w342${item.poster_path}`"
                :alt="item.original_title">
                <div 
                class="movie-info"
                >
                        <h3 v-if="item.type == 'movie'">MOVIE</h3>
                        <h3 v-else>TV SERIES</h3>
                        <h3>Titolo: </h3>
                        <div v-if="item.type == 'movie'">{{item.title}}</div>
                        <div v-else >{{item.name}}</div>
                   
                        <div v-if="!(item.original_title === item.title) && item.type == 'movie'">
                            <h3 class="title">Titolo originale: </h3>
                            <div>{{item.original_title}}</div>
                        </div>
                        <div v-if="!(item.original_name === item.name)">
                            <h3 class="title">Titolo originale: </h3>
                            <div>{{item.original_title}}</div>
                        </div>
                   
                        <h3
                        
                         class="title">Lingua originale: </h3>
                        <img
                            :alt="`${item.original_language}-fla`"
                            :src="`http://purecatamphetamine.github.io/country-flag-icons/3x2/${flagLang(item.original_language)}.svg`"/>
                    
                        <h3 class="title">Voto: </h3>
                        <div>{{item.vote_average}}</div>
                    

                </div>
            </div>
</template>

<script>
export default {
    props: {
        item: Object,
    },
    data() {
        return {
            
        }
    },
    methods: {
       flagLang: function(language) {
         return language === 'en' ? 'GB' : language.toUpperCase();
       }
        
    }
    
}
</script>

<style lang="scss" scoped>


    .movie-card {
        width: 200px;
        height: 300px;
        position: relative;
        margin: 30px 20px;
        box-shadow:  2px 2px 7px 4px #303443;
        border-radius: 2px;

        img{
            width: 100%;
            height: 100%;
            object-fit: cover;
            border-radius: 2px;
        }
        .movie-info {
            display: none;
            height: 100%;
            width: 100%;
            position: absolute;
            left: 0;
            top: 0;
            padding: 10px 8px;
            background: rgba($color: #333, $alpha: 0.8);

            text-align: center;

            h3 {
                margin-top: 10px;
                margin-bottom: 5px;
            }
            img {
                width: 30px;
                height: 20px;
            }

           
            
        }
         &:hover>.movie-info{
                display: inline-block;
            }
    }

</style>