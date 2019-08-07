<template>
  <div id="app">
    <pokemon-header/>
    <router-view/>
    <pokemon-footer/>
  </div>
</template>

<script>
// @ is an alias to /src

import Header from '@/components/Shared/Header'
import Footer from '@/components/Shared/Footer'
export default {
  name: 'App',
  components: {
    PokemonHeader: Header,
    PokemonFooter: Footer
  }
}
</script>

<style lang="scss">
#app {
  font-family: 'Baloo Bhaina', Arial, sans-serif;
  font-weight: 400;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

</style>
