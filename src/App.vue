<template>
  <div id="app">
    
    <!-- header container -->
    <header-container/>
    <!-- / header container -->

    <!-- main container -->
    <main-container/>
    <!-- / main container -->

  </div>
</template>

<script>
import HeaderContainer from './components/HeaderContainer.vue'
import MainContainer from './components/MainContainer.vue'


export default {
  components: {
    HeaderContainer,
    MainContainer 
  },

}
</script>

<style lang="scss">

</style>
