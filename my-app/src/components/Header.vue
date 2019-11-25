<template>
  <div class="header">
    <nav id="nav" class="d-flex flex-row justify-content-between align-items-center">
      <div class="app-logo text-left">
        <h1 class="app-logo__text">{{ text }}</h1>
      </div>
      <div class="app-nav__container">
        <router-link to="/">Home</router-link>
        <router-link to="/about">Favorites</router-link>
      </div>
    </nav>
    <router-view/>
  </div>
</template>

<script>
export default {
  name: 'Header',
  props: {
    text: String,
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
#nav {
  padding: 30px;

  a {
    font: 700 22px/26px Cairo;
    color: #110133;
    margin: 0 15px;
    &.router-link-exact-active {
      color: #10316b;
      border-bottom: 2px solid #e25822;
    }
  }
}
.app-logo {
  position: relative;
  &__img {
    max-width: 40px;
  }
  &__text {
    font: 900 26px/30px Cairo;
    color: #110133;
  }
}
</style>
