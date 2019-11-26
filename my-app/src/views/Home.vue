<template>
  <div class="home">
    <div class="container">
      <div class="home__search d-flex flex-column m-auto py-3">
        <label for="search">Search</label>
        <input id="search" type="text" name="search">
      </div>
      <TopAlbum :feedAlbum="feedAlbum"/>
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
      feeds: [],
      feedAlbum: [],
    };
  },
  components: {
    TopAlbum,
  },
  created() {
    this.getFeeds();
  },
  methods: {
    async getFeeds() {
      const { data } = await axios.get('https://itunes.apple.com/us/rss/topalbums/limit=100/json');
      this.feeds = data;
      const feedArray = data.feed.entry;
      feedArray.map(feed => this.feedAlbum.push(feed));
      // feed['im:image'][2].label
    },
  },
};
</script>
<style lang="scss">
.home {
  &__search {
    max-width: 300px;
  }
}
</style>
