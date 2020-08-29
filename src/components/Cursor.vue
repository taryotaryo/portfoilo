<template>
  <div>
    <p id="cursor" v-bind:style="cursorStyle"></p>
    <div id="stalker" v-bind:style="stalkerStyle">{{hoverMessage}}</div>
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
      cursorOpacity: 0,
      stalkerOpacity: 0,
      hoverMessage: '',
      isHover: false, // 要素上にホバーしているかどうか
      isHoverOnNavMenu: false, // ナビメニュー要素上にホバーしているかどうか
      isHoverOnLink: false, // 外部リンク遷移のある要素にホバーしているかどうか
      isHoverOnInput: false, // input要素にホバーしているかどうか
      isFocus: false
    }
  },
  computed: {
    cursorStyle: function () {
      if (this.isHover || this.isHoverOnLink || this.isHoverOnInput) {
        return {
          backgroundColor: 'transparent',
          opacity: this.cursorOpacity,
          top: this.mouseY + 'px',
          left: this.mouseX + 'px'
        }
      }
      return {
        opacity: this.cursorOpacity,
        top: this.mouseY + 'px',
        left: this.mouseX + 'px'
      }
    },
    stalkerStyle: function () {
      if (this.isHover) {
        return {
          zIndex: -1,
          opacity: this.stalkerOpacity,
          transform: 'translate(' + this.posX + 'px,' + this.posY + 'px) scale(2)'
        }
      }
      if (this.isHoverOnLink || this.isHoverOnInput) {
        return {
          zIndex: 2,
          opacity: this.stalkerOpacity,
          transform: 'translate(' + this.posX + 'px,' + this.posY + 'px) scale(2)',
          backgroundColor: '#ffefd5',
          color: '#89c997',
          fontSize: '14px',
          lineHeight: '40px',
          textAlign: 'center'
        }
      }
      if (this.isFocus) {
        return {
          transform: 'translate(' + this.posX + 'px,' + this.posY + 'px) scale(2)'
        }
      }
      return {
        opacity: this.stalkerOpacity,
        transform: 'translate(' + this.posX + 'px,' + this.posY + 'px)'
      }
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
      if (this.cursorOpacity === 0) {
        this.cursorOpacity = 1
      }
      setTimeout(function () {
        this.posX = `${this.mouseX - 20}`
        this.posY = `${this.mouseY - 24}`
        if (this.stalkerOpacity === 0) {
          this.stalkerOpacity = 1
        }
      }.bind(this), 100)
    },
    // ホバーの動作
    onNav: function () {
      this.isHover = true
      this.hoverMessage = ''
    },
    onView: function () {
      this.isHoverOnLink = true
      this.hoverMessage = 'view'
    },
    onInput: function () {
      this.isFocus = false
      this.isHoverOnInput = true
      this.hoverMessage = 'input'
    },
    off: function () {
      this.isHover = false
      this.isHoverOnLink = false
      this.isHoverOnInput = false
      this.isFocus = false
      this.hoverMessage = ''
    },
    // クリック時の動作
    focusInput: function () {
      this.isFocus = true
      this.isHoverOnInput = false
      this.hoverMessage = ''
    },
    blurInput: function () {
      this.isFocus = false
    }
  }
}
</script>

<style scoped lang="scss">
/*カーソル*/
#cursor{
  position: absolute;
  top: 0;
  left: 0;
  height: 8px;
  width: 8px;
  margin: -7px 0 0 -4px;
  background-color: #89c997;
  border-radius: 50%;
  opacity: 0;/*開いた瞬間非表示*/
  pointer-events: none;/*【重要】マウス直下に常に画像があるので、全てをクリックできなくなる。noneにして対応*/
  transition: transform 180ms;
  z-index: 3;/*一番手前に来るように*/
}
#stalker{
  position: absolute;
  height: 40px;
  width: 40px;
  z-index: 2;/*一番手前に来るように*/
  background-color: blue;
  background-size: contain;
  background-color: #ffefd5;
  border-radius: 50%;
  opacity: 0;/*開いた瞬間非表示*/
  pointer-events: none;/*【重要】マウス直下に常に画像があるので、全てをクリックできなくなる。noneにして対応*/
  transition: transform 180ms;
}
</style>
