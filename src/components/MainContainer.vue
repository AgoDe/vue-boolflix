<template>
    <main>

        <div 
        class="home-container"
        v-if="homeVisible">
            <h3>Film più popolari</h3>
            <div class="popular-movie slider-box">
                <movie-card
                class="slider-card"
                v-for="item in popularMovies"
                :key="item.id"
                :item="item"
                @addFavorites="$emit('addFavorites', item)"
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
                @addFavorites="$emit('addFavorites', item)"
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
                />  
        </div>


    </main>
</template>

<script>
import MovieCard from './MovieCard.vue'


export default {
  components: { 
    MovieCard,
    
   },
    props: {
        generalFilter: Array,
        popularMovies: Array,
        popularTv: Array,
        favorites:Array,
        searchVisible: Boolean,
        homeVisible: Boolean,
        favoritesVisible: Boolean,
    },
    data() {
        return {
            searchInput: ''
        }
    },
    methods: {
    }
}
</script>

<style lang="scss" scoped>

main {
    background: linear-gradient(0deg, rgba(48,52,67,1) 6%, rgba(0,0,0,1) 94%, rgba(0,0,0,1) 94%);
    height: calc(100vh - 80px);
    

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
        
    }
    
    .search-container {
        width: 100%;
        max-height: 100%;
  
        input {
            width: 100%;
            height: 80px;
            background-color: #4b4e5a;
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
            width: 100%;
            height: 600px;
            overflow-y: auto;
            display: flex;
            flex-wrap: wrap;
            justify-content: space-around;
        }
    }

    .favorites-container {
           width: 100%;
            height: 680px;
            overflow-y: auto;
            display: flex;
            flex-wrap: wrap;
            justify-content: space-around;
    }
}

</style>