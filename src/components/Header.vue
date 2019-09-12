<template>
  <div class="spot slidedown">
    <div class="wrap">
      <h1>
        <router-link to="/" title="vuetube">
          vuetube ▶
        </router-link>
      </h1>
      <div class="space single"></div>
      <p>Video resources that will help you to improve your Vue skills</p>
      <div class="space"></div>
      <div class="space"></div>
      <p class="note">
        By Drake Aiman - Please check out the original
        <a href="http://vuetube.surge.sh/#/" target="_blank">here</a>
      </p>
      <div class="space"></div>
    </div>
  </div>
</template>

<script>
export default {

};
</script>

<style>

.slidedown {
  transform: translateY(0);
}

.spot {
  top: 0;
  left: 0;
  width: 100%;
  height: 300px;
  display: flex;
  position: absolute;
  text-align: center;
  align-items: center;
  background-color: #333;
  transition: transform .3s;
  color: #fff;
}

.spot h1 a {
  font-size: 50px;
}

.spot a {
  color: #5bc498;
  text-decoration: none;
}

.spot a:hover {
  color: #fff;
}
</style>
