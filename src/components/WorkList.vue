<template>
  <figure class="content">
    <a class="videoSide" v-bind:href="workinfo.url" v-on:mouseover="mouseEnter()" v-on:mouseleave="mouseLeave()">
      <video class="workVideo" v-bind:src="workinfo.image" loop autoplay muted></video>
    </a>
    <figcaption class="description">
      <h3 class="headline"><span class="icon"><font-awesome-icon icon="caret-square-right" /></span>概要</h3>
      <ul class="summary">
        <li class="list" v-for="summary in workinfo.summaries" v-bind:key="summary">{{ summary }}</li>
      </ul>
      <h3 class="headline"><span class="icon"><font-awesome-icon icon="laptop-code" /></span>使用技術・デプロイ</h3>
      <span class="tech" v-for="tech in workinfo.techs" v-bind:key="tech">{{ tech }}</span>
      <h3 class="headline"><span class="icon"><font-awesome-icon icon="lightbulb" /></span>こだわりポイント</h3>
      <ul class="commitment">
        <li class="list" v-for="commitment in workinfo.commitments" v-bind:key="commitment">{{ commitment }}</li>
      </ul>
    </figcaption>
  </figure>
</template>

<script>
import { bus } from '../main.js'
export default {
  name: 'workList',
  props: [
    'workinfo'
  ],
  methods: {
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
.content {
  display: flex;
  align-items: flex-start;
  width: 80%;
  margin-bottom: 80px;
  padding-top: 80px;
  padding-bottom: 80px;
  @media screen and (max-width: 1024px) {
    display: block;
    margin-right: auto;
    margin-left: auto;
    margin-bottom: 0px;
    padding-top: 40px;
    padding-bottom: 40px;
  }
  @media screen and (max-width: 767px) {
    width: 90%;
    padding-top: 30px;
    padding-bottom: 30px;
  }

  .videoSide {
    width: 40%;
    height: auto;
    background: #8735b0;
    text-align: left;
    @media screen and (max-width: 1024px) {
      width: 100%;
      background: transparent;
    }
    .workVideo {
      width: 100%;
      opacity: 1;
      transition: 0.3s;
      vertical-align: bottom;
      &:hover {
        opacity: .8;
      }
    }
  }
  .description {
    margin-left: 50px;
    width: 50%;
    @media screen and (max-width: 1024px) {
      width: 100%;
      margin-left: 0px;
    }
    .headline {
      font-size: 20px;
      margin-top: 20px;
      margin-bottom: 20px;
      @media screen and (max-width: 1024px) {
        font-size: 18px;
        margin-top: 18px;
        margin-bottom: 18px;
      }
    }
    .list{
      color: darken(#fff, 15%);
      font-size: 18px;
      line-height: 1.6rem;
      margin-left: 2em;
      @media screen and (max-width: 1024px) {
        font-size: 16px;
      }
    }
    .icon {
      margin-right: 1rem;
    }
    .tech {
      margin-right: 8px;
      margin-bottom: 8px;
      padding: 8px 10px;
      color: darken(#fff, 15%);
      @media screen and (max-width: 1024px) {
        font-size: 16px;
      }
      @media screen and (max-width: 1024px) {
        padding: 8px 2px;
      }
    }
  }
}
</style>
