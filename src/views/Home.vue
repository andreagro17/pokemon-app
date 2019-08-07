<template>
  <section class="pokemon-list">
    <pokemon-list/>
  </section>
</template>

<script>
// @ is an alias to /src
import PokemonList from '@/components/Hero/PokemonList'
export default {
  name: 'home',

  components: {
    PokemonList
  }
}
</script>

<style lang="scss">

</style>
