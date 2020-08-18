<template>
  <div id="contact">
    <div class="contact-inner">
      <section-title></section-title>
      <form action="">
        <input type="text" placeholder="Name" name="name" required v-on:mouseover="mouseEnter()" v-on:mouseleave="mouseLeave()" v-on:focus="focus()">
        <input type="email" placeholder="Email" name="email" required v-on:mouseover="mouseEnter()" v-on:mouseleave="mouseLeave()" v-on:focus="focus()">
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
    }
  }
}
</script>

<style lang="scss">
$blue: #4784AD;

.contact-inner {
  width: 1600px;
  margin: 0 auto;

  form {
  width: 50%;
  margin: 6% auto;
  min-width: 9rem;

    input, textarea {
      width: 100%;
      max-width: 100%;
      border: none;
      margin: 0.5rem 0;
      padding: 0.5rem 1rem;
      border-radius: 0.3rem;
      background: #f9f9f9;
      color: darken(#f9f9f9, 40%);
      cursor: none;

        &[type=submit] {
          background: #89c997;
          color: #fff;
          width: auto;
        }

        &::placeholder {
          color: darken(#f9f9f9, 40%);
        }

        &.error {
          background: #AD4747;
          color: #fff;
          &::placeholder {
            color: darken(#AD4747, 60%);
          }
      }
    }

    textarea {
      height: 10rem;
    }
  }
}
</style>
