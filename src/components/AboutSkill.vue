<template>
<div class="content">
  <div class="skillGraph">
    <div class="frontend">
      <div class="chartBox">
        <frontendskillchart class="chart" width="600" height="200"></frontendskillchart>
      </div>
      <p class="skillType position">Frontend</p>
    </div>
    <div class="dividingLine"></div>
    <div class="backend">
      <div class="chartBox">
        <backendskillchart class="chart" width="600" height="200"></backendskillchart>
      </div>
      <p class="skillType position">Backend</p>
    </div>
  </div>
  <div class="ohter">
    <p class="skillType position">Others</p>
    <div class="unit">
      <p class="headline">Tools</p>
      <ul class="otherlist">
        <li v-for="(tool) in tools" v-bind:key="tool">{{ tool }}</li>
      </ul>
    </div>
    <div class="unit">
      <p class="headline">Certifications</p>
      <ul class="otherlist">
        <li v-for="(certification) in certifications" v-bind:key="certification">{{ certification }}</li>
      </ul>
    </div>
    <div class="unit">
      <p class="headline">Business Skills</p>
      <ul class="otherlist">
        <li v-for="(businesse) in businesses" v-bind:key="businesse">{{ businesse }}</li>
      </ul>
    </div>
  </div>
</div>
</template>

<script>
import FrontendSkillChart from './AboutSkillFrontend'
import BackendSkillChart from './AboutSkillBackend'
export default {
  data: function () {
    return {
      tools: [
        'Git',
        'Github',
        'Developer Tools',
        'Visual Studio Code'
      ],
      certifications: [
        'LinuC1',
        'LinuC2',
        'CCNA',
        'TOEIC780'
      ],
      businesses: [
        'Leader experience',
        'Writing Ability',
        'Infrastructure Operation',
        'translation'
      ]
    }
  },
  components: {
    frontendskillchart: FrontendSkillChart,
    backendskillchart: BackendSkillChart
  }
}
</script>

<style scoped lang="scss">
.skill {
  // 共通class
  .skillType {
    position: absolute;
    font-size: 24px;
    font-weight: bold;
    letter-spacing: 0.8rem;
  }
  .skillGraph {
    margin-top: 200px;
    margin-bottom: 200px;
    // フロントエンド用CSS
    .frontend {
      position: relative;
      color: #fff;
      .position {
        top: 50%;
        right: 80px;
        transform: translateY(-50%);
      }
    }
    // バックエンド用CSS
    .backend {
      position: relative;
      color: #8e8e8e;
      .position {
        top: 50%;
        right: 96px;
        transform: translateY(-50%);
      }
    }
    .dividingLine {
      height: 1px;
      width: 100%;
      background-color: #fff;
    }
  }
  .ohter {
    display: flex;
    color: darken(#fff, 30%);
    .position {
      right: 135px;
    }
    .unit {
      width: 20%;
      font-size: 20px;
    }
    .headline {
      font-weight: bold;
      margin-bottom: 10px;
    }
    .otherlist {
      list-style: none;
    }
  }
}
</style>
