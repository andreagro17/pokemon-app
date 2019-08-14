<template>
  <section class="pokemon-list">
    <ul class="pokemon-list__ul">
      <pokemon-cards
        v-for="pepe in api.results"
          :key = "pepe.name"
          :name = "pepe.name"
          :url = "pepe.url"/>
        </ul>
      <div class=""></div>
   <button class="btn btn-primary" v-if="api.previous" @click="previous">Previous</button>
   <button class="btn btn-primary" v-if="api.next" @click="next">Next</button>
  </section>
</template>

<script>
import axios from 'axios'
import PokemonCards from '@/components/Hero/PokemonCards'

export default {

  name: 'PokemonList',

  components: {
    PokemonCards
  },

  data () {
    return {
      api: {}
    }
  },
  created () {
    this.fetchPokemons()
  },
  methods: {
    fetchPokemons (url = 'https://pokeapi.co/api/v2/pokemon') {
      axios.get(url)
        .then(res => { this.api = res.data })
    },
    next () {
      this.fetchPokemons(this.api.next)
    },
    previous () {
      this.fetchPokemons(this.api.previous)
    }
  }
}
</script>

<style lang="scss" scoped>
.pokemon-list {
  &__ul {
    display: flex;
    flex-wrap: wrap;
  }
}

</style>
