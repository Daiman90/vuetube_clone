<template>
  <ul class="tags">
    <li @click="filterSearch(tag)" :class="{tag : isActive.includes(tag)}" v-for="(tag, index) in tags" :key=tag>{{tag}}</li>
  </ul>
</template>

<script>
export default {
  data: () => ({
    isActive: [],
    tags: [
      'vuex',
      'vue-router',
      'vuetify',
      'nuxt',
      'ssr',
      'typescript',
      'axios',
      'testing',
      'vue-material',
      'laravel',
      'tutorial',
      'talks',
      'conf',
    ],
  }),
  watch: {
    isActive() {
      return this.$emit('filter', this.isActive);
    },
  },
  methods: {
    filterSearch(tag) {
      if (this.isActive.includes(tag)) {
        const pos = this.isActive.indexOf(tag);
        this.isActive.splice(pos, 1);
      } else {
        this.isActive.push(tag);
      }
    },
  },
};
</script>

<style>
.tags {
  list-style: none;
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
}

.tags li {
  margin: 0.1em;
  color: #fff;
  padding: 5px;
  cursor: pointer;
  display: inline;
  border-radius: 3px;
  background-color: #5bc498;
  transition: background-color .3s;
}

.tags li:hover {
  background-color: #333!important;
}

.tag {
  background-color: #333!important;
}
</style>
