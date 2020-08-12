<template>
  <h1 class="section-title" v-if="$route.path === '/about'">About</h1>
  <h1 class="section-title" v-else if="$route.path === '/work'">Works</h1>
</template>

<script>
</script>

<style lang="scss">
  .section-title {
    font-size: 60px;
    letter-spacing: 0.2em;
    margin: 20px auto;
    margin-bottom: 40px;
    text-align: left;
    width: 1600px;

    &:first-letter {
      color: #89c997;
      font-size: 100px;
    }
  }
</style>
