<template>
    <footer>
        <p v-on:mouseover="mouseEnter()" v-on:mouseleave="mouseLeave()">Copyright © 2020 Ryota Iwasaki All Rights Reserved.</p>
    </footer>
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

<style>
footer p {
    color: #fff;
    text-align: center;
    padding-bottom: 40px;
}
</style>
