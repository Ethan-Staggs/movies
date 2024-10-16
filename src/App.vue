<template>
  <div id="app">
    <ViewMovies/>
  </div>
</template>

<script>

import ViewMovies from './components/ViewMovies.vue'
// import TopBar from './components/TopBar.vue'


export default {
  name: 'App',
  components: {
    ViewMovies
  }
}
</script>

<style>
#app {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  gap: 5px;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}


</style>
