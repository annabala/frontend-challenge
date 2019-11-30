<template>
  <div class="info-box d-flex d-md-block align-items-end p-2">
    <div
      class="info-box__more-info h-100 w-100
      d-flex flex-column align-items-start justify-content-around text-left p-2">
      <button class="rounded-0 btn w-100 text-right btn-sm btn-link btn-close fixed-top"
      @click="$emit('close')">Close</button>
      <div class="info-box__more-info-img w-100 text-center pb-3">
        <img :src="albumInfo.cover" alt="cover">
      </div>
      <p><span class="info-box__more-info-label">Title: </span>{{ albumInfo.title }}</p>
      <p><span class="info-box__more-info-label">Artist: </span>{{ albumInfo.artist }}</p>
      <p><span class="info-box__more-info-label">Price: </span>{{ albumInfo.price }}</p>
      <p><span class="info-box__more-info-label">Genre: </span>{{ albumInfo.genre }}</p>
      <p><span class="info-box__more-info-label">Release date: </span>{{ albumInfo.date }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'InfoBox',
  props: {
    albumInfo: {
      type: Object,
    },
    showModal: {
      type: Boolean,
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

@import "../styles/setup/variables.scss";
@import "../styles/setup/mixins.scss";
@import "../styles/components/buttons.scss";
@import "../styles/components/infobox.scss";

</style>
