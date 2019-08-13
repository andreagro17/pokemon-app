<template>
  <section>
    <div>
      <div class="prueba">
        <input type="textSearch" class="prueba__form-control" v-model="textSearch" placeholder="Searching...">
          <p> Text searched is: {{textSearch}} </p>
           <button v-on:click="getOnePoke"> Detalles </button>
            <div class="prueba__pokemon-filtered">
             <li v-for="pok2 of pokemonFilter" :key="pok2.name">
            <span v-on:click="getFullPoke"> {{ pok2.name }} </span>
          </li>
        </div>
      </div>
      <!-- <router-link class="pokemonhgj" tag= "div" :to="`/pokemon/${this.textSearch}`"> -->
            <!-- v-for="pok2 in textSearch"
            :key="pok2.name"/> -->
    <pokemon-detail
      :pokemons="pokemons"
    />
  <!-- </router-link> -->
    </div>
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
      pokemons: [],
      textSearch: ''
    }
  },
  mounted () {
    this.getFullPoke()
  },
  methods: {
    async getFullPoke () {
      try {
        let resul = await axios.get('https://pokeapi.co/api/v2/pokemon/?limit=964')
        this.pokemons = resul.data.results
      } catch (e) {
        throw new Error('Prueba con otro Pokemo getFull')
      }
    },
    async getOnePoke (textSearch) {
      try {
        let res = await axios.get(`https://pokeapi.co/api/v2/pokemon/${this.textSearch}`)
        console.log(res)
        this.textSearch = res.data
      } catch (e) {
        throw new Error('Search again')
      }
    },
    showDetail: function (a) {
      console.log(this.textSearch)
    }
  },
  computed: {
    pokemonFilter () {
      // buscado en internet: por qué ocurre esto: con el this.textSearch no funciona
      var textSearch = this.textSearch
      return this.pokemons.filter(function (item) {
        return item.name.indexOf(textSearch) !== -1
      })
    }
  }
}

</script>

<style lang="scss" scoped>
.prueba {
  &__pokemon-filtered {
    max-height: 150px;
    overflow-y: scroll;
    list-style: none;
    text-transform: capitalize;
  }
}
</style>
