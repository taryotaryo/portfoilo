<template>
    <header>
      <div class="header-inner">
        <div class="header-home">Home</div>
        <div class="header-list">
            <ul class="header-lists">
                <li>About</li>
                <li>Works</li>
                <li>Posts</li>
                <li>Contact</li>
            </ul>
        </div>
      </div>
    </header>
</template>

<script>

export default {
}

</script>

<style lang="scss">
header {
  font-weight: bold;
  font-size: 26px;

  .header-home{
    line-height: 3;
      &:hover {
      color: #89c997;
    }
  }

  .header-inner{
    display: flex;
    justify-content: space-between;
    margin: 0 auto;
    width: 90%;

    .header-lists {
      list-style: none;
      display: flex;

      li {
        cursor: pointer;
        border-radius: 5px;
        padding: 10px;
        margin-right: 50px;
          &:nth-of-type(4){
            margin-right: 0px;
          }
          &:hover {
            color: #89c997;
            background-color: #fff;
          }
      }
    }
  }

}

</style>
