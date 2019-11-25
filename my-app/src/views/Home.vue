<template>
  <div class="home">
    <div class="container">
      <div class="home__search d-flex flex-column m-auto py-3">
        <label for="search">Search</label>
        <input id="search" type="text" name="search">
      </div>
      <TopAlbum/>
      <div class="home__album-container d-flex flex-row flex-wrap justify-content-between">
        <div class="home__album-item"></div>
        <div class="home__album-item"></div>
        <div class="home__album-item"></div>
        <div class="home__album-item"></div>
        <div class="home__album-item"></div>
        <div class="home__album-item"></div>
        <div class="home__album-item"></div>
        <div class="home__album-item"></div>
        <div class="home__album-item"></div>
        <div class="home__album-item"></div>
      </div>
    </div>
    <div>Icons made by <a href="https://www.flaticon.com/authors/freepik" title="Freepik">Freepik</a> from <a href="https://www.flaticon.com/" title="Flaticon">www.flaticon.com</a></div>
  </div>
</template>

<script>
// @ is an alias to /src
import axios from 'axios';
import TopAlbum from '@/components/TopAlbum.vue';

// const API = 'https://itunes.apple.com/us/rss/topalbums/limit=100/json';

export default {
  name: 'home',
  data() {
    return {
      // search
    };
  },
  components: {
    TopAlbum,
  },
  mounted() {
    axios.get('https://itunes.apple.com/us/rss/topalbums/limit=100/json')
      .then((response) => {
        console.log(response);
      })
      .catch((error) => {
        console.log(error);
      });
  },
};
</script>
<style lang="scss">
$color-primary: #16174f;
$color-cta: #f2b632;
.home {
  &__search {
    max-width: 300px;
  }
  &__album-container {
    max-width: 700px;
    margin: 0 auto;
  }
  &__album-item {
    background-color: $color-cta;
    width: 180px;
    height: 180px;
    box-shadow: 2px 2px 12px rgba(0,0,0,.2);
    margin: 15px 20px;
  }
}
</style>
