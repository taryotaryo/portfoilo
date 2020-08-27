<template>
  <div id="about">
    <section-title></section-title>
    <div class="about-inner">
      <div class="profile section-padding flex">
        <div class="toc">
          <h2>WHO AM I</h2>
        </div>
        <div class="content">
          <div class="content-profile">
            <div class="description">
              <h3>Ryota Iwasaki</h3>
              <p>都内のSES企業でチームリーダーとして働いています。人に使ってもらえるものを自分で作りたいと思い、2019年12月から独学でプログラミング学習を開始しました。現在はフロントエンドエンジニアを目指して転職活動中です。</p>
              <div class="like">
                <h3>Likes</h3>
                <p><span v-for="(like) in likes" v-bind:key="like">{{ like }}</span></p>
              </div>
              <div class="account">
                <h3>Acounts</h3>
                <a href="https://github.com/taryotaryo" v-on:mouseover="mouseEnter()" v-on:mouseleave="mouseLeave()"><font-awesome-icon v-bind:icon="['fab', 'github']" /></a>
                <a href="https://qiita.com/KUMA_TR" v-on:mouseover="mouseEnter()" v-on:mouseleave="mouseLeave()"><font-awesome-icon v-bind:icon="['fab', 'quora']" /></a>
                <a href="https://twitter.com/KUMA90473134" v-on:mouseover="mouseEnter()" v-on:mouseleave="mouseLeave()"><font-awesome-icon v-bind:icon="['fab', 'twitter']" /></a>
                <a href="mailto:yarot.wsaiaik@outlook.jp" v-on:mouseover="mouseEnter()" v-on:mouseleave="mouseLeave()"><font-awesome-icon v-bind:icon="['fas', 'envelope']" /></a>
              </div>
            </div>
            <div class="profile-imageArea">
              <img src="../assets/profile.png" alt="プロフィール画像">
            </div>
          </div>
        </div>
      </div>
      <div class="skill section-padding flex">
        <div class="toc">
          <h2>SKILL</h2>
        </div>
        <div class="content">
          <div class="skill-graph">
            <div class="frontend">
              <p class="type">Frontend</p>
              <ul>
                <li v-for="(frontSkill) in frontSkills" v-bind:key="frontSkill">
                  <p>{{ frontSkill }}</p>
                  <div class="bar"></div>
                </li>
              </ul>
            </div>
            <div class="section-bar"></div>
            <div class="backend">
              <p class="type">Backend</p>
              <ul>
                <li v-for="(backEndSkill) in backEndSkills" v-bind:key="backEndSkill">
                  <div class="bar"></div>
                  <p>{{ backEndSkill }}</p>
                </li>
              </ul>
            </div>
          </div>
          <div class="ohter-block">
            <p class="type">Others</p>
            <ul class="tool">
              <p>Tools</p>
              <li v-for="(tool) in tools" v-bind:key="tool">{{ tool }}</li>
            </ul>
            <ul class="certification">
              <p>Certifications</p>
              <li v-for="(certification) in certifications" v-bind:key="certification">{{ certification }}</li>
            </ul>
            <ul class="businesse">
              <p>Business Skills</p>
              <li v-for="(businesse) in businesses" v-bind:key="businesse">{{ businesse }}</li>
            </ul>
          </div>
        </div>
      </div>
      <div class="history section-padding flex">
        <div class="toc">
          <h2>HISTORY</h2>
        </div>
        <div class="content">
          <ul class="timeline">
            <li>
              <p class="timeline-date">2017年6月</p>
              <div class="timeline-content">
                <h3>SES企業に未経験でバイリンガルエンジニアとして入社</h3>
                <p>インフラのモニタリングや翻訳業務に携わる。<strong>各種手順書や業務ツールに手早くアクセスできる資料をエクセルで先輩へのヒアリングし作成。</strong>その結果、業務を早く覚えることができ、先輩全員から太鼓判を押されるようになりました。</p>
              </div>
            </li>
            <li>
              <p class="timeline-date">2018年8月</p>
              <div class="timeline-content">
                <h3>現場のチームリーダーへ昇進</h3>
                <p>LinuCレベル2を4カ月で取得。その実績や面倒見のよさ、それまでの仕事を評価され、<strong>1年で現場のチームリーダーへの抜擢</strong>。新しい運用保守業務のプロジェクトの巻取り業務を任されました。</p>
              </div>
            </li>
            <li>
              <p class="timeline-date">2019年1月</p>
              <div class="timeline-content">
                <h3>主任に昇格</h3>
                <p>現場での活躍とコミュニケーション能力を評価され、<strong>同期の中では最速で主任に昇格。</strong>部下のマネジメント業務や現場の業務改善に取組みました。手順書や監視業務の見直しを行い、<strong>監視業務の稼働を30%稼働削減を実現。</strong></p>
              </div>
            </li>
            <li>
              <p class="timeline-date">2019年12月</p>
              <div class="timeline-content">
                <h3>プログラミング勉強開始</h3>
                <p>誰かの制作したアプリやをツールを使って業務に取り組むなかで、ふと「このままで大丈夫なんだろうか」という不安を感じ、徐々にその感情は「人に使ってもらえるものを自分で作りたい」に変化。特に使いやすいUIの作成に携わりたいと思い、<strong>フロントエンドエンジニアを志し、独学でプログラミング学習を開始しました。</strong></p>
              </div>
            </li>
            <li>
              <p class="timeline-date">{{ now }}</p>
              <div class="timeline-content">
                <h3>現在</h3>
                <p>Progate、ドットインストール、Udemy、30daysトライアルを活用し以下のスキルを得ました。</p>
                <p>※毎日欠かさず勉強を継続し、日々のスキルアップを行っております</p>
                <p>・作品を作れるレベルのフロントエンド技術(HTML、CSS / SCSS、Bootstrap、Javascript、jQuery、vue.js、デベロッパーツール)</p>
                <p>・基礎レベルのバックエンド技術(PHP、Ruby、Ruby on Rails、SQL、WordPress)</p>
                <p>・実業務を意識したチーム開発ツールへの理解(Git、Github、Github Flow)</p>
                <p>・デプロイ経験(Xserver、Github Pages、Firebase)</p>
                <p>・ローカル開発技術(Visual Studio Code、Vue CLI)</p>
                <p>現在、フロントエンドエンジニアを目指し転職活動中です。</p>
              </div>
            </li>
          </ul>
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
    this.now = now.getFullYear() + '年' + (now.getMonth() + 1) + '月'
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

<style lang="scss">
#about {
  margin: 0 auto;
  padding-bottom: 50px;

// 共通設定
  .section-padding {
  padding-top: 80px;
  padding-bottom: 80px;
  }

  .flex {
    display: flex;
  }

  .toc {
    width: 20%;
    h2 {
      position: relative;
      font-size: 24px;
      letter-spacing: 1rem;
      text-indent: 1rem;
      margin-top: 40px;
      margin-bottom: 40px;
      &:before {
        position: absolute;
        top: 40px;
        height: 1px;
        width: 280px;
        content: '';
        background-color: #fff;
      }
    }
  }
  h2, h3, a {
  color: #fff;
  cursor: none;
  }
  p {
    color: darken(#fff, 15%);
    cursor: none;
  }

  .content {
    width: 80%;
  }

  .about-inner {
    width: 100%;

    .profile {

      .content-profile {
        .description {
          h3 {
            font-size: 40px;
          }
          p {
            width: 50%;
          }
          .like {
            margin-top: 20px;
            h3 {
              font-size: 20px;
            }
            span {
              margin-right: 10px;
            }
          }
          .account {
            margin-top: 30px;
            color: #fff;
            h3 {
              font-size: 20px;
            }
            a {
              position: relative;
              margin-right: 40px;
              font-size: 30px;
              text-decoration: none;
              transition: .3s;
              &:hover:before {
                content: 'Click';
                display: block;
                position: absolute;
                top: -16px;
                left: 50%;
                transform: translateX(-50%);
                font-size: 16px;
                font-weight: bold;
              }

              &:nth-of-type(1):hover{
                color: #171515;
              }
              &:nth-of-type(2):hover{
                color: #55C500;
              }
              &:nth-of-type(3):hover{
                color: #00acee;
              }
              &:nth-of-type(4):hover{
                color: #487c38;
              }
            }
          }
        }
        .profile-imageArea {
          text-align: right;
          margin-right: 300px;
          img {
            width: 200px;
          }
        }
      }
    }
    .skill {
      .bar {
          width:  20px;
          height: 100px;
          margin:  0 auto;
          background-color: #fff;
      }
      li {
        display:  inline-block;
        width:  100px;
        font-size: 16px;
        text-align:  center;
      }
      ul {
        font-size: 0; // li要素をボーダーにくっつける
      }
      .skill-graph {
        margin-top: 200px;
        margin-bottom: 200px;
        .type {
          position: absolute;
          font-size: 24px;
          font-weight: bold;
          letter-spacing: 0.8rem;
        }
        .frontend {
          position: relative;
          color: #fff;
          p {
            color: #fff;
          }
          .type {
            top: 50%;
            right: 80px;
            transform: translateY(-50%);
          }
        }
        .backend {
          position: relative;
          .type {
            top: 50%;
            right: 96px;
            transform: translateY(-50%);
            color: #666;
          }
          p {
            color: #666;
          }
          .bar {
            background-color: #666;
          }
        }
        .section-bar {
          height: 1px;
          width: 100%;
          background-color: #fff;
        }
      }
      .ohter-block {
        .type {
          position: absolute;
          right: 135px;
          color: darken(#fff, 15%);
          font-size: 24px;
          font-weight: bold;
          letter-spacing: 0.8rem;
        }
        display: flex;
        ul {
          width: 20%;
          font-size: 20px;
          li {
            width: 100%;
            display: block;
            color: darken(#fff, 15%);
            text-align: left;
          }
        }
      }
    }
    .history {
      .timeline {
        margin-top: 200px;
        list-style: none;
        li {
          margin-bottom: 60px;
          overflow: hidden;
          margin: 0;
          position: relative;
        }
        .timeline-date {
          width: 110px;
          float: left;
          margin-top: 20px;
        }
        .timeline-content {
          width: 75%;
          float: left;
          border-left: 3px #fff solid;
          padding-left: 30px;
          &:before {
            content: '';
            width: 12px;
            height: 12px;
            background: #89c997;
            position: absolute;
            left: 106px;
            top: 24px;
            border-radius: 100%;
          }
        }
      }
    }
  }
}
</style>
