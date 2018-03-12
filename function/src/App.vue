<template>
  <div id="app">
    <img src="./assets/image/logo.png">
    <div class="t1"></div>
    <div class="t2"></div>
    <router-view/>
  </div>
</template>

<script>
export default {
  name: 'App'
}
</script>

<style lang="scss">
@import './assets/styles/base.scss';

html,body {
  margin: 0;
  font-size: vw(10)
}

// // 根元素大小使用 vw 单位
// $vm_design: 750;
// html {
//     font-size: ($vm_fontsize / ($vm_design / 2)) * 100vw;
//     // 同时，通过Media Queries 限制根元素最大最小值
//     @media screen and (max-width: 320px) {
//         font-size: 15px;
//     }
//     @media screen and (min-width: 540px) {
//         font-size: 18px;
//     }
// }
// // body 也增加最大最小宽度限制，避免默认100%宽度的 block 元素跟随 body 而过大过小
// body {
//     max-width: 540px;
//     min-width: 320px;
// }

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  // margin-top: vw(20);
  /* margin-bottom: vw(2); */
}
.t1 {
  width: vw(375);
  height: 20px;
  background-color: pink;
}
.t2 {
  width: vw(300);
  height: 20px;
  background-color: green;
}
</style>
