<template>
    <header>
      <div class="header-inner">
        <router-link to="/"><div class="header-home" v-on:mouseover="mouseEnter()" v-on:mouseleave="mouseLeave()">Home</div></router-link>
        <div class="header-list">
            <ul class="header-lists">
                <router-link to="/about"><li v-on:mouseover="mouseEnter()" v-on:mouseleave="mouseLeave()">About</li></router-link>
                <router-link to="/work"><li v-on:mouseover="mouseEnter()" v-on:mouseleave="mouseLeave()">Works</li></router-link>
                <router-link to="/post"><li v-on:mouseover="mouseEnter()" v-on:mouseleave="mouseLeave()">Posts</li></router-link>
                <router-link to="/contact"><li v-on:mouseover="mouseEnter()" v-on:mouseleave="mouseLeave()">Contact</li></router-link>
            </ul>
        </div>
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

<style lang="scss">
header {
  font-weight: bold;
  font-size: 26px;

  a {
    color: #fff;
    text-decoration: none;
  }

  .header-home{
    line-height: 3;
    transition: 0.3s;
    &:hover {
      color: #89c997;
      transform: scale(1.5);
    }
  }

  .header-inner{
    display: flex;
    justify-content: space-between;
    margin: 0 auto;
    width: 90%;

    .header-lists {
      list-style: none;
      display: flex;

      li {
        cursor: none;
        border-radius: 5px;
        padding: 10px;
        margin-right: 50px;
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
