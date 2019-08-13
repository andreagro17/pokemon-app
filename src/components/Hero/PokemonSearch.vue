<template>
    <ul>
      <li
        class="pokemon_filter"
        v-for="pok of pokemonFilter"
        :key="pok.name">
          <span v-on:click="getFullPoke">
            {{ pok.name }}
          </span>
       </li>
    </ul>
</template>

<script>
// export default {
//   name: 'PokemonSearch',

//   props: {
//     pokemons: {
//       type: Array,
//       default: ''
//     },
//     name: {
//       type: String
//     }
//   }
// computed: {
//   pokemonFilter () {
//   // buscado en internet: por qué ocurre esto: con el this.textSearch no funciona
//     return this.pokemons.filter(function (poke) {
//       return poke.name.include(this.name)
//     })
//   }
// },
// created: {
//   async getFullPoke () {
//     try {
//       let resul = await axios.get('https://pokeapi.co/api/v2/pokemon/?limit=964')
//       this.pokemons = resul.data.results
//     } catch (e) {
//       throw new Error('Prueba con otro Pokemo getFull')
//     }
//   }
// }

</script>

<style lang="scss" scoped>

</style>
