<template>
<div>
    <pokemon-detail/>
    <!-- v-for="pokemon in detailD"
          :key = "pokemon.name"
          :name = "pokemon.name"
          :url = "pokemon.url"/> -->
</div>
</template>

<script>
import axios from 'axios'
import PokemonDetail from '@/components/Hero/PokemonDetail'

export default {
  name: 'Detail',
  components: {
    PokemonDetail
  },
  data () {
    return {
      detailD: ''
    }
  },
  // Cómo se saca la imagen y el id
  async created () {
    try {
      let res = await axios.get('https://pokeapi.co/api/v2/pokemon/')
      this.detailD = res.data.results
    } catch (e) {
      throw new Error('Buscando el pokemon...')
    }
  }
}
</script>
