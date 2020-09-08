<template>
<div class="content">
  <ul class="timeline">
    <li class="event clearfix">
      <p class="date"><time>2017年6月</time></p>
      <div class="what">
        <p class="date-sp"><time>2017年6月</time></p>
        <h3 class="headline">SES企業に未経験でバイリンガルエンジニアとして入社</h3>
        <p class="description">インフラのモニタリングや翻訳業務に携わる。<strong>各種手順書や業務ツールに手早くアクセスできる資料をエクセルで先輩へのヒアリングし作成。</strong>その結果、業務を早く覚えることができ、先輩全員から太鼓判を押されるようになりました。</p>
      </div>
    </li>
    <li class="event clearfix">
      <p class="date"><time>2018年8月</time></p>
      <div class="what">
        <p class="date-sp"><time>2018年8月</time></p>
        <h3 class="headline">現場のチームリーダーへ昇進</h3>
        <p class="description">LinuCレベル2を4カ月で取得。その実績や面倒見のよさ、それまでの仕事を評価され、<strong>1年で現場のチームリーダーへの抜擢</strong>。新しい運用保守業務のプロジェクトの巻取り業務を任されました。</p>
      </div>
    </li>
    <li class="event clearfix">
      <p class="date"><time>2019年1月</time></p>
      <div class="what">
        <p class="date-sp"><time>2019年1月</time></p>
        <h3 class="headline">主任に昇格</h3>
        <p class="description">現場での活躍とコミュニケーション能力を評価され、<strong>同期の中では最速で主任に昇格。</strong>部下のマネジメント業務や現場の業務改善に取組みました。手順書や監視業務の見直しを行い、<strong>監視業務の稼働を30%稼働削減を実現。</strong></p>
      </div>
    </li>
    <li class="event clearfix">
      <p class="date"><time>2019年12月</time></p>
      <div class="what">
        <p class="date-sp"><time>2019年12月</time></p>
        <h3 class="headline">プログラミング勉強開始</h3>
        <p class="description">誰かの制作したアプリやをツールを使って業務に取り組むなかで、ふと「このままで大丈夫なんだろうか」という不安を感じ、徐々にその感情は「人に使ってもらえるものを自分で作りたい」に変化。特に使いやすいUIの作成に携わりたいと思い、<strong>フロントエンドエンジニアを志し、独学でプログラミング学習を開始しました。</strong></p>
      </div>
    </li>
    <li class="event clearfix">
      <p class="date"><time>{{ cuurentMonth }}</time></p>
      <div class="what">
        <p class="date-sp"><time>{{ cuurentMonth }}</time></p>
        <h3 class="headline">現在</h3>
        <p class="description">Progate、ドットインストール、Udemy、30daysトライアルを活用し以下のスキルを得ました。</p>
        <p class="description">※毎日欠かさず勉強を継続し、日々のスキルアップを行っております</p>
        <p class="description">・作品を作れるレベルのフロントエンド技術(HTML、CSS / SCSS、Bootstrap、Javascript、jQuery、vue.js、デベロッパーツール)</p>
        <p class="description">・基礎レベルのバックエンド技術(PHP、Ruby、Ruby on Rails、SQL、WordPress)</p>
        <p class="description">・実業務を意識したチーム開発ツールへの理解(Git、Github、Github Flow)</p>
        <p class="description">・デプロイ経験(Xserver、Github Pages、Firebase)</p>
        <p class="description">・ローカル開発技術(Visual Studio Code、Vue CLI)</p>
        <p class="description">現在、フロントエンドエンジニアを目指し転職活動中です。</p>
      </div>
    </li>
  </ul>
</div>
</template>

<script>
export default {
  data: function () {
    return {
      cuurentMonth: ''
    }
  },
  mounted: function () {
    const cuurentMonth = new Date()
    this.cuurentMonth = cuurentMonth.getFullYear() + '年' + (cuurentMonth.getMonth() + 1) + '月'
  }
}
</script>

<style scoped lang="scss">
.content {
  .timeline {
    margin-top: 200px;
    list-style: none;
      @media screen and (max-width: 1024px) {
        margin-top: 200px;
      }
      @media screen and (max-width: 767px) {
        margin-top: 120px;
      }
    .clearfix:after {
      content: "";
      display: block;
      clear: both;
    }
    .event {
      overflow: hidden;
      position: relative;
      @media screen and (max-width: 1024px) {
        width: 90%;
        margin-left: 60px;
      }
      @media screen and (max-width: 767px) {
        margin: 0 auto;
        overflow: visible;
      }
    }
    .date {
      float: left;
      margin-top: 20px;
      width: 110px;
      @media screen and (max-width: 767px) {
        display: none;
      }
    }
    .what {
      float: left;
      width: 75%;
      padding-left: 30px;
      border-left: 3px #fff solid;
      @media screen and (max-width: 1024px) {
        width: 80%;
      }
      @media screen and (max-width: 767px) {
        width: 100%;
      }
      .date-sp {
        display: none;
        @media screen and (max-width: 767px) {
          display: block;
        }
      }
      .headline {
        margin-top: 18px;
        @media screen and (max-width: 1024px) {
          font-size: 18px;
        }
      }
      .description {
        color: darken(#fff, 15%);
        @media screen and (max-width: 1024px) {
          font-size: 16px;
        }
      }
      &:before {
        content: '';
        position: absolute;
        top: 24px;
        left: 106px;
        height: 12px;
        width: 12px;
        background: #89c997;
        border-radius: 100%;
        @media screen and (max-width: 767px) {
          top: 9px;
          left: -6px;
        }
      }
    }
  }
}
</style>
