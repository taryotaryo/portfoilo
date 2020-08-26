<template>
<div v-if="$route.path === '/about'" class="section-firstview">
  <div class="section-title">
    <h1 v-on:mouseover="mouseEnter()" v-on:mouseleave="mouseLeave()">About</h1>
  </div>
  <div class="img-block"></div>
</div>
<div v-else-if="$route.path === '/work'" class="section-firstview">
  <div class="section-title">
    <h1 v-on:mouseover="mouseEnter()" v-on:mouseleave="mouseLeave()">Work</h1>
  </div>
  <div class="img-block"></div>
</div>
  <!-- <h1 class="section-title" v-else-if="$route.path === '/work'" v-on:mouseover="mouseEnter()" v-on:mouseleave="mouseLeave()">Works</h1>
  <h1 class="section-title" v-else-if="$route.path === '/post'" v-on:mouseover="mouseEnter()" v-on:mouseleave="mouseLeave()">Post</h1>
  <h1 class="section-title" v-else-if="$route.path === '/contact'" v-on:mouseover="mouseEnter()" v-on:mouseleave="mouseLeave()">Contact</h1> -->
</template>

<script>
import { bus } from '../main.js'
export default {
  methods: {
    mouseEnter: function () {
      bus.$emit('bus-event-onNav')
    },
    mouseLeave: function () {
      bus.$emit('bus-event-off')
    }
  }
}
</script>

<style lang="scss">
.section-firstview {
  display: flex;
  width: 100%;
  .section-title {
    display: inline-block;
    z-index: -2;
    width: 20%;
    height: 100vh;
    background-color: #111;
    h1 {
      position: absolute;
      top: 360px;
      left: 240px;
      font-size: 80px;
      letter-spacing: 0.4em;
      margin: 0;
      &:first-letter {
        font-size: 100px;
      }
    }

  }
  .img-block {
    z-index: -3;
    position: relative;
    background-image: url("../assets/about_image.jpg");
    width: 80%;
    height: 100vh;

    &:before {
      position: absolute;
      content: '';
      width: 100%;
      height: 100%;
      background-color: #FFDEAD;
      opacity: 0.7;
    }
  }
}
</style>
