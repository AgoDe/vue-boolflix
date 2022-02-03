<template>
    <main>

        <div class="movies-container">
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
// import TvCard from './TvCard.vue'

export default {
  components: { 
    MovieCard,
    // TvCard,
   },
    props: {
        generalFilter: Array,

    },
    data() {
        return {

        }
    },
}
</script>

<style lang="scss" scoped>

main {
    background: linear-gradient(0deg, rgba(48,52,67,1) 6%, rgba(0,0,0,1) 94%, rgba(0,0,0,1) 94%);
    height: calc(100vh - 80px);


    
    .movies-container { 
        display: flex;
        flex-wrap: wrap;
        justify-content: space-around;
        
    }
}

</style>