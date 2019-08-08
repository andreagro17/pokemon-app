<template>
<pagination
    v-bind:prevPage="api.prevPage"
    v-bind:nextPage="api.nextPage"
    v-on:prev-page="prevPage"
    v-on:next-page="nextPage"
/>
</template>

<script>
export default {
  name: 'Search2',
  data () {
    return {
      pokemons: [],
      pokemonSearch: ''

    }
  },
  methods: {

  }
}
</script>
