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
   <span> {{ pageCount }} {{numberOfPages}} </span>
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
      api: {},
      pageCount: 1,
      perPage: 20,
      numberOfPages: ''
    }
  },
  created () {
    this.fetchPokemons()
  },
  methods: {
    fetchPokemons (url = 'https://pokeapi.co/api/v2/pokemon') {
      axios.get(url)
        .then(res => { this.api = res.data })
      console.log(1, this.api.length)
    },
    next () {
      this.fetchPokemons(this.api.next)
      this.pageCount = this.pageCount + 1
    },
    previous () {
      this.fetchPokemons(this.api.previous)
      this.pageCount = this.pageCount - 1
    },
    numberPage () {
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
