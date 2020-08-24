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
      transform: 'translate('+posX+'px,'+posY+'px)'+scale
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
      zIndex: 2,
      scale: 'scale(2)'
    }
  },
  created: function () {
    // ホバー/非ホバー時のトリガー
    bus.$on('bus-event-onNav', this.onNav) // 拡大のみ
    bus.$on('bus-event-onView', this.onView) // 拡大 + 文字「view」
    bus.$on('bus-event-onInput', this.onInput) // 拡大 + 文字「input」
    bus.$on('bus-event-off', this.off) // 縮小(元に戻る)
    // フォーカス/非フォーカス時のトリガー
    bus.$on('bus-event-focusInput', this.focusInput) // 縮小して消える
    bus.$on('bus-event-blurInput', this.blurInput) // 縮小(元に戻る)
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
    // ホバーの動作
    onNav: function () {
      this.onViewActive = true
      this.scale = 'scale(2)'
      this.hoverMessage = ''
      this.zIndex = -1
    },
    onView: function () {
      this.onViewActive = true
      this.scale = 'scale(2)'
      this.hoverMessage = 'view'
      this.zIndex = 2
    },
    onInput: function () {
      this.onViewActive = true
      this.scale = 'scale(2)'
      this.hoverMessage = 'input'
      this.zIndex = 2
    },
    off: function () {
      this.onViewActive = false
    },
    // クリック時の動作
    focusInput: function () {
      this.scale = 'scale(0)'
    }
  }
}
</script>

<style>
/*カーソル*/
#cursor{
  position: absolute;
  top: 0;
  left: 0;
  width: 8px;
  height: 8px;
  margin: -7px 0 0 -4px;
  border-radius: 50%;
  z-index: 3;/*一番手前に来るように*/
  pointer-events: none;/*【重要】マウス直下に常に画像があるので、全てをクリックできなくなる。noneにして対応*/
  transition: transform 180ms;
  opacity: 0;/*開いた瞬間非表示*/
  background-color: #000;
}

#cursor.active{
  background-color: transparent;
}

#stalker{
  position: absolute;
  background-color: blue;
  border-radius: 50%;
  width: 40px;
  height: 40px;
  z-index: 2;/*一番手前に来るように*/
  pointer-events: none;/*【重要】マウス直下に常に画像があるので、全てをクリックできなくなる。noneにして対応*/
  background-size: contain;
  background-color: #ffefd5;
  opacity: 0;/*開いた瞬間非表示*/
  transition: transform 180ms;
}
#stalker.active{
  background-color: #ffefd5;
  color: #89c997;
  line-height: 40px;
  text-align: center;
  font-size: 14px;
}
</style>
