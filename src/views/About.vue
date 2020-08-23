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
              <p>くまです。都内のSES企業でチームリーダーとして働いています。人に使ってもらえるものを自分で作りたいと思い、2019年12月から独学でプログラミング学習を開始しました。現在はフロントエンドエンジニアを目指して転職活動中です。</p>
            </div>
          </div>
          <div class="myacounts">
            <a href="https://github.com/taryotaryo" class="github myacount" v-on:mouseover="mouseEnter()" v-on:mouseleave="mouseLeave()"><span><font-awesome-icon v-bind:icon="['fab', 'github']" /></span><span>github</span></a>
            <a href="https://qiita.com/KUMA_TR" class="qiita myacount" v-on:mouseover="mouseEnter()" v-on:mouseleave="mouseLeave()"><span><font-awesome-icon v-bind:icon="['fab', 'quora']" /></span><span>Qiita</span></a>
            <a href="https://twitter.com/KUMA90473134" class="twitter myacount" v-on:mouseover="mouseEnter()" v-on:mouseleave="mouseLeave()"><span><font-awesome-icon v-bind:icon="['fab', 'twitter']" /></span><span>Twitter</span></a>
            <a href="mailto:yarot.wsaiaik@outlook.jp" class="mail myacount" v-on:mouseover="mouseEnter()" v-on:mouseleave="mouseLeave()"><span><font-awesome-icon v-bind:icon="['fas', 'envelope']" /></span><span>Mail</span></a>
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
          <p>2017年6月</p>
          <p>SES企業に未経験でバイリンガルエンジニアとして入社。インフラのモニタリングや翻訳業務に携わる。<strong>各種手順書や業務ツールに手早くアクセスできる資料をエクセルで先輩へのヒアリングし作成。</strong>その結果、業務を早く覚えることができ、先輩全員から太鼓判を押されるようになりました。</p>
          <p>2018年8月</p>
          <p>LinuCレベル2を4カ月で取得。その実績や面倒見のよさ、それまでの仕事を評価され、<strong>1年で現場のチームリーダーへの抜擢</strong>。新しい運用保守業務のプロジェクトの巻取り業務を任されました。</p>
          <p>2019年1月</p>
          <p>現場での活躍とコミュニケーション能力を評価され、<strong>同期の中では最速で主任に昇格。</strong>部下のマネジメント業務や現場の業務改善に取組みました。手順書や監視業務の見直しを行い、<strong>監視業務の稼働を30%稼働削減を実現。</strong></p>
          <p>2019年12月</p>
          <p>誰かの制作したアプリやをツールを使って業務に取り組むなかで、ふと「このままで大丈夫なんだろうか」という不安を感じ、徐々にその感情は「人に使ってもらえるものを自分で作りたい」に変化。特に使いやすいUIの作成に携わりたいと思い、<strong>フロントエンドエンジニアを志し、独学でプログラミング学習を開始しました。</strong></p>
          <p>{{ now }}</p>
          <p>Progate、ドットインストール、Udemy、30daysトライアルを活用し以下のスキルを得ました。<br>※毎日欠かさず勉強を継続し、日々のスキルアップを行っております</p>
          <ul>
            <li>作品を作れるレベルのフロントエンド技術(HTML、CSS / SCSS、Bootstrap、Javascript、jQuery、vue.js、デベロッパーツール)</li>
            <li>基礎レベルのバックエンド技術(PHP、Ruby、Ruby on Rails、SQL、WordPress)</li>
            <li>実業務を意識したチーム開発ツールへの理解(Git、Github、Github Flow)</li>
            <li>デプロイ経験(Xserver、Github Pages、Firebase)</li>
            <li>ローカル開発技術(Visual Studio Code、Vue CLI)</li>
          </ul>
          <p>現在、フロントエンドエンジニアを目指し転職活動中です。</p>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import { bus } from '../main.js'
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
        'Developer Tools',
        'Vue.js',
        'Vue CLI',
        'Webpack',
        'PHP',
        'Ruby',
        'Ruby on rails',
        'SQL',
        'WordPress',
        'Git',
        'Github',
        'Firebase',
        'Visual Studio Code'
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
      ],
      now: ''
    }
  },
  mounted: function () {
    const now = new Date()
    this.now = now.getFullYear() + '年' + (now.getMonth() + 1) + '月 現在'
  },
  methods: {
    mouseEnter: function () {
      bus.$emit('bus-event-onView')
    },
    mouseLeave: function () {
      bus.$emit('bus-event-off')
    }
  }
}
</script>

<style lang="scss">
#about {
  margin: 0 auto;
  width: 1600px;
}

li {
  line-height: 1.8;
}

.about-inner {
  color: #696969;
  display: flex;
  justify-content: space-around;
  padding-bottom: 40px;

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

      .myacounts {
        font-size: 30px;
        text-align: right;

        .myacount {
          margin-right: 40px;
          text-decoration: none;
          transition: 0.3s;
          &:hover {
            color: #89c997;
          }
        }
      }

      .github {
        color: #171515;
      }

      .qiita {
        color: #55C500;
      }

      .twitter {
        color: #00acee;
      }

      .mail {
        color: #487c38;
      }

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

    .history {
      p {
        &:nth-child(even) {
          font-weight: bold;
          font-size: 20px;
        }
        &:nth-child(odd) {
          text-indent: 1rem;
        }
      }
    }
  }
}
</style>
