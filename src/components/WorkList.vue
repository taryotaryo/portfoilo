<template>
  <div>
    <div class="worklist section-padding flex" v-for="workList in workLists" v-bind:key="workList">
      <div class="toc">
        <h2>{{ workList.toc }}</h2>
      </div>
      <div class="worklist-section">
        <div class="worklist-left">
          <a v-bind:href="workList.url" class="worklist-movie" v-on:mouseover="mouseEnter()" v-on:mouseleave="mouseLeave()">
            <video v-bind:src="workList.image" loop autoplay muted></video>
          </a>
        </div>
        <div class="worklist-right">
          <h3><span class="worklist-icon"><font-awesome-icon icon="caret-square-right" /></span>概要</h3>
          <ul class="worklist-summary">
            <li v-for="summary in workList.summaries" v-bind:key="summary">{{ summary }}</li>
          </ul>
          <h3><span class="worklist-icon"><font-awesome-icon icon="laptop-code" /></span>使用技術・デプロイ</h3>
          <span class="worklist-tech" v-for="tech in workList.techs" v-bind:key="tech">{{ tech }}</span>
          <h3><span class="worklist-icon"><font-awesome-icon icon="lightbulb" /></span>こだわりポイント</h3>
          <ul class="worklist-commitments">
            <li class="worklist-commitment" v-for="commitment in workList.commitments" v-bind:key="commitment">{{ commitment }}</li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { bus } from '../main.js'
export default {
  name: 'workList',
  data: function () {
    return {
      workLists: [
        {
          image: require('../assets/portfolio_movie.mp4'),
          url: 'https://ta-ryo.com/lp',
          toc: '01',
          techs: ['HTML', 'CSS', 'hover.css', 'Javascript(jQuery)', 'Xserver'],
          summaries: [
            '縦長のシングルページで制作したポートフォリオサイト'
          ],
          commitments: [
            '開いた瞬間のインパクトにこだわった画面いっぱいのヒーロームービーを実装',
            '上部固定ヘッダーを背景に埋もれさせないように色を背景色に合わせて変化',
            '見た目に多くの動きを実装する過程で様々なライブラリを経験',
            'ホバーしたら何もないところから説明文を出現させる実装を独力で実装'
          ]
        },
        {
          image: require('../assets/portfolio_janken.mp4'),
          url: 'https://ta-ryo.com/lp',
          toc: '02',
          techs: ['Vue.js', 'Vue CLI', 'Vue Router', 'Github Pages'],
          summaries: [
            'vue.jsで制作したじゃんけんアプリ',
            'vue.jsを実践的に学ぶために制作',
            '開始ボタンを押すことで何度でも再戦可能',
            '勝敗結果を保持し戦績をスコアページで確認できる'
          ],
          commitments:
          [
            '「はじめる」ボタンを押したらそのボタンは押せなくなり、出す手を決めるボタンを押せるようになる等の制御を実装',
            'ゲーム画面とスコア画面の切り替えにSPAで構成',
            'じゃんけんの戦績をスコアに渡せるようにコンポーネント間でデータの受け渡しを実装'
          ]
        },
        {
          image: require('../assets/this_portfolio.mp4'),
          url: '#',
          toc: '03',
          techs: ['Vue.js', 'Vue CLI', 'Vue Router', 'npm', 'Firebase'],
          summaries: [
            'vue.jsで作成したポートフォリオサイト',
            '計5ページで構成(ホーム、技術や経歴紹介、作品紹介、執筆した記事一覧、コンタクト)'
          ],
          commitments:
          [
            'hover後の誘導機能とずっと動かしていたくなるような変化機能を備えたマウスストーカーを実装',
            'axiosでqiita APIにhttp接続し執筆した記事を取得。Postページに一覧表示',
            '共通化可能な部分は積極的にComponent化',
            'npmを利用してaxios、FontAwesomeなどのパッケージを活用',
            'Firebaseへのデプロイ',
            'シンプルで統一感のあるデザインにするため色を3色に限定'
          ]
        },
        {
          image: require('../assets/portofolio_blog.mp4'),
          url: 'https://ta-ryo.com/',
          toc: '04',
          techs: ['HTML', 'SCSS', 'Javascript(jQuery)', 'PHP', 'WordPress', 'Xserver'],
          summaries: [
            'はじめて作成したWordPressテーマ',
            '記事投稿、アイキャッチ、目次、パンくずリスト、ウィジェット、お問い合わせ機能、記事検索など基本的な機能を利用可能'
          ],
          commitments:
          [
            'デザインツールを学ぶためにデザイン過程でAdobeXDを使用し草案を作成',
            'レスポンシブ対応',
            '制作過程でPHPの基礎を習得',
            'エディタに構文チェッカーを導入し、WordPressコーディング規約に完全準拠'
          ]
        }
      ]
    }
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
// 共通設定
.section-padding {
padding-top: 80px;
padding-bottom: 80px;
}

.flex {
  display: flex;
}

p, li {
  color: darken(#fff, 15%);
}

.worklist {
  margin-bottom: 30px;
  color: #fff;
  margin-bottom: 80px;
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
        width: 180px;
        content: '';
        background-color: #fff;
      }
    }
  }
  .worklist-section {
    display: flex;
    margin-top: 60px;
    width: 80%;

    .worklist-left {
      width: 40%;
      text-align: left;
      .worklist-movie {
        video {
          margin-top: 20px;
          transition: 0.5s;
          width: 100%;
            &:hover {
              opacity: 0.8;
          }
        }
      }
    }
    .worklist-right {
      margin-left: 50px;
      width: 50%;
      h3 {
        font-size: 20px;
        margin-top: 20px;
        margin-bottom: 20px;
      }
      p, li{
        font-size: 18px;
        line-height: 1.6rem;
      }
      .worklist-icon {
        margin-right: 1rem;
      }
      .worklist-tech {
        padding: 8px 10px;
        margin-right: 8px;
        margin-bottom: 8px;
      }
    }
  }
}
</style>
