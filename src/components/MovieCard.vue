<template>
     <div class="movie-card"
     @mouseover="showInfo"
     @mouseleave="hideInfo"
     >

        <img 
        :src="posterVerify(item.poster_path)"
        :alt="item.original_title"
        >

        <!-- movie info (in card hover) -->
        <div 
        class="movie-info"
        v-if="infoActive" 
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
            <flag-lang :language="item.original_language"/>
            
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

            <div class=addfav>
                <i
                @click="$emit('removeFavorites', item)" 
                class="fas fa-times"
                v-if="favorites.includes(item)"
                else>
                </i>
                <i 
                @click="$emit('addFavorites', item)" 
                class="fas fa-heart"
                :class="{ active : favorites.includes(item)}">
                </i>

                
            </div>

        </div>
        <!-- movie info (in card hover) -->

    </div>
</template>

<script>
import axios from 'axios'
import FlagLang from './FlagLang.vue'
export default {
  components: {
    FlagLang,
    },
    props: {
        item: Object,
        favorites: Array,
        
    },
    data() {
        return {
            infoActive: false,
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
       voteStar: function(number) {
           return Math.round(number / 2)
        },
        showInfo: function() {
            this.infoActive = true
        },
        hideInfo: function() {
            this.infoActive = false
        }
        // getCredit: function(type, item) {

        //     axios.get('')

        // }
       
    },
    
}
</script>

<style lang="scss" scoped>
@import '@/styles/variables.scss';

    .movie-card {
        min-width: $card-width;
        max-width: $card-width;
        height: $card-height;
        position: relative;

        margin: 20px 0;
        

        img{
            width: 100%;
            height: 100%;
            object-fit: cover;
            border-radius: 2px;
        }
        .movie-info {
            // display: none;
            height: 100%;
            width: 100%;
            position: absolute;
            left: 0;
            top: 0;
            padding: 10px 8px;
            background: rgba($color: $background, $alpha: 0.9);

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
                bottom: 0px;
                left: 0;
                width: 110px;
                height: 40px;
                text-align: left;
                padding-left: 5px;
                line-height: 50px;
                border-top-right-radius: 100% ;
                opacity: 0.5;
                box-shadow: 0 0 3px 1px blue;
            }
            .card-footer.movie {
                background: blue; 
                box-shadow: 0 0 3px 1px blue;
            }
            .card-footer.tv {
                background: green;
                box-shadow: 0 0 3px 1px green;
            }
            .addfav {
                position: absolute;
                right: 7px;
                bottom: 7px;       
                font-size: 30px;

                .fa-heart {
                    opacity: 0.6;
                    &:hover {
                        color: red;
                    }
                }
                .fa-heart.active {
                    color: red;
                    opacity: 1;
                }
                .fa-times {
                    opacity: 0.6;
                    display: none;
                }
                &:hover .fa-times {
                    display: block;
                }

            }

        }
        //  &:hover>.movie-info{
        //         display: inline-block;
        //     }

    }

</style>