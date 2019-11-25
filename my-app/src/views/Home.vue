<template>
  <div class="home">
    <TopAlbum msg="Top 100 iTunes albums"/>
    <div>Icons made by <a href="https://www.flaticon.com/authors/freepik" title="Freepik">Freepik</a> from <a href="https://www.flaticon.com/" title="Flaticon">www.flaticon.com</a></div>
  </div>
</template>

<script>
// @ is an alias to /src
import TopAlbum from '@/components/TopAlbum.vue';


export default {
  name: 'home',
  components: {
    TopAlbum,
  },
};
</script>
