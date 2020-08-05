<template>
  <div id="app">
    <v-header></v-header>
    <router-view></router-view>
    <v-footer></v-footer>
  </div>
</template>

<script>
import 'normalize.css'
import Header from './components/Header.vue'
import Footer from './components/Footer.vue'

export default {
  name: 'App',
  components: {
    'v-header': Header,
    'v-footer': Footer
  }
}
</script>

<style lang="scss">
body {
  background-color: #dcdcdc;
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
