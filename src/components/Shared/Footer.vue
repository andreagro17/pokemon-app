<template>
  <footer class="pokemon-footer">
    <nav class="pokemon-footer__nav"/>
      <div class="pokemon-footer__logo">
        <a> &copy; 1995-1999 GAME FREAK inc</a>
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
