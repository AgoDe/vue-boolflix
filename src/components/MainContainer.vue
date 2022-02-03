<template>
    <main>

        <div class="movies-container">
            <div class="movie-card">
                <img src="" alt="">

                <div class="movie-info">
                    <div>
                        <span>Titolo:</span>
                        <span>The Avengers</span>
                    </div>
                    <div>
                        <span>Titolo originale:</span>
                        <span>The Avengers</span>
                    </div>
                    <div>
                        <span>voto:</span>
                        <span>5</span>
                    </div>

                </div>


            </div>
        </div>
    </main>
</template>

<script>
export default {
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
    

    .movie-card {
        width: 200px;
        height: 300px;

        border: white 1px solid;
    }
}

</style>