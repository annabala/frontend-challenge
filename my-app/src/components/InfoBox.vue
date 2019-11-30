<template>
  <div class="info-box p-2">
    <div
      class="info-box__more-info h-100
      d-flex flex-column align-items-start justify-content-around text-left p-2">
      <button class="rounded-0 btn w-100 text-right btn-sm btn-link btn-close fixed-top"
      @click="$emit('close')">Close</button>
      <div class="info-box__more-info-img w-100 text-center">
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
@import "../styles/components/buttons.scss";

.info-box {
  position: fixed;
  top: 50%;
  right: 50%;
  transform: translate(50%, -50%);
  color: $color-black;
  font: 700 1rem/1.2rem $font-special;
  width: 500px;
  height: 500px;
  background-color: $color-white;
  border: 15px solid $color-vibrant;
  z-index: 20;
  & img {
    box-shadow: 2px 0px 10px rgba(0,0,0, 0.3);
  }
  &__more-info-label {
    font: 500 1rem/1rem $font-body;
    color: $color-primary;
    margin: 0 5px 0 0;
  }
}
</style>
