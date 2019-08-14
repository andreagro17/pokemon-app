<template>
  <router-link class="pokemon-cards" tag= "article" :to="`/pokemon/${name}`">
    <div id='root' v-cloak>
  </div>
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
[v-cloak] > * { display: none; }
[v-cloak]::before {
  content: '';
  position: absolute;
  left: 50%;
  top: 50%;
  z-index: 1;
  width: 150px;
  height: 150px;
  margin: -75px 0 0 -75px;
  border: 16px solid #f3f3f3;
  border-radius: 50%;
  border-top: 16px solid #3498db;
  width: 120px;
  height: 120px;
  -webkit-animation: spin 2s linear infinite;
  animation: spin 2s linear infinite;
}
@-webkit-keyframes spin {
  0% { -webkit-transform: rotate(0deg); }
  100% { -webkit-transform: rotate(360deg); }
}

@keyframes spin {
  0% { transform: rotate(0deg); }
  100% { transform: rotate(360deg); }
}

</style>
