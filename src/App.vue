<template>
  <div id="app">
    
    <!-- header container -->
    <header-container
    @searchApi="searchApi"
    />
    <!-- / header container -->

    <!-- main container -->
    <main-container/>
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

        this.filteredMovies = response.data;
      })
    }
  }

}
</script>

<style lang="scss">

 #app {
   background: rgb(25, 25, 25);
 }
</style>
