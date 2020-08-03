<template>
  <div id="home">
      <div class="home-container">
        <h1 class="home-message"><span>W</span>elcome <span>T</span>o <span>M</span>y <span>P</span>orofolio</h1>
      </div>
  </div>
</template>

<script>
// @ is an alias to /src

export default {
}
</script>

<style lang="scss">
#home {
  .home-container {
    padding-top: 330px;
    padding-bottom: 330px;
    .home-message{
      font-size: 100px;
      display: inline;
      position: relative;

        &:before, &:after {
          animation-name: border-moving;
          animation-duration: 10s;
          animation-timing-function: linear;
          animation-iteration-count: infinite;
          animation-direction: alternate;
        }

        @keyframes border-moving {
          from {
            width: 0%;
          }
          to {
            width: 100%;
          }
        }

        &:before {
          content: '';
          background-color: #fff;
          position: absolute;
          top: 0;
          left: 0;
          height: 3px;
        }

        &:after {
          content: '';
          background-color: #fff;
          position: absolute;
          bottom: 0;
          right: 0;
          height: 3px;
        }

      span{
        color: #89c997;
      }
    }
  }
}

</style>
