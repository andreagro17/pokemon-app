<template>
  <router-link class="pokemon-cards" tag= "article" :to="`/pokemon/${name}`">
    <h3 class="pokemon-cards__name">
      <br>
        <!-- name que aparece es el name de las props -->
        {{ nameUp }} <br>  {{ '#' + pokemonId }}
          </h3>
        <div class="pokemon-cards__image">
      <img :src="pokemonImg" alt="image" class="img-thumbnail"/>
    </div>
  </router-link>
</template>

<script>
import axios from 'axios'
export default {
  name: 'PokemonCards',
  props: {
    name: {
      type: String,
      default: ''
    },
    url: {
      type: String
    }
  },
  data () {
    return {
      pokemonImg: null,
      pokemonId: ''
    }
  },
  computed: {
    nameUp () {
      return this.name.charAt(0).toUpperCase() + this.name.slice(1)
    }
  },
  async created () {
    let res = await axios.get(this.url)
    this.pokemonImg = res.data.sprites.front_default
    this.pokemonId = res.data.id
    console.log(res)
  }
}
</script>

<style lang="scss" scoped>
.pokemon-cards {
  width: 25%;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
    &__name {
      font-size: 15px;
    }
    &__image {
      margin-bottom: 16px;
      border-radius: 100%;
      border: 1px dotted;
    }
}

</style>
