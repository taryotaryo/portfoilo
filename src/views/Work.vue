<template>
  <div id="work">
    <div class="work-inner">
      <section-title></section-title>
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
.work-inner {
  width: 1600px;
  margin: 0 auto;
}
</style>
