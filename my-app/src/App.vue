<template>
  <div id="app">
    <nav id="nav" class="d-flex flex-column justify-content-center align-items-center">
      <div class="app-logo text-left">
        <h1 class="app-logo__text">topTunes</h1>
      </div>
      <div class="nav-links d-flex py-3">
      <router-link to="/">Home</router-link>
      <router-link to="/about">Favorites</router-link>
      </div>
    </nav>
    <router-view/>
  </div>
</template>
<script>


export default {
  name: 'app',
};
</script>

<style lang="scss">
// Variables
$color-black : #000;
$color-white : #fff;
$color-primary: #16174f;
$color-primary-light: #f6f1ed;
$color-cta: #f2b632;

@import url('https://fonts.googleapis.com/css?family=Cairo:400,700,900|Roboto:400,500,700&display=swap');
#app {
  font-family: 'Roboto', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  background-color: $color-primary;
  height: 100%;
}
#nav {
  padding: 30px;
  background-color: $color-primary;

  a {
    font: 700 22px/26px Cairo;
    color: $color-white;
    margin: 0 15px;
    transition: border-bottom .2s ease;
    &:hover {
      border-bottom: 2px solid $color-cta;
      text-decoration: none;
    }
    &.router-link-exact-active {
      border-bottom: 3px solid $color-cta;
    }
  }
  .app-logo {
    position: relative;
    // &__img {
    //   width: 40px;
    // }
    &__text {
      font: 900 26px/30px Cairo;
      color: $color-cta;
    }
  }
}
</style>
