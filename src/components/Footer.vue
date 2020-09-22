<template>
    <footer v-show="footerDisplay">
        <p>Copyright © 2020 Ryota Iwasaki All Rights Reserved.</p>
    </footer>
</template>

<script>
import { bus } from '../main.js'
export default {
  data: function () {
    return {
      footerDisplay: true
    }
  },
  created: function () {
    bus.$on('bus-event-focusInput', this.focus)
    bus.$on('bus-event-blurInput', this.blur)
  },
  methods: {
    focus: function () {
      const windowWidth = window.innerWidth
      if (windowWidth < 1024) {
        this.footerDisplay = false
      }
    },
    blur: function () {
      this.footerDisplay = true
    }
  }
}
</script>

<style scoped lang="scss">
footer {
  position: absolute;
  bottom: 10px;
  width: 100%;
  left: 50%;
  transform: translateX(-50%);
  @media screen and (max-width: 1024px) {
    bottom: 0;
  }
  p {
    color: #fff;
    text-align: center;
    @media screen and (max-width: 1024px) {
      font-size: 12px;
    }
  }
}
</style>
