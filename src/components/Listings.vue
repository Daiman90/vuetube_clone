<template>
  <div class="listing">
    <article :class="{loading : loading }" v-for="video in videos" :key="video.id.videoId" class="video">
      <router-link :to="video.id.videoId" :title="video.snippet.title" >
        <div class="thumb" :style="video.snippet.thumbnails.medium.url"></div>
      </router-link>
      <div class="space"></div>
      <div class="meta">
        <div class="title">
          <router-link :to="video.id.videoId">
            <b>{{video.snippet.title}}</b>
          </router-link>
        </div>
        <div class="space single"></div>
        <span class="time">{{video.snippet.publishedAt}}</span>
      </div>
    </article>
  </div>
</template>

<script>

export default {
  data: () => ({
    videos: [],
    loading: true,
    filter: '',
  }),
  props: {
    filtered: Array,
  },
  mounted() {
    this.getVideos();
  },
  watch: {
    filtered() {
      this.filter = this.filtered.reduce((string, tag) => `${string}+${tag}`, '');
      this.getVideos();
    },
  },
  methods: {
    async getVideos() {
      this.loading = true;
      this.$emit('loading', this.loading);
      const response = await fetch(`https://www.googleapis.com/youtube/v3/search?&part=snippet&type=video&q=vuejs${this.filter}&maxResults=50&key=AIzaSyBlSc4Zavlls-c_K2cESn1jyuiUSckHgwM`);
      const results = await response.json();
      this.videos = await results.items;
      await this.changeImage();
      this.loading = false;
    },
    changeImage() {
      this.videos.forEach((video) => {
        video.snippet.thumbnails.medium.url = `background-image: url(${video.snippet.thumbnails.medium.url})`;
      });
    },
  },
};
</script>

<style>
.listing {
  width: 100%;
  display: flex;
  flex-wrap: wrap;
  min-height: 100%;
  justify-content: space-between;
}

.video {
  width: 32%;
  position: relative;
  margin-bottom: 35px;
  padding-bottom: 10px;
}

.video .thumb {
  width: 100%;
  height: 140px;
  border-radius: 3px;
  background-size: cover;
}

.video:before {
  width: 0;
  bottom: 0;
  height: 4px;
  content: "";
  position: absolute;
  transition: width .5s;
  background-color: #5bc498;
}

.video:before {
  left: 0;
}

.video:hover:before {
  width: 50%;
}

.video:after {
  width: 0;
  bottom: 0;
  height: 4px;
  content: "";
  position: absolute;
  transition: width .5s;
  background-color: #5bc498;
}

.video:after {
  right: 0;
}

.video:hover:after {
  width: 50%;
}

@media screen and (max-width: 750px) {
  .video {
    width: 100%;
  }
}

.meta {
  color: #666;
}

.title {
  font-size: 14px;
}

a {
  color: #333;
  text-decoration: none;
}

span {
  font-size: 12px;
}
</style>
