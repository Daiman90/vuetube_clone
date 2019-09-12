<template>
<div class="root">
  <div class="space"></div>
  <div class="space"></div>
  <div class="player">
    <iframe width="480" height="100%" :src="url" frameborder="0" allow="accelerometer, autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
  </div>
</div>
</template>

<script>
export default {
  computed: {
    url() {
      return `https://www.youtube.com/embed/${this.$route.params.id}`;
    },
  },
};
</script>

<style>
.player {
  height: 500px;
}

  iframe {
    width: 100%;
    height: 60%;
  }
</style>
