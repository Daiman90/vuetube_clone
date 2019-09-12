<template>
  <div class="home">
    <div class="space"></div>
    <div class="space"></div>
    <tags @filter="getFiltered"/>
    <div class="space"></div>
    <div class="space"></div>
    <Listings :filtered="filtered" @loading="setLoading" />
    <Loading :class="{ display : loading }" />
  </div>
</template>

<script>
import Tags from '@/components/Tags.vue';
import Loading from '@/components/Loading.vue';
import Listings from '@/components/Listings.vue';

export default {
  name: 'home',
  data: () => ({
    loading: false,
    filtered: [],
  }),
  components: {
    Tags,
    Listings,
    Loading,
  },
  methods: {
    setLoading(loading) {
      this.loading = loading;
    },
    getFiltered(filtered) {
      this.filtered = filtered;
    },
  },
};
</script>

<style>
.display {
  display: '';
}
</style>
