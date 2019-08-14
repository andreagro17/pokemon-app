<template>
  <header class="pokemon-header">
    <div class="pokemon-header__logo">
      <a href='#/' class="router-link-active">
        <router-link to="/" active-class="active">
          <img src="@/assets/pokemon-svgrepo-com.svg" alt="PokeBall" class="router-link-active">
          Hazte con todos! | Pokemon
        </router-link>
      </a>
    </div>
  <nav class="pokemon-header__nav">
    <ul class="nav__ul">
      <router-link to="/" tag="li" active-class="active" exact>Pueblo Paleta</router-link>
        <li><a> | </a></li>
          <router-link to="/search" tag="li" active-class="active">Pokedex</router-link>
        </ul>
    </nav>
  </header>
</template>

<script>
export default {
  name: 'Header'
}
</script>

<style lang="scss" scoped>
.pokemon-header {
  display: flex;
  justify-content: space-between;
  align-content: center;
  padding: 10px;
  &__logo {
    justify-items: flex-start;
    align-content: center;
    img {
      margin-right: 8px;
      vertical-align: middle;
      width: 80px;
      border-radius: 50%;
      transition: transform .8s ease-in-out;
    }
    img:hover{
    transform: rotate(360deg);
}
  }
  &__nav {
    align-content: center;
  }
}

.nav {
  &__ul {
  display: flex;
  align-content: center;
  padding: 0 5px;
  list-style: none;
  li{
    padding: 8px;
    text-decoration: none;
    cursor: pointer;
  }
  }
  a {
    text-decoration: none;
    cursor: default;
  }
}

</style>
