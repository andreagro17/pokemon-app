<template>
<footer class="pokemon-footer">
    <nav class="pokemon-footer__nav">
        <!-- <ul class="nav__ul">
            <li class="nav__li">
                <a href="#/" class="router-link-active">Rojo</a>
            </li>
            <li class="nav__li">
                <a href="#/" class="router-link-active">Amarillo</a>
            </li>
            <li class="nav__li">
                <a href="#/" class="router-link-active">Azul</a>
            </li>
            <li class="nav__li">
                <a href="#/" class="router-link-active">Plata</a>
            </li>
        </ul> -->
    </nav>
    <div class="pokemon-footer__logo">
        <a> &copy; 1995-1999 GAME FREAK inc
        <!-- <img src="pokemon-app/s-l300.jpg" alt="PokeBall" class="pokemon-header__logo"> -->
        </a>
    </div>
</footer>
</template>

<script>
export default {
  name: 'Footer'
}
</script>

<style lang="scss" scoped>
.pokemon-footer {
    display: flex;
    flex-direction: column;
    justify-content:   center;
}
.nav {
    &__ul {
    display: flex;
    align-content: center;
    justify-content: center;
    }
    &__li {
    list-style: none;
    text-decoration: none;
    justify-items: center;
    align-items: center;
    padding: 5px;

    }
}
</style>
