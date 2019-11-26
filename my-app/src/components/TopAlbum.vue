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
$color-primary: #161B40;
$color-cta: #f2b632;
.top-album {
  &__album-container {
    max-width: 1100px;
    margin: 0 auto;
  }
  &__album-item {
    background-color: $color-cta;
    width: 185px;
    height: 185px;
    box-shadow: 2px 2px 12px rgba(0,0,0,.3);
    margin: 15px 20px;
    z-index: 10;
    &::after{
      content: url('../assets/cd.svg');
      width: 140px;
      position: absolute;
      transition: .4s linear;
      transform-origin: center;
      z-index: -1;
    }
    &:hover::after {
      margin-left: 60px;
      transform: rotate(40deg);
    }
  }
}
</style>
