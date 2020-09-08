<template>
  <div id="about">
    <section-title></section-title>
    <div class="inner">
      <section class="section-padding flex">
        <toc topic="WHO AM I" />
        <profile />
      </section>
      <section class="skill section-padding flex">
        <toc topic="SKILL" />
        <skill />
      </section>
      <section class="history section-padding flex">
        <toc topic="HISTORY" />
        <history />
      </section>
    </div>
  </div>
</template>
<script>
import { bus } from '../main.js'
import SectionTitle from '../components/SectionTitle.vue'
import Toc from '../components/Toc.vue'
import Profile from '../components/AboutProfile.vue'
import Skill from '../components/AboutSkill.vue'
import History from '../components/AboutHistory.vue'
export default {
  name: 'about',
  components: {
    'section-title': SectionTitle,
    toc: Toc,
    profile: Profile,
    skill: Skill,
    history: History
  },
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
#about {
  padding-bottom: 100px;

// 共通設定
  .section-padding {
  padding-top: 80px;
  }

  .flex {
    display: flex;
    @media screen and (max-width: 1024px) {
      display: block;
    }
  }

  .content {
    width: 80%;
    @media screen and (max-width: 1024px) {
      width: 100%;
    }
  }
}
</style>
