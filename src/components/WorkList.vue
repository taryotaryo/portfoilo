<template>
  <div>
    <div class="worklist" v-for="workList in workLists" v-bind:key="workList" v-on:mouseover="mouseEnter()" v-on:mouseleave="mouseLeave()">
      <img v-bind:src="workList.image" alt="">
      <!-- <span v-for="tech in workList.techs" v-bind:key="tech">{{ tech }}</span> -->
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
          image: require('../assets/ta-ryo_blog.png')
          // techs: ['HTML', 'SCSS', 'jQuery', 'WordPress', 'Xserver']
        },
        {
          image: require('../assets/portfolio.png')
          // techs: ['HTML', 'CSS', 'hover.css', 'jQuery', 'Xserver']
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
.worklist {
  box-shadow: 0px 8px 8px #cccccc;
  cursor: none;
  margin: 0 auto;
  margin-bottom: 30px;
  overflow: hidden;
  text-align: center;
  transition: 0.5s;
  width: 800px;
    &:hover {
      border-radius: 30px;
      box-shadow: none;
    }
    img {
      transition: 0.5s;
      width: 800px;
      &:hover {
      transform: scale(1.1, 1.1);
    }
    }
}
</style>
