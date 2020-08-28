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
      </div>
    </header>
</template>

<script>
import { bus } from '../main.js'
export default {
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
header {
  position: absolute;
  top: 0;
  height: 140px;
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
    justify-content: space-between;
    margin: 0 auto;
    width: 90%;
    .home{
      transition: 0.3s;
      line-height: 140px;
      &:hover {
        color: #89c997;
        transform: scale(1.5);
      }
    }
    .navMenu {
      display: flex;
      margin: 0;
      list-style: none;
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
  }
}
</style>
