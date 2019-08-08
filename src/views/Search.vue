<template>
    <div>
      <div>
        <div class="prueba">
          <input
          type="text"
          class="prueba__form-control"
          v-model="textSearch"
          placeholder='Search...'>
         <button v-on:click="fetchPoke">Buscar</button>
         <button v-on:click="pokemonFilter">Buscar_filtro</button>
          <div v-for="pok2 of pokemonFilter" :key="pok2.name">
          <span>{{ pok2.name }}</span>
          </div>

        </div>
      <a :pokemon="pokemonFilter"/>
        <!-- <pokemon-detail/> esto funciona de moodo que si le doy a intro se cargan los pokemo y despues puedo hacer una busqueda por letras pero no e lo que busco -->
      </div>
    </div>

</template>
<script>
import axios from 'axios'
// import PokemonDetail from '@/components/Hero/PokemonDetail'
// con axios puedo hacer una "request"
// y pedir aquello del data ¿axios.put?
export default {
  name: 'Search',

  components: {
    // PokemonDetail
  },

  data () {
    return {
      pokemons: [],
      textSearch: '',
      searchPokemon: {}
    }
  },

  methods: {
    fetchPoke () {
    // https://router.vuejs.org/guide/advanced/data-fetching.html#fetching-after-navigation
    // $route.params.id
      axios.get('https://pokeapi.co/api/v2/pokemon/')
        .then(resul => {
          console.log('hay alguien?')
          console.log(resul)
          this.pokemons = resul.data.results
          console.log('hola')
        })
        .catch(error =>
          console.log(error))
    } },
  computed: {

    pokemonFilter () {
      var textSearch = this.textSearch
      return this.pokemons.filter(function (el) {
        return el.name.toLowerCase().indexOf(textSearch.toLowerCase()) !== -1
      })
    } }
}

</script>
