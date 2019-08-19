<template>
  <router-link class="pokemon-cards" tag= "article" :to="`/pokemon/${name}`">
    <div v-if='loading' class="loading">
      <i class="fas fa-spinner fa-pulse"></i>
    </div>
    <section v-else>
    <h3 class="pokemon-cards__name">
      <br>
        <!-- name que aparece es el name de las props -->
        {{ nameUp }} <br>  {{ '#' + pokemonId }}
          </h3>
        <div class="pokemon-cards__image">
      <img :src="pokemonImg" alt="image" class="img-thumbnail"/>
    </div>
    </section>
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
      pokemonId: '',
      loading: false
    }
  },
  computed: {
    nameUp () {
      return this.name.charAt(0).toUpperCase() + this.name.slice(1)
    }
  },
  async created () {
    this.loading = true
    let res = await axios.get(this.url)
    this.pokemonImg = res.data.sprites.front_default
    this.pokemonId = res.data.id
    this.loading = false
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
      font-size: 20px;
    }
    &__image {
      display: flex;
      justify-content: center;
      align-items: center;
      width: 120px;
      height: 120px;
      border-radius: 50%;
      cursor: pointer;
      background-color: rgb(190, 174, 174);
    }
    &__image:hover {
      transform: scale(1.2);
      box-shadow: 2px 2px 10px #666;
    }
}
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
