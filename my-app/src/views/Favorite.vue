<template>
  <div class="favorite">
    <h1>Your favorite albums</h1>
    <InfoBox/>
  </div>
</template>

<script>
// @ is an alias to /src

import InfoBox from '@/components/InfoBox.vue';

export default {
  name: 'home',
  components: {
    InfoBox,
  },
};
</script>
<style lang="scss" scoped>
@import "../styles/setup/variables.scss";
@import "../styles/setup/mixins.scss";
@import "../styles/setup/animations.scss";
@import "../styles/views/home.scss";
@import "../styles/components/topalbum.scss";
@import "../styles/components/buttons.scss";

</style>
