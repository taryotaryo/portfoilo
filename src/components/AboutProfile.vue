<template>
<div class="content">
  <div class="introduction">
    <h3 class="name">Ryota Iwasaki</h3>
    <p class="description">
      都内のSES企業でチームリーダーとして働いています。人に使ってもらえるものを自分で作りたいと思い、
      2019年12月から独学でプログラミング学習を開始しました。現在はフロントエンドエンジニアを目指して転職活動中です。
    </p>
    <div class="like">
      <h3 class="headline">Likes</h3>
      <p class="description"><span class="space" v-for="(like) in likes" v-bind:key="like">{{ like }}</span></p>
    </div>
    <div class="account">
      <h3 class="headline">Acounts</h3>
      <a class=icon href="https://github.com/taryotaryo" v-on:mouseover="mouseEnter()" v-on:mouseleave="mouseLeave()"><font-awesome-icon v-bind:icon="['fab', 'github']" /></a>
      <a class=icon href="https://qiita.com/KUMA_TR" v-on:mouseover="mouseEnter()" v-on:mouseleave="mouseLeave()"><font-awesome-icon v-bind:icon="['fab', 'quora']" /></a>
      <a class=icon href="https://twitter.com/KUMA90473134" v-on:mouseover="mouseEnter()" v-on:mouseleave="mouseLeave()"><font-awesome-icon v-bind:icon="['fab', 'twitter']" /></a>
      <a class=icon href="mailto:yarot.wsaiaik@outlook.jp" v-on:mouseover="mouseEnter()" v-on:mouseleave="mouseLeave()"><font-awesome-icon v-bind:icon="['fas', 'envelope']" /></a>
    </div>
  </div>
  <figure class="profileImage">
    <img src="../assets/profile.png" alt="プロフィール画像">
  </figure>
</div>
</template>

<script>
import { bus } from '../main.js'
export default {
  data: function () {
    return {
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
// 共通Class
.headline {
  margin-bottom: 20px;
  font-size: 20px;
}
.description {
  color: darken(#fff, 15%);
  letter-spacing: 0.1rem;
}
.content {
  margin-top: 40px;
  .introduction {
    width: 50%;
    @media screen and (max-width: 1024px) {
      width: 90%;
      margin: 0 auto;
    }
    .name {
      margin-bottom: 30px;
      font-size: 40px;
      @media screen and (max-width: 1024px) {
        margin-bottom: 20px;
        font-size: 32px;
      }
    }
  }
  .like {
    margin-top: 20px;
    .space {
      margin-right: 10px;
    }
    }
    .account {
    margin-top: 20px;
    .icon {
        display: inline-block;
        margin-right: 50px;
        position: relative;
        color: #fff;
        font-size: 30px;
        text-decoration: none;
        transition: .3s;
        @media screen and (max-width: 767px) {
          width: 25%;
          margin-right: 0px;
          font-size: 50px;
        }
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
.profileImage {
    text-align: right;
    margin-right: 300px;
    @media screen and (max-width: 1024px) {
      text-align: center;
      margin-top: 40px;
      margin-right: 0px;
    }
    img {
    width: 200px;
      @media screen and (max-width: 767px) {
        width: 150px;
      }
    }
}
</style>
