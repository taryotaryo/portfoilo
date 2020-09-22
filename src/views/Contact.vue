<template>
<div id="contact">
    <div class="inner">
      <section-title></section-title>
      <form class="contactForm" action="" v-on:submit="checkForm" method="POST" data-netlify="true">
        <div v-if="errors.length">
          <p v-for="error in errors" v-bind:key="error">{{ error }}</p>
        </div>
        <input
        id="name"
        type="text"
        placeholder="Name"
        name="name"
        v-model="name"
        v-on:mouseover="mouseEnter()"
        v-on:mouseleave="mouseLeave()"
        v-on:focus="focus()"
        v-on:blur="blur()"
        >
        <input
        id="email"
        placeholder="Email"
        name="email"
        v-model="email"
        v-on:mouseover="mouseEnter()"
        v-on:mouseleave="mouseLeave()"
        v-on:focus="focus()"
        v-on:blur="blur()"
        >
        <textarea
        id="message"
        placeholder="Message"
        name="message"
        v-model="contents"
        v-on:mouseover="mouseEnter()"
        v-on:mouseleave="mouseLeave()"
        v-on:focus="focus()"
        v-on:blur="blur()">
        </textarea>
        <input
        type="submit"
        value="Send"
        v-on:mouseover="mouseEnterSend()"
        v-on:mouseleave="mouseLeave()"
        >
      </form>
    </div>
</div>
</template>

<script>
import { bus } from '../main.js'
import SectionTitle from '../components/SectionTitle.vue'
export default {
  data: function () {
    return {
      errors: [],
      name: '',
      email: '',
      contents: ''
    }
  },
  components: {
    'section-title': SectionTitle
  },
  methods: {
    checkForm: function (e) {
      if (this.name && this.email && this.contents && this.checkString(this.email)) {
        return true
      }
      this.errors = []
      if (!this.name) {
        this.errors.push('※名前を入力してください')
      }
      if (!this.email) {
        this.errors.push('※メールアドレスを入力してください')
      }
      if (this.email && !this.checkString(this.email)) {
        this.errors.push('※正しいメールアドレスを入力してください')
      }
      if (!this.contents) {
        this.errors.push('※メッセージを入力してください')
      }
      e.preventDefault()
    },
    checkString: function (inputdata) {
      const reg = /^[A-Za-z0-9]{1}[A-Za-z0-9_.-]*@{1}[A-Za-z0-9_.-]{1,}\.[A-Za-z0-9]{1,}$/
      return reg.test(inputdata)
    },
    mouseEnter: function () {
      bus.$emit('bus-event-onInput')
    },
    mouseEnterSend: function () {
      bus.$emit('bus-event-onSend')
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
  height: 100vh;
  .inner {
    width: 90%;
    margin: 0 auto;
    .contactForm {
    width: 50%;
    margin: 6% auto;
    min-width: 9rem;
    @media screen and (max-width: 1024px) {
      width: 80%;
    }
    @media screen and (max-width: 767px) {
      width: 100%;
    }
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
        @media screen and (max-width: 1024px) {
          margin: 0.8rem 0;
          padding: 1rem 1rem;
          background: #f9f9f9;
          border: none;
          border-radius: 0.3rem;
          color: darken(#f9f9f9, 40%);
          cursor: none;
        }
          &[type=submit] {
            width: auto;
            background: #89c997;
            color: #fff;
            @media screen and (max-width: 1024px) {
              width: 100%;
            }
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
