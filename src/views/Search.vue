<template>
    <div>
        <h1 class='buscar'> Search  </h1>
        <button v-on:click="fetchPoke">Buscar</button>

        <div v-for="pok of pokemon" v-bind:key="pok.name">
            {{ pok.name }} + 'hola'
        </div>
    </div>

</template>
<script>
import axios from 'axios'

export default {
  name: 'Search',
  data () {
    return {
      pokemon: {}
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
          this.pokemon = resul.data.results
          console.log('hola')
        })
        .catch(error =>
          console.log(error))
    } }
}
</script>
