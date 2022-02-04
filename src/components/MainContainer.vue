<template>
    <main>

        <div class="home-container">

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

            <movie-card
            v-for="item in generalFilter"
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
        searchVisible: Boolean,

    },
    data() {
        return {
            searchInput: ''
        }
    },
}
</script>

<style lang="scss" scoped>

main {
    background: linear-gradient(0deg, rgba(48,52,67,1) 6%, rgba(0,0,0,1) 94%, rgba(0,0,0,1) 94%);
    height: calc(100vh - 80px);


    
    .search-container {
        width: 100%;
        display: flex;
        flex-wrap: wrap;
        justify-content: space-around;
        
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
    }
}

</style>