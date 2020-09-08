<template>
  <div id="home">
      <div class="wrapper">
        <h1 class="message" v-on:mouseover="mouseEnter()" v-on:mouseleave="mouseLeave()">
          <span class="mintgreen">W</span>elcome <span class="mintgreen">T</span>o <span class="mintgreen">M</span>y <span class="mintgreen">P</span>ortfolio
        </h1>
      </div>
  </div>
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
#home {
  height: 100vh;
  .wrapper {
    position: absolute;
    top: 50%;
    left: 50%;
    width: 100%;
    transform: translate(-50%, -50%);
    text-align: center;
    .message{
      font-size: 100px;
      display: inline;
      position: relative;
      @media screen and (max-width: 1024px) {
        font-size: 60px;
      }

        &:before, &:after {
          animation-name: border-moving;
          animation-duration: 10s;
          animation-timing-function: linear;
          animation-iteration-count: infinite;
          animation-direction: alternate;
        }

        @keyframes border-moving {
          from {
            width: 0%;
          }
          to {
            width: 100%;
          }
        }

        &:before {
          content: '';
          background-color: #fff;
          position: absolute;
          top: 0;
          left: 0;
          height: 3px;
        }

        &:after {
          content: '';
          background-color: #fff;
          position: absolute;
          bottom: 0;
          right: 0;
          height: 3px;
        }

      .mintgreen{
        color: #89c997;
      }
    }
  }
}

</style>
