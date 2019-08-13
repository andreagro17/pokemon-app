<template>
  <section class="pokemon-list">
    <ul class="pokemon-list__ul">
      <pokemon-cards
        v-for="pepe in pokemonsList"
          :key = "pepe.name"
          :name = "pepe.name"
          :url = "pepe.url"/>
        </ul>
      <div class=""></div>
    <h5> Prueba prev </h5>
      <button @click="fullPokemons('prev')" class="prueba_prev"> Prev </button>
        <button v-on:click="fullPokemons(nextPage)">Buscar</button>
          <button @click="fullPokemons('next')" class="prueba_prev">Next</button>
          <br>
        {{ currentPage}}
      <br>
    {{ pageNumber }}
  </section>
</template>

<script>
import axios from 'axios'
import PokemonCards from '@/components/Hero/PokemonCards'

export default {
  // Mi componente
  name: 'PokemonList',
  // MiComponenteHijo
  components: {
    PokemonCards
  },
  // Mi variable: valor;
  // Esto es lo que aparece en la pantalla.
  data () {
    return {
      pokemonsList: [],
      nextPage: '',
      prevPage: '',
      maxResults: 20,
      currentPage: 1,
      pageNumber: 0
    }
  },
  // methods: {
  //   // async fullPokemons (a) {
  //   //   try {
  //   //     if (a === 'prev') {
  //   //       let res = await axios.get(this.prevPage)
  //   //     } else {
  //   //       let res = await axios.get(this.nextPage)
  //   //     }

  //   //     this.pokemonsList = res.data.results
  //   //     this.pageNumber = Math.ceil(res.data.count / 20)
  //   //     console.log(res.data)
  //   //   } catch (e) {
  //   //     throw new Error('error')
  //   //   }
  //   }
  // nextPage() {
  //   let res = await axios.get(this.nextPage)
  // },
  // previousPage() {
  //   this.$emit('previousPage')
  // },
  //  onClick() {
  //   this.$emit("loadPage", this.pageNumber)
  // }

  // computed: {
  //   isPreviousButtonDisabled() {
  //     return this.currentPage === 1
  //   },
  //   isNextButtonDisabled() {
  //     return this.currentPage === this.pageCount
  //   }
  // },
  async created () {
    try {
      let res = await axios.get('https://pokeapi.co/api/v2/pokemon/')
      this.pokemonsList = res.data.results
      this.nextPage = res.data.next
    } catch (error) {
      console.error('Error servicio')
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
