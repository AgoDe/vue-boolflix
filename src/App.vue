<template>
  <div id="app">
    
    <!-- header container -->
    <header-container
    @searchApi="searchApi"
    />
    <!-- / header container -->

    <!-- main container -->
    <main-container
    :filteredMovies="filteredMovies"
    />
    <!-- / main container -->

  

  </div>
</template>

<script>
import axios from 'axios'
import HeaderContainer from './components/HeaderContainer.vue';
import MainContainer from './components/MainContainer.vue';


export default {
  components: {
    HeaderContainer,
    MainContainer 
  },
  data() {
    return {
      filteredMovies: [],
    }
  },
  methods: {
    searchApi: function(searchInput) {
      axios.get(`https://api.themoviedb.org/3/search/movie/?api_key=ad1668ee1fca2cd9ebdd9b7319f4ce6c&query=${searchInput}`).then((response) => {
        console.log('data',response.data)
        console.log('input', searchInput)

        this.filteredMovies = response.data.results;
      })
    }
  }

}
</script>

<style lang="scss">

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
 #app {
   background: rgb(25, 25, 25);
   color: white;
 }
</style>
