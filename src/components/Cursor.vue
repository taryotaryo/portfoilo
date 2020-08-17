<template>
  <div>
    <!--body直下にカーソルとなる要素を配置-->
    <p id="cursor" v-bind:class="{ active: onViewActive }"
    v-bind:style="{
      opacity: opacityA,
      top: mouseY + 'px',
      left: mouseX + 'px'
      }">
    </p>
    <!--body直下にマウスストーカーとなる要素を配置-->
    <div v-if="!onViewActive" id="stalker"
    v-bind:style="{
      opacity: opacityB,
      transform: 'translate('+posX+'px,'+posY+'px)'
      }">
    </div>
    <div v-else-if="onViewActive" v-bind:class="{ active: onViewActive }" id="stalker"
    v-bind:style="{
      zIndex: zIndex,
      opacity: opacityB,
      transform: 'translate('+posX+'px,'+posY+'px) scale(2)'
      }">{{hoverMessage}}
    </div>
  </div>
</template>

<script>
import { bus } from '../main.js'
export default {
  data: function () {
    return {
      mouseX: 0,
      mouseY: 0,
      posX: 0,
      posY: 0,
      opacityA: 0,
      opacityB: 0,
      onViewActive: false,
      hoverMessage: '',
      zIndex: 2
    }
  },
  created: function () {
    bus.$on('bus-event-onView', this.onView)
    bus.$on('bus-event-offView', this.offView)
    bus.$on('bus-event-onNav', this.onNav)
    bus.$on('bus-event-offNav', this.offView)
  },
  methods: {
    getCursorCoordinate: function (event) {
      this.mouseX = event.pageX
      this.mouseY = event.pageY
      if (this.opacityA === 0) {
        this.opacityA = 1
      }
      setTimeout(function () {
        this.posX = `${this.mouseX - 20}`
        this.posY = `${this.mouseY - 24}`
        if (this.opacityB === 0) {
          this.opacityB = 1
        }
      }.bind(this), 100)
    },
    onView: function () {
      this.onViewActive = true
      this.hoverMessage = 'view'
      this.zIndex = 2
    },
    onNav: function () {
      this.onViewActive = true
      this.zIndex = -1
      this.hoverMessage = ''
    },
    offView: function () {
      this.onViewActive = false
    }
  }
}
</script>

<style>
/*カーソル*/
#cursor{
  position: relative;
  top: 0;
  left: 0;
  width: 8px;
  height: 8px;
  margin: -4px 0 0 -4px;
  border-radius: 50%;
  z-index: 3;/*一番手前に来るように*/
  pointer-events: none;/*【重要】マウス直下に常に画像があるので、全てをクリックできなくなる。noneにして対応*/
  transition: transform 0.1s;
  opacity: 0;/*開いた瞬間非表示*/
  background-color: #000;
}

#cursor.active{
  background-color: transparent;
}

#stalker{
  position: relative;
  background-color: blue;
  border-radius: 50%;
  width: 40px;
  height: 40px;
  z-index: 2;/*一番手前に来るように*/
  pointer-events: none;/*【重要】マウス直下に常に画像があるので、全てをクリックできなくなる。noneにして対応*/
  background-size: contain;
  background-color: #89c997;
  opacity: 0;/*開いた瞬間非表示*/
  transition: transform 0.1s;
}
#stalker.active{
  background-color: #ffefd5;
  color: #89c997;
  line-height: 40px;
  text-align: center;
  font-size: 14px;
}
</style>
