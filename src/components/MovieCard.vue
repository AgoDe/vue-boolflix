<template>
     <div
        class="movie-card">
                <img 
                :src="`https://image.tmdb.org/t/p/w342${movie.poster_path}`"
                :alt="movie.original_title">
                <div 
                class="movie-info"
                >
                        <h3>Titolo: </h3>
                        <div>{{movie.title}}</div>
                   
                        <div v-if="!(movie.original_title === movie.title)">
                            <h3 class="title">Titolo originale: </h3>
                            <div>{{movie.original_title}}</div>
                        </div>
                   
                        <h3
                        
                         class="title">Lingua originale: </h3>
                        <img
                            :alt="`${movie.original_language}-fla`"
                            :src="`http://purecatamphetamine.github.io/country-flag-icons/3x2/${flagLang(movie.original_language)}.svg`"/>
                    
                        <h3 class="title">Voto: </h3>
                        <div>{{movie.vote_average}}</div>
                    

                </div>
            </div>
</template>

<script>
export default {
    props: {
        movie: Object,
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

        img{
            width: 100%;
            height: 100%;
            object-fit: cover;
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