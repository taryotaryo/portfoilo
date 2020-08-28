<template>
  <div class="toc">
      <h2 class="topic">{{ topic }}</h2>
  </div>
</template>

<script>
export default {
  props: [
    'topic'
  ]
}
</script>

<style scoped lang="scss">
.toc {
  width: 20%;
  .topic {
    position: relative;
    margin-top: 40px;
    margin-bottom: 40px;
    font-size: 24px;
    letter-spacing: 1rem;
    text-indent: 1rem;
    &:before {
      content: '';
      position: absolute;
      top: 40px;
      height: 1px;
      width: 280px;
      background-color: #fff;
    }
  }
}
</style>
