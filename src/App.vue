<template>
  <div id="app" v-on:mousemove="callChildMethod()">
    <v-cursor ref="child"></v-cursor>
    <v-header v-on:mouseenter="callChildMethod2()"></v-header>
    <transition>
    <router-view></router-view>
    </transition>
    <v-footer></v-footer>
  </div>
</template>

<script>
import 'normalize.css'
import Header from './components/Header.vue'
import Footer from './components/Footer.vue'
import Cursor from './components/Cursor.vue'
export default {
  name: 'App',
  components: {
    'v-header': Header,
    'v-footer': Footer,
    'v-cursor': Cursor
  },
  methods: {
    callChildMethod () {
      this.$refs.child.getCursorCoordinate(event)
    },
    callChildMethod2 () {
      this.$refs.child.cursorHover()
    }
  }
}
</script>

<style lang="scss">
.v-enter, .v-leave-to {
    opacity: 0;
}
.v-enter-to, .v-leave {
    opacity: 1;
}
.v-enter-active, .v-leave-active {
    transition: opacity 300ms;
}

body {
  background-color: #dcdcdc;
  cursor: none;
  position: relative;
}

body a:hover{
  cursor: none;/*aタグホバーのカーソルも非表示に*/
}

p {
  margin: 0;
  color: #696969;
  line-height: 2;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #fff;
}
</style>
