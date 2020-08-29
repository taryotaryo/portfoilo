<template>
  <div id="contact">
    <div class="inner">
      <section-title></section-title>
      <form class="contactForm" action="">
        <input type="text" placeholder="Name" name="name" required v-on:mouseover="mouseEnter()" v-on:mouseleave="mouseLeave()" v-on:focus="focus()" v-on:blur="blur()">
        <input type="email" placeholder="Email" name="email" required v-on:mouseover="mouseEnter()" v-on:mouseleave="mouseLeave()" v-on:focus="focus()" v-on:blur="blur()">
        <textarea placeholder="Message" name="message" required v-on:mouseover="mouseEnter()" v-on:mouseleave="mouseLeave()" v-on:focus="focus()" v-on:blur="blur()"></textarea>
        <input type="submit" value="Send">
      </form>
    </div>
  </div>
</template>

<script>
import { bus } from '../main.js'
import SectionTitle from '../components/SectionTitle.vue'
export default {
  components: {
    'section-title': SectionTitle
  },
  methods: {
    mouseEnter: function () {
      bus.$emit('bus-event-onInput')
    },
    mouseLeave: function () {
      bus.$emit('bus-event-off')
    },
    focus: function () {
      bus.$emit('bus-event-focusInput')
    },
    blur: function () {
      bus.$emit('bus-event-blurInput')
    }
  }
}
</script>

<style scoped lang="scss">
#contact {
  padding-bottom: 50px;
  .inner {
    width: 1600px;
    margin: 0 auto;
    .contactForm {
    width: 50%;
    margin: 6% auto;
    min-width: 9rem;
      input, textarea {
        width: 100%;
        max-width: 100%;
        margin: 0.5rem 0;
        padding: 0.5rem 1rem;
        background: #f9f9f9;
        border: none;
        border-radius: 0.3rem;
        color: darken(#f9f9f9, 40%);
        cursor: none;
          &[type=submit] {
            width: auto;
            background: #89c997;
            color: #fff;
          }
          &::placeholder {
            color: darken(#f9f9f9, 40%);
          }
      }
      textarea {
        height: 10rem;
      }
    }
  }
}

</style>
