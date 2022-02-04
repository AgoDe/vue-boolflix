<template>
     <div
        class="movie-card">
                <img 
                :src="posterVerify(item.poster_path)"
                :alt="item.original_title">
                <div 
                class="movie-info"
                >
                        
                        <h3>Titolo: </h3>
                        <div v-if="item.type == 'movie'">{{item.title}}</div>
                        <div v-else >{{item.name}}</div>
                   
                        <div v-if="!(item.original_title === item.title) && item.type == 'movie'">
                            <h3>Titolo originale: </h3>
                            <div>{{item.original_title}}</div>
                        </div>
                        <div v-if="!(item.original_name === item.name)">
                            <h3>Titolo originale: </h3>
                            <div>{{item.original_title}}</div>
                        </div>
                   
                        <h3>Lingua originale: </h3>
                        <img
                        :alt="`${item.original_language}-flag`"
                        :src="`http://purecatamphetamine.github.io/country-flag-icons/3x2/${flagLang(item.original_language)}.svg`"
                        />
                    
                        <h3 class="title">Voto: </h3>
                        <div>
                            <i 
                            v-for="index in voteStar(item.vote_average)"
                            :key="index"
                            class="fas fa-star"></i>
                        </div>

                        <!-- card footer -->
                        <div class="card-footer movie" v-if="item.type == 'movie'">
                            MOVIE
                        </div>
                        <div 
                        class="card-footer tv" v-else>
                            TV SERIES
                        </div>
                        <!-- / card footer -->

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
        posterVerify: function(item) {
            if (item == null) {
                return 'https://montagnolirino.it/wp-content/uploads/2015/12/immagine-non-disponibile.png'
            } else {
                return `https://image.tmdb.org/t/p/w342${item}`
            }
        },
       flagLang: function(language) {
         return language === 'en' ? 'GB' : language.toUpperCase();
       },
       voteStar: function(number) {
           return Math.round(number / 2)
        }
    },
    
}
</script>

<style lang="scss" scoped>
@import url('https://use.fontawesome.com/releases/v5.7.1/css/all.css');

    .movie-card {
        min-width: 200px;
        max-width: 200px;
        height: 300px;
        position: relative;
        margin: 20px 20px;
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
            background: rgba($color: #303443, $alpha: 0.9);

            text-align: center;

            h3 {
                margin-top: 10px;
                margin-bottom: 5px;
            }
            img {
                width: 30px;
                height: 20px;
            }   
            .fa-star {
                color: gold;
                margin: 2px;
            }
            .card-footer {
                position: absolute;
                bottom: 1px;
                left: 0;
                width: 100%;
                text-align: center;
                border-radius: 3px;
                opacity: 0.8;
            }
            .card-footer.movie {
                background: blue;
            }
            .card-footer.tv {
                background: green;
            }

        }
         &:hover>.movie-info{
                display: inline-block;
            }

    }

</style>