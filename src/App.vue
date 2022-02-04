<template>
  <div id="app">

    <!-- header container -->
    <header-container
    @searchApi="searchApi"
    @activeSearch="activeSearch"
    />
    <!-- / header container -->

    <!-- main container -->
    <main-container
    @searchApi="searchApi"
    :generalFilter="generalFilter"
    :searchVisible="searchVisible"
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
    MainContainer,
  },
  data() {
    return {
      filteredMovies: [],
      filteredTv: [],
      generalFilter: [],
      searchVisible: false,
      
    }
  },
  methods: {
    activeSearch: function() {
      this.searchVisible = true
    },

    searchApi: function(searchInput) {

      this.generalFilter = [];
      axios.get(`https://api.themoviedb.org/3/search/movie/?api_key=ad1668ee1fca2cd9ebdd9b7319f4ce6c&query=${searchInput}`).then((response) => {
        this.filteredMovies = response.data.results;
        this.filteredMovies.forEach(element => {
          element.type = 'movie';
          this.generalFilter.push(element)
        });
      }); 

      axios.get(`https://api.themoviedb.org/3/search/tv/?api_key=ad1668ee1fca2cd9ebdd9b7319f4ce6c&query=${searchInput}`).then((response) => {
        this.filteredTv = response.data.results;
        this.filteredTv.forEach(element => {
          element.type = 'tv';
        this.generalFilter.push(element)
        });
      });  
    },

  },
  // end methods
}
</script>

<style lang="scss">
@import url('https://use.fontawesome.com/releases/v5.7.1/css/all.css');
@import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@300;400;700&display=swap');
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: 'Montserrat', sans-serif;
}
 #app {
   background: black;
   color: #f9f9f9;
   height: 100vh;
 }
</style>
