<template>
    <footer>
        <p>Copyright © 2020 Ryota Iwasaki All Rights Reserved.</p>
    </footer>
</template>

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
