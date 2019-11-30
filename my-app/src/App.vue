<template>
  <div id="app">
    <nav id="nav" class="d-flex flex-column justify-content-center align-items-center">
      <div class="app-logo text-left d-flex flex-column-reverse">
        <h1 class="app-logo__text">topTunes</h1>
        <img class="app-logo__img img-fluid" src="./assets/headphones.svg" alt="top tunes logo">
      </div>
      <div class="nav-links d-flex py-3">
      <router-link to="/">Home</router-link>
      <router-link to="/favorite">Favorites</router-link>
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
@import url('https://fonts.googleapis.com/css?family=Cairo:400,700,900|Roboto:400,500,700&display=swap');
@import "./styles/setup/variables.scss";
@import "./styles/setup/mixins.scss";
@import "./styles/setup/animations.scss";
@import "./styles/basics/app.scss";
@import "./styles/basics/layout.scss";

</style>
