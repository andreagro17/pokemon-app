<template>
  <section class="search">
    <div class="search__navbar">
      <input type="text"
      v-model="searchP"
      placeholder="Looking for pokemons..."
      v-on:keyup.enter="pokemonSelect">
      <p> Pokedex is searching...: {{searchP}} </p>
    </div>
    <div class="search__lista-todos">
      <ul
        @click="pokemonSelect(detail.name)">
        <li v-for="pok2 of filteredPokemon"
        v-bind:name="pok2.name"
        v-show="searchP"
        :key="pok2.name">
        <span> {{pok2.name}} </span>
        </li>
      </ul>
    </div>
      <pokemon-detail
      :name = "name"
      v-show="searchP"/>
  </section>

</template>
<script>
import axios from 'axios'
import PokemonDetail from '@/components/Hero/PokemonDetail'

export default {
  name: 'Search',
  components: {
    PokemonDetail
  },
  data () {
    return {
      pokemon: null,
      name: '',
      detail: '',
      searchP: '',
      pokemons: []

    }
  },
  mounted () {
    this.pokemonComplete()
  },
  methods: {
    async pokemonComplete () {
      try {
        let res = await axios.get('https://pokeapi.co/api/v2/pokemon/?limit=386')
        this.pokemons = res.data.results
        this.name = res.data.results.name
      } catch (e) {
        throw new Error('Buscando el pokemon...')
      }
    },
    async pokemonSelect () {
      try {
        this.name = this.searchP
      } catch (e) {
        throw new Error('Buscando el pokemon...')
      }
    }
  },
  computed: {
    filteredPokemon (searching) {
      return this.pokemons.filter(poke => {
        return poke.name.includes(this.searchP)
      })
    }
  }
}
</script>

<style lang="scss" scoped>
.search {
  position: relative;
  padding-bottom: 50px;
  &__lista-todos {
    position: absolute;
    width: 100%;
    background: #fff;
    box-shadow: 0 4px 6px -1px rgba(0,0,0,.15);
    max-height: 200px;
    overflow-y: scroll;
    li {
      list-style: none;
    }
  }
}
</style>
