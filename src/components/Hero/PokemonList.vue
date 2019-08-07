<template>
  <section class="pokemon-list">
    <ul class="pokemon-list__ul">
    <!-- Preguntar a qué hace referencia lo siguiente y por qué se pone dentro del componente creado -->
    <pokemon-cards
          v-for="pepe in pokemonsList"
          :key = "pepe.name"
          :name = "pepe.name"
          :url = "pepe.url"/>
    </ul>
    <div class=""></div>
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
      pokemonsList: []
    }
  },

  async created () {
    try {
      let res = await axios.get('https://pokeapi.co/api/v2/pokemon/')
      this.pokemonsList = res.data.results
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
