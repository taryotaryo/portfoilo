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
  @media screen and (max-width: 1024px) {
    width: 100%;
  }
  .topic {
    position: relative;
    margin-top: 40px;
    margin-bottom: 40px;
    font-size: 24px;
    letter-spacing: 1rem;
    text-indent: 1em;
    @media screen and (max-width: 1024px) {
      margin-top: 30px;
      margin-bottom: 30px;
    }
    &:before {
      content: '';
      position: absolute;
      top: 40px;
      left: 0;
      height: 1px;
      width: 280px;
      background-color: #fff;
    }
  }
}
</style>
