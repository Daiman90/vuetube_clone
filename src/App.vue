<template>
  <div id="app">
    <Header />
    <router-view class="view wrap root" />
  </div>
</template>

<script>
import Header from '@/components/Header.vue';

export default {
  components: {
    Header,
  },

};
</script>

<style>
* {
  margin: 0;
  padding: 0;
}
.space {
  width: 100%;
  height: 20px;
}

.single {
  height: 10px;
}

.view {
  margin-top:300px;
}

.wrap {
  width:70%;
  margin-bottom: 0;
  margin-right: auto;
  margin-left: auto;
}
</style>
