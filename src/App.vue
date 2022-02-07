<template>
  <div id="app">

    <!-- header container -->
    <header-container
    @searchApi="searchApi"
    @activeSearch="activeSearch"
    @activeHome="activeHome"
    @activeFavorites="activeFavorites"

    />
    <!-- / header container -->

    <!-- main container -->
    <main-container
    @searchApi="searchApi"
    @addFavorites="addFavorites"
    @removeFavorites="removeFavorites"
    :generalFilter="generalFilter"
    :searchVisible="searchVisible"
    :homeVisible="homeVisible"
    :favoritesVisible="favoritesVisible"
    :popularMovies="popularMovies"
    :popularTv="popularTv"
    :favorites="favorites"
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
      popularMovies: [],
      popularTv: [],
      favorites: [],
      searchVisible: false,
      homeVisible: true,
      favoritesVisible: false,
      
    }
  }, // end of data
  mounted() {
    // array popular movies
    axios.get('https://api.themoviedb.org/3/movie/popular?api_key=ad1668ee1fca2cd9ebdd9b7319f4ce6c').then((res) => {
      for(let i = 0; i < 20; i++) {
        res.data.results[i].type = 'movie'
        this.popularMovies.push(res.data.results[i])
      }
    })

    // array popular tv
    axios.get('https://api.themoviedb.org/3/tv/popular?api_key=ad1668ee1fca2cd9ebdd9b7319f4ce6c').then((res) => {
      for(let i = 0; i < 20; i++) {
        res.data.results[i].type = 'tv'
        this.popularTv.push(res.data.results[i])
      }
    })
  }, // end of mounted
  methods: {
    addFavorites: function(item) {
        this.favorites.push(item)
        console.log('aggiunto')
    },
    removeFavorites: function(item) {
        const filtered = this.favorites.filter((res) => {
          return res != item
        })
        this.favorites = filtered
        console.log(filtered)
    },
    activeSearch: function() {
      this.searchVisible = true
      this.homeVisible = false;
      this.favoritesVisible = false;
    },
    activeHome: function() {
      this.homeVisible = true;
      this.searchVisible = false;
      this.favoritesVisible = false;
    },
    activeFavorites: function() {
      this.favoritesVisible = true;
      this.homeVisible = false;
      this.searchVisible = false;
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
  }, // end of methods
  
}
</script>

<style lang="scss">
@import '@/styles/variables.scss';

@import url('https://use.fontawesome.com/releases/v5.7.1/css/all.css');
@import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@300;400;700&display=swap');

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: 'Avenir-Roman',sans-serif;

  /* scrollbar */
  ::-webkit-scrollbar{
    width:0.5em;
    height:0.5em;
    margin-right: 10px;
  }
  ::-webkit-scrollbar-thumb{
    min-height:0.8em;
    min-width:0.8em;
    -webkit-border-radius:4px;
    background-color: #303443;
    border: none;
  }
  ::-webkit-scrollbar:active{
    background-color:#414450;
  }
  /* / scrollbar */
}
 #app {
   background: linear-gradient(0deg, rgba(48,52,67,1) 6%, rgba(0,0,0,1) 94%, rgba(0,0,0,1) 94%);
   color: #f9f9f9;
   max-height: 100vh;
 }
</style>
