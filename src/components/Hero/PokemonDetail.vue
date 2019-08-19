<template>
  <section class="pokemon__all">
    <h1 class="pokemon__title">
      #{{ detail.id }}  {{ detail.name }}</h1>
        <section class="pokemon__sprites">
          <p v-for="imagen in detail.sprites" :key="imagen" >
            <img v-if='imagen' :src="imagen" alt="pokemon image"/>
          </p>
        </section>
      <section class="pokemon__info-boxes">
        <article class="pokemon__info-box">
          <div
            class="info-box__title">
              <h2>Abilities</h2>
            </div>
          <div class="info-box__content">
            <p
              v-for="ability in detail.abilities"
                :key="ability.ability.name">
                  {{ ability.ability.name }}
              </p>
            </div>
          </article>
        <article class="pokemon__info-box">
          <div class="info-box__title">
            <h2>Base Experience</h2>
            </div>
          <div class="info-box__content">
            <p>
              {{ detail.base_experience }}
            </p>
          </div>
        </article>
        <article class="pokemon__info-box">
          <div class="info-box__title">
            <h2>Height & Weight</h2>
          </div>
          <div class="info-box__content">
            <p>
              height: {{ detail.height }}
                <br>
              weight: {{ detail.weight }}
            </p>
          </div>
        </article>
        <article class="pokemon__info-box">
          <div class="info-box__title">
            <h2>Types</h2>
          </div>
          <div class="info-box__content">
            <p
              v-for="tipo in detail.types" v-bind:key="tipo.type.name">
                {{ tipo.type.name }}
            </p>
          </div>
        </article>
        <article class="pokemon__info-box">
          <div class="info-box__title">
            <h2>Stats</h2>
          </div>
          <div class="info-box__content">
            <p
              v-for="estado in detail.stats" v-bind:key="estado.stat.name">
                {{ estado.stat.name }} : {{ estado.base_stat }}
            </p>
          </div>
        </article>
        <article class="pokemon__info-box">
          <div class="info-box__title">
            <h2>Moves</h2>
          </div>
          <div class="info-box__content">
            <p
              v-for="move in detail.moves" v-bind:key="move.move.name">
                {{ move.move.name }}
              </p>
          </div>
        </article>
        <article class="pokemon__info-box">
          <div class="info-box__title">
            <h2>Item</h2>
          </div>
          <div class="info-box__content">
            <p
              v-for="item in detail.held_items" v-bind:key="item.held_items">
                {{ item.held_items }}
            </p>
          </div>
        </article>
        <article class="pokemon__info-box">
          <div class="info-box__title">
            <h2>Order</h2>
          </div>
          <div class="info-box__content">
            <p>
              {{ detail.order }}
            </p>
          </div>
          <div class="info-box__title">
            <h2>Default</h2>
          </div>
          <div class="info-box__content">
            <p>
              {{ detail.is_default }}
            </p>
          </div>
        </article>
      </section>
    </section>
</template>

<script>
import axios from 'axios'
export default {
  name: 'PokemonDetail',
  props: {
    name: {
      type: String,
      default: ''
    }
  },
  data () {
    return {
      detail: {}
    }
  },
  async created () {
    let namePokemon = this.$route.params.name
    if (namePokemon !== undefined) {
      try {
        let resu = await axios.get(`https://pokeapi.co/api/v2/pokemon/${namePokemon}`)
        console.log(resu)
        this.detail = resu.data
      } catch (e) {
        throw new Error('Prueba con otro Pokemon')
      }
    }
  },
  watch: {
    name: function (newVal, oldVal) { // watch it
      console.log(newVal, oldVal)
      if (newVal !== undefined) {
        let namePokemon = newVal
        axios.get(`https://pokeapi.co/api/v2/pokemon/${namePokemon}`)
          .then((resu) => {
            console.log(resu)
            this.detail = resu.data
          })
      }
    }
  }
}

</script>

<style lang="scss" scoped>
.pokemon {
  &__all {
    width: 960px;
    padding-top: 60px;
    margin: auto;
  }
  &__title {
    font-size: 48px;
    font-weight: 500;
    text-transform: capitalize;
    border-bottom: 1px solid #e1e1e1;
    padding-bottom: 48px;
    margin-bottom: 24px;
  }
  &__sprites {
    display: flex;
    justify-content: space-evenly;
  }
  &__info-boxes {
    display: flex;
    flex-wrap: wrap;
    align-content: center;
  }
  &__info-box {
    border: 1px #bababa;
    text-align: center;
    width: 25%;
  }
}
.info-box {
  &__tite {
    margin-bottom: 12px;
    border-bottom: 1px #e1e1e1;
    padding-bottom: 8 px;
  }
  &__content {
    max-height: 150px;
    overflow-y: scroll;
  }
}

</style>
