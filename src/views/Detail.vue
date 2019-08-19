<template>
<div>
    <pokemon-detail v-if='detailD'/>
    <div v-else class="loading">
      <i class="fas fa-cog fa-spin"></i>
    </div>
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
      detailD: '',
      loading: false
    }
  },
  // Cómo se saca la imagen y el id
  async created () {
    try {
      this.loading = true
      let res = await axios.get('https://pokeapi.co/api/v2/pokemon/')
      this.detailD = res.data.results
      this.loading = false
    } catch (e) {
      throw new Error('Buscando el pokemon...')
    }
  }
}
</script>
<style>
.loading {
  position: relative;
  width: 20px;
  height: 20px;
  margin:50px auto;
  -webkit-animation: fa-spin 2s infinite linear;
  animation: fa-spin 2s infinite linear;
}

.loading:before {
  content: "\f110";
  font-family: FontAwesome;
  font-size:20px;
  position: absolute;
  top: 0;
}
</style>
