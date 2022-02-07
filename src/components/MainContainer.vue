<template>
    <main>

        <div 
        class="home-container"
        v-if="homeVisible"
        >
            <h3>Film più popolari</h3>
            <div class="popular-movie slider-box">
                <movie-card
                class="slider-card"
                v-for="item in popularMovies"
                :key="item.id"
                :item="item"
                @addFavorites="$emit('addFavorites', item)"
                @removeFavorites="$emit('removeFavorites', item)"
                :favorites="favorites"
                />    
            </div>

            <h3>Serie TV più popolari</h3>
            <div class="popular-tv slider-box">
                <movie-card
                class="slider-card"
                v-for="item in popularTv"
                :key="item.id"
                :item="item"
                @addFavorites="$emit('addFavorites', item)"
                @removeFavorites="$emit('removeFavorites', item)"
                :favorites="favorites"
                />    
            </div>
        </div>

        <div  
        class="search-container"
        v-if="searchVisible"
        >
        
            <input 
            type="text"
            placeholder="Cerca per Titolo"
            v-model="searchInput"
            @keyup.enter="$emit('searchApi', searchInput)"
            >
            <div class="card-container">
                <movie-card
                v-for="item in generalFilter"
                :key="item.id"
                :item="item"
                :favorites="favorites"
                @addFavorites="$emit('addFavorites', item)"
                @removeFavorites="$emit('removeFavorites', item)"
                />    
            </div>
        </div>

         <div 
        class="favorites-container"
        v-if="favoritesVisible">
            
            <movie-card
            v-for="item in favorites"
            :key="item.id"
            :item="item"
            :favorites="favorites"
            @removeFavorites="$emit('removeFavorites', item)"
            />  
            
        </div>


    </main>
</template>

<script>
import MovieCard from './MovieCard.vue'

export default {
  components: { 
    MovieCard, 
   }, // end of componets
    props: {
        generalFilter: Array,
        popularMovies: Array,
        popularTv: Array,
        favorites:Array,
        searchVisible: Boolean,
        homeVisible: Boolean,
        favoritesVisible: Boolean,
    }, // end of props
    data() {
        return {
            searchInput: ''
        }
    }, // end of data

}  // end of export
</script>

<style lang="scss" scoped>
@import '@/styles/variables.scss';

main {
    height: calc(100% - 80px);

    .home-container {
        max-height: 100%;
        overflow-y: auto;
        h3 {
            margin-top: 15px;
        }
        .slider-box {
            display: flex;
            flex-shrink: 0;
            max-height: 360px;
            overflow-x: auto;
        }
    } // end of home-container
    
    .search-container {
        height: 100%;
  
        input {
            width: 100%;
            height: 80px;
            background-color: $input-background;
            border: none;
            padding-left: 40px;
            font-size: 35px;
            color: #A8A9AD;
            font-weight: bold;

            &:focus-visible {
                outline: none;
            }
            &::-webkit-input-placeholder {
                color: #A8A9AD;         
            }  
        }
        .card-container {
            margin: 0 auto;
            width: $container-width;
            height: calc(100% - 80px);
            overflow-y: auto;
            display: flex;
            flex-wrap: wrap;    
        }
    } // end of serch-container

    .favorites-container {
        margin: 0 auto;
        width: $container-width;
        height: 100%;
        overflow-y: auto;
        display: flex;
        flex-wrap: wrap;
        
    }
}

</style>