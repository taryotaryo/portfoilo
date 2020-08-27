<template>
  <div id="work">
      <section-title></section-title>
    <div class="work-inner">
      <work-list></work-list>
    </div>
  </div>
</template>

<script>
import SectionTitle from '../components/SectionTitle.vue'
import WorkList from '../components/WorkList.vue'
export default {
  name: 'work',
  components: {
    'section-title': SectionTitle,
    'work-list': WorkList
  }
}
</script>

<style lang="scss">
#work {
  padding-bottom: 50px;
    .work-inner {
      width: 100%;
      margin: 0 auto;
    }
}
</style>
