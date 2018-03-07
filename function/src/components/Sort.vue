<template>
<div>
<h1>这个js排序算法对比</h1>
<p>Sort函数用时： 0.087158203125ms</p>
<p>SortByES6函数用时：0.261962890625ms</p>
</div>
</template>

<script>
export default {
  name: '排序组件',
  data () {
    return {
      arr: [12, 5, 10, 7, 1]
    }
  },
  methods: {
    // 利用两层for循环实现
    Sort (arr) {
      var j, d
      for (let i = 0; i < arr.length; i++) {
        for (j = 0; j < arr.length; j++) {
          if (arr[i] < arr[j]) {
            d = arr[j]
            arr[j] = arr[i]
            arr[i] = d
          }
        }
      }
      return arr
    },
    // 利用sort函数来实现
    SortByES6 (arr) {
      arr.sort((a, b) => a - b)
    }
  }
}
</script>

<style scope>

</style>
