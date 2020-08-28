<template>
  <div id="works">
      <section-title></section-title>
    <div class="inner">
      <section class="work">
        <toc v-bind:topic="work1.topic" />
        <work-list v-bind:workinfo="work1"></work-list>
      </section>
      <section class="work">
        <toc v-bind:topic="work2.topic" />
        <work-list v-bind:workinfo="work2"></work-list>
      </section>
      <section class="work">
        <toc v-bind:topic="work3.topic" />
        <work-list v-bind:workinfo="work3"></work-list>
      </section>
      <section class="work">
        <toc v-bind:topic="work4.topic" />
        <work-list v-bind:workinfo="work4"></work-list>
      </section>
    </div>
  </div>
</template>

<script>
import SectionTitle from '../components/SectionTitle.vue'
import Toc from '../components/Toc.vue'
import WorkList from '../components/WorkList.vue'
export default {
  name: 'work',
  components: {
    'section-title': SectionTitle,
    toc: Toc,
    'work-list': WorkList
  },
  data: function () {
    return {
      work1: {
        image: require('../assets/portfolio_movie.mp4'),
        url: 'https://ta-ryo.com/lp',
        topic: '01',
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
      work2: {
        image: require('../assets/portfolio_janken.mp4'),
        url: 'https://ta-ryo.com/lp',
        topic: '02',
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
      work3: {
        image: require('../assets/this_portfolio.mp4'),
        url: '#',
        topic: '03',
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
      work4: {
        image: require('../assets/portofolio_blog.mp4'),
        url: 'https://ta-ryo.com/',
        topic: '04',
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
    }
  }
}
</script>

<style scoped lang="scss">
#works {
  padding-bottom: 50px;
  .inner {
    width: 100%;
    margin: 0 auto;
  }
  .work {
    display: flex;
    padding-top: 80px;
    color: #fff;
  }
}
</style>
