<template>
  <div id="post">
    <div class="inner">
      <section-title></section-title>
      <ul class="qiitaPosts" >
        <li class="qiitaPost" v-for="post in posts" v-bind:key="post" v-on:mouseover="mouseEnter()" v-on:mouseleave="mouseLeave()">
          <a v-bind:href="post['url']" target="_blank" rel="noopener noreferrer">
            <p class="title">{{ post['title'] }}</p>
            <span  class="tag" v-for="tag in post['tags']" v-bind:key="tag">{{ tag['name'] }}</span>
          </a>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
import { bus } from '../main.js'
import axios from 'axios'
import SectionTitle from '../components/SectionTitle.vue'
export default {
  name: 'post',
  data: function () {
    return {
      posts: []
    }
  },
  components: {
    'section-title': SectionTitle
  },
  mounted: function () {
    this.getPost()
  },
  methods: {
    getPost: function () {
      axios.get('https://qiita.com/api/v2/users/KUMA_TR/items')
        .then((res) => {
          this.posts = res.data
        })
    },
    mouseEnter: function () {
      bus.$emit('bus-event-onView')
    },
    mouseLeave: function () {
      bus.$emit('bus-event-off')
    }
  }
}
</script>

<style scoped lang="scss">
#post {
  padding-bottom: 100px;
  .inner {
    width: 1600px;
    margin: 0 auto;
    .qiitaPosts {
      display: flex;
      flex-wrap: wrap;
      justify-content: space-between;
      .qiitaPost {
        width: 45%;
        margin-bottom: 30px;
        background-color: #fff;
        border-radius: 5px;
        list-style: none;
        transition: 0.3s;

        &:hover {
          transform: translateY(-10px);
        }
        a {
          display: block;
          padding: 20px 20px;
          color: #696969;
          text-decoration: none;
          .title {
            margin-bottom: 5px;
            font-size: 20px;
            font-weight: bold;
          }
          .tag {
            margin-right: 5px;
            padding: 5px 10px 5px 10px;
            background-color: #89c997;
            border-radius: 5px;
            color: #fff;
            font-weight: bold;
          }
        }
      }
    }
  }
}
</style>
