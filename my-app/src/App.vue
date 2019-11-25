<template>
  <div id="app">
    <div class="container">
      <Header title="topTunes"/>
    </div>
  </div>
</template>
<script>

import Header from '@/components/Header.vue';

export default {
  name: 'app',
  components: {
    Header,
  },
};
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css?family=Cairo:400,700,900|Roboto:400,500,700&display=swap');
#app {
  font-family: 'Roboto', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
