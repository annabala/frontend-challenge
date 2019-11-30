<template>
  <div class="home" :class="{'home--shadow': showModal == true}">
    <div class="container">
      <div class="home__search d-flex flex-column mx-auto mt-4 mb-5">
        <label for="search" class="m-0  text-left">Search by album title:</label>
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
        <div class="spinner" v-if="spinner">Waiting</div>
        <li class="top-album__album-item d-flex flex-column align-items-center
          justify-content-baseline"
          v-for="(feed, index) in searchList" :key="feed.label"
          >
          <div class="top-album__album-item-img">
            <img :src="feed['im:image'][2].label"/>
          </div>
          <p class="top-album__album-item-name--sm">{{ feed['im:artist'].label }}</p>
          <div class="top-album__album-item-title-box">
            <p class="top-album__album-item-name">{{ feed['im:name'].label }}</p>
            <button
              type="button"
              class="rounded-0 btn btn-sm btn-link btn-more"
              @click="getItem(index), showModal = true"
            >
              More
              <img src="../assets/arrow-right.svg" alt="arrow">
            </button>
          </div>
        </li>
      </ul>
      <InfoBox
        :albumInfo="albumInfo"
        :show="showModal"
        v-if="showModal"
        @close="showModal = false"
      />
    </div>
    <div class="home__icons-info">Icons made by <a href="https://www.flaticon.com/authors/freepik" title="Freepik">Freepik</a> from <a href="https://www.flaticon.com/" title="Flaticon">www.flaticon.com</a></div>
  </div>
</template>

<script>
// @ is an alias to /src
import axios from 'axios';
import InfoBox from '@/components/InfoBox.vue';

export default {
  name: 'home',
  data() {
    return {
      feeds: [],
      feedAlbum: [],
      searchValue: '',
      albumInfo: Object,
      showModal: false,
      spinner: false,
    };
  },
  components: {
    InfoBox,
  },
  created() {
    this.getFeeds();
  },
  methods: {
    async getFeeds() {
      this.spinner = true;
      let array = [];
      const { data } = await axios.get('https://itunes.apple.com/us/rss/topalbums/limit=100/json');
      this.spinner = false;
      this.feeds = data;
      array = data.feed.entry;
      array.map(feed => this.feedAlbum.push(feed));
    },
    getItem(i) {
      const titlename = this.feedAlbum[i]['im:name'].label;
      const artistname = this.feedAlbum[i]['im:artist'].label;
      const pricename = this.feedAlbum[i]['im:price'].label;
      const genrename = this.feedAlbum[i].category.attributes.label;
      const coverimg = this.feedAlbum[i]['im:image'][2].label;
      const releasedate = this.feedAlbum[i]['im:releaseDate'].attributes.label;
      this.albumInfo = {
        title: titlename,
        artist: artistname,
        price: pricename,
        genre: genrename,
        cover: coverimg,
        date: releasedate,
      };
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
@import "../styles/basics/utilities.scss";
@import "../styles/views/home.scss";
@import "../styles/components/topalbum.scss";
@import "../styles/components/buttons.scss";

</style>
