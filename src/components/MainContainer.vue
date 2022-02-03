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

.movies-container { 

    display: flex;
    flex-wrap: wrap;
    justify-content: space-around;
    
}

</style>