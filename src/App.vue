<template>
  <div id="app">
    <species-overview ></species-overview>
  </div>
</template>

<script>
import SpeciesOverview from './components/SpeciesOverview.vue'

export default {
  name: 'App',
  components: {
    SpeciesOverview
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
