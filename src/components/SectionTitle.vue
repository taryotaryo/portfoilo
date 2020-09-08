<template>
<div class="title-withFirstview" v-if="$route.path === '/about'">
  <div class="leftSpace">
    <h1 class="title" v-on:mouseover="mouseEnter()" v-on:mouseleave="mouseLeave()">About</h1>
  </div>
  <div class="background background-profile"></div>
</div>
<div class="title-withFirstview" v-else-if="$route.path === '/work'">
  <div class="leftSpace">
    <h1 class="title" v-on:mouseover="mouseEnter()" v-on:mouseleave="mouseLeave()">Work</h1>
  </div>
  <div class="background background-work"></div>
</div>
<h1 class="title-simple" v-else-if="$route.path === '/post'" v-on:mouseover="mouseEnter()" v-on:mouseleave="mouseLeave()">Post</h1>
<h1 class="title-simple" v-else-if="$route.path === '/contact'" v-on:mouseover="mouseEnter()" v-on:mouseleave="mouseLeave()">Contact</h1>
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

<style scoped lang="scss">
.title-withFirstview {
  display: flex;
  width: 100%;
  .leftSpace {
    display: inline-block;
    height: 100vh;
    width: 20%;
    background-color: #111;
    z-index: -2;
      @media screen and (max-width: 1024px) {
        width: 0%;
      }
    .title {
      position: absolute;
      top: 360px;
      left: 240px;
      font-size: 80px;
      letter-spacing: 0.4em;
      margin: 0;
      @media screen and (max-width: 1024px) {
        left: 50%;
        transform: translateX(-50%);
        font-size: 50px;
      }
      &:first-letter {
        font-size: 100px;
        @media screen and (max-width: 1024px) {
          font-size: 70px;
        }
      }
    }

  }
  .background {
    position: relative;
    height: 100vh;
    width: 80%;
    z-index: -3;
    @media screen and (max-width: 1024px) {
      width: 100%;
    }
    &:before {
      content: '';
      position: absolute;
      height: 100%;
      width: 100%;
      background-color: #FFDEAD;
      opacity: 0.7;
    }
  }
  .background-profile {
    background-image: url("../assets/about_image.jpg");
    background-size: cover;
    @media screen and (max-width: 1024px) {
      background-position: top center;
    }
  }
  .background-work {
    background-image: url("../assets/work_image.jpg");
    @media screen and (max-width: 1024px) {
      background-position: top center;
    }
  }
}
.title-simple {
  display: inline-block;
  padding-top: 200px;
  padding-bottom: 50px;
  font-size: 80px;
  letter-spacing: 0.2em;
  @media screen and (max-width: 1024px) {
    padding-top: 40px;
    padding-bottom: 20px;
    font-size: 50px;
  }
}
</style>
