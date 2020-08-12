<template>
  <div id="about">
    <section-title></section-title>
    <div class="about-inner">
      <div class="about-left">
        <div class="profile frame">
          <h2 class="about-title">Profile</h2>
          <div class="profile-area">
            <div class="profile-imageArea">
              <img src="../assets/profile.png" alt="プロフィール画像">
            </div>
            <div class="profile-description">
              <p>くまです。人に使ってもらえるものを自分で作りたいと思い、2019年12月からプログラミングを学んでいます。現在はとあるIT企業でチームリーダーとして働きつつ、フロントエンドエンジニアを目指して転職活動中です。</p>
            </div>
          </div>
        </div>
        <div class="techskill frame">
          <h2 class="about-title">TechSkill</h2>
          <div class="lists-style">
            <span class="list-style" v-for="(techskill, index) in techSkills" v-bind:key="index">{{ techskill }}</span>
          </div>
        </div>
        <div class="about-left-bottom">
          <div class="otherskill frame">
            <h2 class="about-title">OtherSkill</h2>
            <div class="lists-style">
              <span class="list-style" v-for="(otherSkill, index) in otherSkills" v-bind:key="index">{{ otherSkill }}</span>
            </div>
          </div>
          <div class="like frame">
            <h2 class="about-title">Like</h2>
            <div class="lists-style">
              <span class="list-style" v-for="(like, index) in likes" v-bind:key="index">{{ like }}</span>
            </div>
          </div>
        </div>
      </div>
      <div class="about-right">
        <div class="history frame">
          <h2 class="about-title">History</h2>
          <p class="weight">2017年6月</p>
          <p>とあるIT企業に未経験でバイリンガルエンジニアとして入社。社内研修1カ月でネットワーク系の資格であるCCNAを取得し、運用保守の現場に配属。大手企業のインフラのモニタリングの仕事を行うことになる。</p>
          <p class="weight">2018年8月</p>
          <p>仕事の合間に勉強しLinuCレベル2を4カ月で取得。その功績や面倒見のよさと、それまでの仕事を評価され、<strong>1年で現場のチームリーダーへの抜擢</strong>。新しいプロジェクトの巻取り業務を任される。</p>
          <p class="weight">2019年1月</p>
          <p>現場での活躍とコミュニケーション能力を評価され、<strong>同期の中では最速で主任に昇格。</strong>現場の部下をマネジメントしつつ、自らもプレイヤーとしても働く。プロジェクトの日々業務改善、はじめてのマネジメントに思考錯誤の日々を過ごす。</p>
          <p class="weight">2019年12月</p>
          <p>幅広く業務を学べるものの、<strong>誰かが作ったものだけを使って業務をしており、ふと「それで大丈夫なんだろうか」という漫然とした不安</strong>を感じる。徐々にその感情は「人に使ってもらえるものを自分で作りたい」となり、プログラミングを学び始める。</p>
          <p class="weight">2020年6月</p>
          <p>Webサイトの模写、簡単なアプリを作成、ポートフォリオを2つ完成させる。日常が彩られたように楽しくなり、充実した毎日を過ごす。フロントエンドエンジニアを志し、Javascriptやvue.jsを中心に学んでいます。</p>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import SectionTitle from '../components/SectionTitle.vue'
export default {
  name: 'about',
  components: {
    'section-title': SectionTitle
  },
  data: function () {
    return {
      aboutTitle: true,
      techSkills: [
        'HTML',
        'CSS',
        'SCSS',
        'Bootstrap',
        'JavaScript',
        'jQuery',
        'Vue.js',
        'Vue CLI',
        'Webpack',
        'PHP',
        'Ruby',
        'Ruby on rails',
        'WordPress',
        'Git',
        'Github'
      ],
      otherSkills: [
        'Leader experience',
        'Writing Ability',
        'Infrastructure Operation',
        'translation',
        'TOEIC780',
        'LinuC1',
        'LinuC2',
        'CCNA'
      ],
      likes: [
        'ギター',
        'ライブ',
        '自然巡り',
        '読書',
        'ジョギング',
        '筋トレ',
        'テニス',
        'チーズクルチャ',
        'THE BACK HORN',
        'ネクライトーキー'
      ]
    }
  }
}
</script>

<style lang="scss">
.about-inner {
  color: #696969;
  display: flex;
  justify-content: space-around;
  margin: 0 auto;
  width: 1600px;
  padding-bottom: 40px;

  .weight {
    font-weight: bold;
    font-size: 20px;
  }

  .frame {
    background-color: #fff;
    border-radius: 5px;
    box-shadow: 0px 8px 8px #cccccc;
    padding: 20px 20px;
    margin-bottom: 20px;
  }

  .about-title {
    background-color: #89c997;
    border-radius: 5px;
    color: #fff;
    display: inline-block;
    padding: 5px 20px 5px 30px;
    position: relative;
    font-size: 30px;
    margin-top: 0;

    &:before {
      content: '';
      position: absolute;
      top: 50%;
      transform: translateY(-50%);
      left: 10px;
      width: 10px;
      height: 10px;
      border-radius: 50%;
      background-color: #fff;
    }
  }

  .lists-style {
    display: flex;
    flex-wrap: wrap;
  }

  .list-style {
    background-color: #cd5c5c;
    border-radius: 5px;
    color: #fff;
    font-weight: bold;
    padding: 8px 10px;
    margin-right: 8px;
    margin-bottom: 8px;
  }

  .about-left {
    width: 47%;

    .profile-area {
      display: flex;

      img {
        width: 100px;
        margin-right: 50px;
        height: auto;
      }
    }

    .about-left-bottom {
      display: flex;
      margin: 0 auto;
      justify-content: space-between;
      width: 100%;

      .otherskill, .like {
        width: 43%;
      }
    }
  }

  .about-right {
    width: 47%;
  }
}
</style>
