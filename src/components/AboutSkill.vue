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
  <div class="chart-sp">
    <p class="headline">Tech Skills</p>
    <skillchartforsp class="chart-sp" width="360" height="300" />
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
import SkillChartForSp from './AboutSkillGrauhForSp'
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
    backendskillchart: BackendSkillChart,
    skillchartforsp: SkillChartForSp
  }
}
</script>

<style scoped lang="scss">
.skill {
  // 共通class
  .chart-sp {
      display: none;
      .headline {
        margin-top: 120px;
        margin-bottom: 10px;
        color: #fff;
        font-size: 18px;
        font-weight: bold;
        letter-spacing: 0.1rem;
        text-align: center;
      }
      @media screen and (max-width: 767px) {
        display: block;
      }
    }
  .skillType {
    position: absolute;
    font-size: 24px;
    font-weight: bold;
    letter-spacing: 0.8rem;
  }
  .skillGraph {
    margin-top: 200px;
    margin-bottom: 200px;
    @media screen and (max-width: 767px) {
      display: none;
    }
    .chart {
      @media screen and (max-width: 1024px) {
        margin-left: 100px;
      }
    }
    // フロントエンド用CSS
    .frontend {
      position: relative;
      color: #fff;
      .position {
        top: 50%;
        right: 80px;
        transform: translateY(-50%);
        @media screen and (max-width: 1200px) {
          display: none;
        }
      }
    }
    // バックエンド用CSS
    .backend {
      position: relative;
      color: #8e8e8e;
      .position {
        top: 50%;
        right: 100px;
        transform: translateY(-50%);
        @media screen and (max-width: 1200px) {
          display: none;
        }
      }
    }
    .dividingLine {
      height: 1px;
      width: 100%;
      background-color: #fff;
      @media screen and (max-width: 1024px) {
        width: 90%;
        margin-left: auto;
      }
    }
  }
  .ohter {
    display: flex;
    color: darken(#fff, 30%);
      @media screen and (max-width: 1024px) {
        justify-content: space-around;
      }
      @media screen and (max-width: 767px) {
        display: block;
        text-align: center;
      }
    .position {
      right: 135px;
      @media screen and (max-width: 1200px) {
        display: none;
      }
    }
    .unit {
      width: 20%;
      font-size: 20px;
      @media screen and (max-width: 767px) {
        width: 100%;
        font-size: 16px;
        text-align: left;
        text-align: center;
      }
    }
    .headline {
      color: #fff;
      font-weight: bold;
      margin-bottom: 10px;
      letter-spacing: 0.1rem;
      @media screen and (max-width: 767px) {
        margin-top: 20px;
        font-size: 18px;
        text-align: center;
      }
    }
    .otherlist {
      list-style: none;
      line-height: 1.5;
      letter-spacing: 0.1rem;
    }
  }
}
</style>
