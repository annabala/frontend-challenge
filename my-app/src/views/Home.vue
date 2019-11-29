<template>
  <div class="home">
    <div class="container">
      <div class="home__search d-flex flex-column mx-auto my-5">
        <label for="search">Search for albums(by album title):</label>
        <input
          id="search"
          type="text"
          name="search"
          class="mt-2 form-control rounded-0"
          placeholder="Search"
          v-model="searchValue"
        />
      </div>
      <ul class="top-album__album-container d-flex flex-wrap justify-content-center pl-0">
        <li class="top-album__album-item d-flex flex-column align-items-center
          justify-content-baseline"
          v-for="feed in searchList" :key="feed.label">
          <div class="top-album__album-item-img">
            <img v-bind:src="feed['im:image'][2].label"/>
          </div>
          <p class="top-album__album-item-name--author">{{ feed['im:artist'].label }}</p>
          <p class="top-album__album-item-name">{{ feed['im:name'].label }}</p>
        </li>
      </ul>
    </div>
    <div>Icons made by <a href="https://www.flaticon.com/authors/freepik" title="Freepik">Freepik</a> from <a href="https://www.flaticon.com/" title="Flaticon">www.flaticon.com</a></div>
  </div>
</template>

<script>
// @ is an alias to /src
import axios from 'axios';

// const API = 'https://itunes.apple.com/us/rss/topalbums/limit=100/json';

export default {
  name: 'home',
  data() {
    return {
      feeds: [],
      feedAlbum: [],
      searchValue: '',
    };
  },
  // components: {
  //   TopAlbum,
  // },
  created() {
    this.getFeeds();
  },
  methods: {
    async getFeeds() {
      let array = [];
      const { data } = await axios.get('https://itunes.apple.com/us/rss/topalbums/limit=100/json');
      this.feeds = data;
      array = data.feed.entry;
      array.map(feed => this.feedAlbum.push(feed));
    },
  },
  computed: {
    searchList() {
      return this.feedAlbum.filter(feed => feed['im:name'].label.toLowerCase().match(this.searchValue.toLowerCase()));
    },
  },
};
</script>
<style lang="scss" scoped>
@import "../styles/setup/variables.scss";
@import "../styles/setup/mixins.scss";
@import "../styles/setup/animations.scss";
@import "../styles/views/home.scss";
@import "../styles/components/topalbum.scss";
</style>
