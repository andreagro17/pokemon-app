<template>
<header class="pokemon-header">
    <div class="pokemon-header__logo">
        <a href='#/' class="router-link-active">
        <img src="@/assets/pokemon-svgrepo-com.svg" alt="PokeBall" href="#/" class="router-link-active">
        Hazte con todos! | Pokemon
        </a>
    </div>
    <nav class="pokemon-header__nav">
        <ul class="nav__ul">
                <router-link to="#/" tag="li" active-class="active" exact><a>Pueblo Paleta</a></router-link>
                <li><a> | </a></li>
                <router-link to="Search" tag="li" active-class="active"><a>Pokedex</a></router-link>
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
         img{
             margin-right: 8px;
             vertical-align: middle;
             width: 80px;
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
        }
        a {
        text-decoration: none;
        // font-display: swap;
        }
    }
 }
</style>
