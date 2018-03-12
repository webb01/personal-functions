<template>
<div class="hello">
  <h1>{{ msg }}</h1>
  <h2>Essential Links</h2>
  <ul>
    <li>
      <a href="https://vuejs.org" target="_blank">
          Core Docs
        </a>
    </li>
    <li>
      <a href="https://forum.vuejs.org" target="_blank">
          Forum
        </a>
    </li>
    <li>
      <a href="https://chat.vuejs.org" target="_blank">
          Community Chat
        </a>
    </li>
    <li>
      <a href="https://twitter.com/vuejs" target="_blank">
          Twitter
        </a>
    </li>
    <br>
    <li>
      <a href="http://vuejs-templates.github.io/webpack/" target="_blank">
          Docs for This Template
        </a>
    </li>
  </ul>
  <h2>Ecosystem</h2>
  <ul>
    <li>
      <a href="http://router.vuejs.org/" target="_blank">
          vue-router
        </a>
    </li>
    <li>
      <a href="http://vuex.vuejs.org/" target="_blank">
          vuex
        </a>
    </li>
    <li>
      <a @click="jumpTo">
          Sort
        </a>
    </li>
    <li>
      <a>loading</a>
      <span class="dotting"></span>
    </li>
  </ul>
</div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      currentIndex: null,
      msg: 'Welcome to Your Vue.js App'
    }
  },
  methods: {
    // 路由跳转
    jumpTo () {
      this.$router.push({
        path: '/Sort'
      })
    },
    // 只能展开单个表格 （单个变量存储状态）
    showSingleList (item, index) {
      if (index === this.currentIndex) {
        this.currentIndex = -1
        return
      }
      this.currentIndex = index
      // console.log('oooooKKKKK', item)
      // this.$set(item, "toggleShow", !item.listShow);
      item.listShow = !item.listShow
    },
    // 展开多个表格（通过set来添加没项单独的展开标识）
    showList (item) {
      // if(index == this.currentIndex) {
      //   this.currentIndex = -1
      //   return
      // }
      // this.currentIndex = index
      this.$set(item, 'toggleShow', !item.listShow)
      item.listShow = !item.listShow
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
/*纯css制作的loading*/

.dotting {
  display: inline-block;
  width: 10px;
  min-height: 2px;
  padding-right: 2px;
  border-left: 2px solid currentColor;
  border-right: 2px solid currentColor;
  background-color: currentColor;
  background-clip: content-box;
  box-sizing: border-box;
  animation: dot 1s infinite step-start both;
}

.dotting:before {
  content: "...";
}


/* IE8 */

.dotting::before {
  content: "";
}

:root .dotting {
  margin-left: 2px;
  padding-left: 2px;
}


/* IE9+ */

@keyframes dot {
  25% {
    border-color: transparent;
    background-color: transparent;
  }
  /* 0个点 */
  50% {
    border-right-color: transparent;
    background-color: transparent;
  }
  /* 1个点 */
  75% {
    border-right-color: transparent;
  }
  /* 2个点 */
}

h1,
h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
