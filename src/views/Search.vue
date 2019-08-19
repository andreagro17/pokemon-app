<template>
  <section class="search">
    <div class="search__navbar">
      <input type="text"
      v-model="searchP"
      placeholder="Looking for pokemons..."
      v-on:keyup.enter="pokemonSelect">
      <i class="fa fa-search" @click="pokemonSelect">
      </i>
      <p> Pokedex is searching...: {{searchP}} </p>
    </div>
    <div class="search__lista-todos">
      <ul>
        <li v-for="pok2 of filteredPokemon"
        @click="pokemonComplete(pok2.name)"
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
      name: '',
      detail: '',
      searchP: '',
      pokemons: []

    }
  },
  async mounted () {
    let res = await axios.get('https://pokeapi.co/api/v2/pokemon/?limit=386')
    this.pokemons = res.data.results
  },
  methods: {
    async pokemonComplete (name) {
      try {
        this.name = name
      } catch (e) {
        throw new Error('Buscando el pokemon...')
      }
    },
    async pokemonSelect () {
      try {
        console.log(1, this.filteredPokemon.length)
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
i {
  color: #0A2E50;
  cursor: pointer;
}

</style>
