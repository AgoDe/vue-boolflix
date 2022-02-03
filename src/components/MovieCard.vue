<template>
     <div class="movie-card">
                <img src="" alt="">

                <div class="movie-info">
                    <div>
                        <span>Titolo: </span>
                        <span>{{movie.title}}</span>
                    </div>
                    <div>
                        <span>Titolo originale: </span>
                        <span>{{movie.original_title}}</span>
                    </div>
                    <div>
                        <span>Lingua originale: </span>
                        <span>{{movie.original_language}}</span>
                    </div>
                    <div>
                        <span>voto: </span>
                        <span>{{movie.vote_average}}</span>
                    </div>

                </div>
            </div>
</template>

<script>
export default {
    props: {
        movie: Object,
    }
    
}
</script>

<style lang="scss" scoped>

    .movie-card {
        width: 200px;
        height: 300px;

        border: white 1px solid;
    }

</style>