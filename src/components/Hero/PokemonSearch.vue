<template>
    <div class="searchBar">
      <form @submit.prevent="setPokemonUrl">
        <input type="text" v-model="searchValue">
      </form>
      <i class="fas fa-search" @click="setPokemonUrl"></i>

      </div>
</template>

<script>
export default {
  name: 'PokemonSearch',

  props: [
    'apiUrl'
  ],
  data: () => {
    return {
      searchValue: ''
    }
  },
  methods: {
    setPokemonUrl (url) {
      if (this.searchValue !== '') { this.$emit('setPokemonUrl', this.apiUrl, this.searchValue) }
    }
  }
}
</script>

<style lang="scss" scoped>
  .searchBar {
    position: relative;
    width: 100%;
    max-width: 510px;
    padding-bottom: 20px;

    input {
      border: forestgreen;
      outline: black;
      }
    i {
      color: greenyellow;
    }
  }

</style>
