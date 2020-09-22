<template>
<header>
  <div class="inner">
    <router-link to="/"><div class="home" v-on:mouseover="mouseEnter()" v-on:mouseleave="mouseLeave()">Home</div></router-link>
    <nav>
      <ul class="navMenu">
        <router-link to="/about"><li class="navList" v-on:mouseover="mouseEnter()" v-on:mouseleave="mouseLeave()">About</li></router-link>
        <router-link to="/work"><li class="navList" v-on:mouseover="mouseEnter()" v-on:mouseleave="mouseLeave()">Works</li></router-link>
        <router-link to="/post"><li class="navList" v-on:mouseover="mouseEnter()" v-on:mouseleave="mouseLeave()">Posts</li></router-link>
        <router-link to="/contact"><li class="navList" v-on:mouseover="mouseEnter()" v-on:mouseleave="mouseLeave()">Contact</li></router-link>
      </ul>
    </nav>
    <div id="Hamburger" class="hamburger" v-on:click="spheaderIn()" v-show="hamburgerDisplay">
      <div class="bar"></div>
      <div class="bar"></div>
      <div class="bar"></div>
      <p class="text">MENU</p>
    </div>
  </div>
  <!-- スマートフォン表示 -->
  <nav id="navMenu-sp" v-on:touchmove="spheaderOut()">
    <ul>
      <router-link to="/" class="item1"><li class="navList-sp" v-on:touchend="spheaderOut()">Home</li></router-link>
      <router-link to="/about" class="item2"><li class="navList-sp item2" v-on:touchend="spheaderOut()">About</li></router-link>
      <router-link to="/work" class="item3"><li class="navList-sp item3" v-on:touchend="spheaderOut()">Works</li></router-link>
      <router-link to="/post" class="item4"><li class="navList-sp item4" v-on:touchend="spheaderOut()">Posts</li></router-link>
      <router-link to="/contact" class="item5"><li class="navList-sp item5" v-on:touchend="spheaderOut()">Contact</li></router-link>
    </ul>
  </nav>
</header>
</template>

<script>
import { bus } from '../main.js'
export default {
  data: function () {
    return {
      hamburgerDisplay: true
    }
  },
  created: function () {
    bus.$on('bus-event-focusInput', this.focus)
    bus.$on('bus-event-blurInput', this.blur)
  },
  methods: {
    mouseEnter: function () {
      bus.$emit('bus-event-onNav')
    },
    mouseLeave: function () {
      bus.$emit('bus-event-off')
    },
    spheaderIn: function () {
      document.getElementById('navMenu-sp').classList.add('in')
    },
    spheaderOut: function () {
      document.getElementById('navMenu-sp').classList.remove('in')
    },
    focus: function () {
      const windowWidth = window.innerWidth
      if (windowWidth < 1024) {
        this.hamburgerDisplay = false
      }
    },
    blur: function () {
      this.hamburgerDisplay = true
    }
  }
}
</script>

<style scoped lang="scss">
header {
  position: absolute;
  top: 0;
  width: 100%;
  margin: 0 auto;
  font-size: 26px;
  font-weight: bold;
  a {
    color: #fff;
    cursor: none;
    text-decoration: none;
  }
  .inner{
    display: flex;
    align-items: center;
    justify-content: space-between;
    margin: 0 auto;
    width: 90%;
    height: 140px;

    .home{
      transition: 0.3s;
      line-height: 140px;
      @media screen and (max-width: 1024px) {
        display: none;
      }
      &:hover {
        color: #89c997;
        transform: scale(1.5);
      }
    }
    .navMenu {
      display: flex;
      margin: 0;
      list-style: none;
      @media screen and (max-width: 1024px) {
        display: none;
      }
      .navList {
        margin-right: 50px;
        border-radius: 5px;
        line-height: 140px;
        transition: 0.3s;
        &:nth-of-type(4){
          margin-right: 0px;
        }
        &:hover {
          color: #89c997;
          transform: scale(1.5);
        }
      }
    }
    .hamburger {
      position: fixed;
      bottom: 20px;
      right: 20px;
      display: none;
      height: auto;
      width: 32px;
      transition: 2s;
      z-index: 10;
      @media screen and (max-width: 1024px) {
        display: block;
      }
      .bar {
        background-color: #fafafa;
        border-radius: 20px;
        padding: 2px 5px;
        margin: 4px 0;
        transition: 1s;
      }
      .text {
        text-align: center;
        font-size: 10px;
        font-weight: bold;
      }
      .black {
        background-color: #111;
      }
    }
  }
  #navMenu-sp {
    position: fixed;
    top: 0;
    left: -100%;
    height: 100vh;
    width: 100%;
    background: #fff;
    text-align: center;
    transition: .7s;
    z-index: 12;
    ul {
      display: flex;
      align-content: center;
      flex-wrap: wrap;
      justify-content: center;
      height: 100%;
      .item1 {
        flex-basis: 35%;
        order: 5;
      }
      .item2 {
        flex-basis: 35%;
      }
      .item3 {
        flex-basis: 35%;
      }
      .item4 {
        flex-basis: 35%;
      }
      .item5 {
        flex-basis: 35%;
      }
      .navList-sp {
        height: 180px;
        width: 180px;
        margin: 0 auto;
        margin-bottom: 50px;
        border: 1px solid #111;
        border-radius: 50%;
        color: #111;
        list-style: none;
        line-height: 180px;
        transition: 0.2s;
        &:active {
          background-color: #89c997;
          border: none;
          color: #fff;
          transform: translateY(-20px);
        }
        @media screen and (max-width: 767px) {
          height: 120px;
          width: 120px;
          line-height: 120px;
        }
      }
    }
  }
  .in{
  transform: translateX(100%);
  }
}
</style>
