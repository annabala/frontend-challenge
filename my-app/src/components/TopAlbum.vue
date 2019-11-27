<template>
  <div class="top-album">
    <ul class="top-album__album-container d-flex flex-wrap justify-content-between">
      <li class="top-album__album-item d-flex align-items-center justify-content-center"
        v-for="feed in feedAlbum" :key="feed.label">
        <img v-bind:src="feed['im:image'][2].label">
        <p class="d-none">{{ feed['im:name'].label }}</p>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'TopAlbum',
  props: ['feedAlbum'],
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
@import "../styles/setup/variables.scss";
@import "../styles/components/topalbum.scss";
</style>
