<template>
<div class="content">
  <div class="skillGraph">
    <div class="frontend">
      <p class="skillType position">Frontend</p>
      <ul class="skillList">
        <li class="skill" v-for="(frontSkill) in frontSkills" v-bind:key="frontSkill">
          <p>{{ frontSkill }}</p>
          <div class="bar bar-white"></div>
        </li>
      </ul>
    </div>
    <div class="dividingLine"></div>
    <div class="backend">
      <p class="skillType position">Backend</p>
      <ul class="skillList">
        <li class="skill" v-for="(backEndSkill) in backEndSkills" v-bind:key="backEndSkill">
          <div class="bar bar-gray"></div>
          <p>{{ backEndSkill }}</p>
        </li>
      </ul>
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
export default {
  data: function () {
    return {
      frontSkills: [
        'HTML',
        'CSS(SCSS)',
        'Bootstrap',
        'JavaScript',
        'jQuery',
        'Vue.js',
        'Vue CLI',
        'Webpack'
      ],
      backEndSkills: [
        'PHP',
        'Ruby',
        'Ruby on rails',
        'SQL',
        'WordPress',
        'Firebase'
      ],
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
    .bar {
      height: 100px;
      width:  20px;
      margin:  0 auto;
    }
    .skill {
      display:  inline-block;
      width:  100px;
      font-size: 16px;
      text-align:  center;
    }
    .skillList {
      font-size: 0; // li要素をボーダーにくっつける
    }
    // フロントエンド用CSS
    .frontend {
      position: relative;
      color: #fff;
      .position {
        top: 50%;
        right: 80px;
        transform: translateY(-50%);
      }
      .bar-white {
        background-color: #fff;
      }
    }
    // バックエンド用CSS
    .backend {
      position: relative;
      color: #666;
      .position {
        top: 50%;
        right: 96px;
        transform: translateY(-50%);
      }
      .bar-gray {
        background-color: #666;
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
