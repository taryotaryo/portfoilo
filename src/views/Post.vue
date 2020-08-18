<template>
  <div id="post">
    <div class="post-inner">
      <section-title></section-title>
      <div class="qiita-block">
        <h2 v-on:mouseover="mouseEnter2()" v-on:mouseleave="mouseLeave()">Qiita Posts</h2>
        <ul class="qiita-posts" >
          <li class="qiita-post" v-for="post in posts" v-bind:key="post" v-on:mouseover="mouseEnter()" v-on:mouseleave="mouseLeave()">
            <a v-bind:href="post['url']" target="_blank" rel="noopener noreferrer">
              <p class="qiita-post-title">{{ post['title'] }}</p>
              <span  class="qiita-post-tag" v-for="tag in post['tags']" v-bind:key="tag">{{ tag['name'] }}</span>
            </a>
          </li>
        </ul>
      </div>
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
    mouseEnter2: function () {
      bus.$emit('bus-event-onNav')
    },
    mouseLeave: function () {
      bus.$emit('bus-event-off')
    }
  }
}
</script>

<style lang="scss">
.post-inner {
  width: 1600px;
  margin: 0 auto;

  .qiita-block {
    h2{
      font-size: 30px;
    }
    .qiita-posts {
      display: flex;
      flex-wrap: wrap;
      justify-content: space-between;

      .qiita-post {
        width: 45%;
        background-color: #fff;
        border-radius: 5px;
        box-shadow: 0px 8px 8px #cccccc;
        list-style: none;
        margin-bottom: 30px;
        transition: 0.3s;

        &:hover {
          transform: translateY(-10px);
        }
        a {
          display: block;
          color: #696969;
          padding: 20px 20px;
          text-decoration: none;

          .qiita-post-title {
            font-size: 20px;
            font-weight: bold;
            margin-bottom: 5px;
          }

          .qiita-post-tag {
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
