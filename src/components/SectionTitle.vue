<template>
  <h1 class="section-title" v-if="$route.path === '/about'" v-on:mouseover="mouseEnter()" v-on:mouseleave="mouseLeave()">About</h1>
  <h1 class="section-title" v-else-if="$route.path === '/work'" v-on:mouseover="mouseEnter()" v-on:mouseleave="mouseLeave()">Works</h1>
  <h1 class="section-title" v-else-if="$route.path === '/post'" v-on:mouseover="mouseEnter()" v-on:mouseleave="mouseLeave()">Post</h1>
  <h1 class="section-title" v-else-if="$route.path === '/contact'" v-on:mouseover="mouseEnter()" v-on:mouseleave="mouseLeave()">Contact</h1>
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
  .section-title {
    display: inline-block;
    font-size: 60px;
    letter-spacing: 0.2em;
    margin: 60px auto 60px auto;
    text-align: left;

    &:first-letter {
      color: #89c997;
      font-size: 100px;
    }
  }
</style>
