<template>
    <main>

        <div class="movies-container">
           
           <movie-card
            v-for="movie in filteredMovies"
            :key="movie.id"
            :movie="movie"
           />
        </div>
    </main>
</template>

<script>
import MovieCard from './MovieCard.vue'
export default {
  components: { MovieCard },
    props: {
        filteredMovies: Array,

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
    
}

</style>