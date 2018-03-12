<template>
<div class="page">
 <div class="only-x-center">只是水平居中</div>
<h1>这个js排序算法对比</h1>
<p>sort函数用时： 0.087158203125ms</p>
<p>sortByES6函数用时：0.261962890625ms</p>

<div>
  冒泡排序耗时26000ms左右
  选择排序耗时5800ms左右
  插入排序耗时10600ms左右
  归并排序耗时80-100ms
  快速排序
  cutoff==5--->30-50ms
  cutoff==10 --->30-60ms
  cutoff==50 ---->40-50ms
  cutoff==3效果不错--->30-50ms，30ms出现的机会很多
  cutoff==0时（即不在分割长度短的时候转为插入排序），效果依然不错，30-50ms，30ms出现的很多
  堆排序耗时120-140ms
  JavaScript提供的原生排序耗时55-70ms
  <p>快速排序效率最高，cutoff取3效果最好（没有悬念）</p>
<p>原生排序竟然是第二快的排序算法！</p>
</div>


        <!-- 垂直水平居中的几种方案 -->
<!-- 不知道宽高的情况 定位 + transform ; 适用于 子盒子 宽高不定时 -->
<div style="position: relative">
<div class="layout" style="width: 100px;height: 50px;background-color: tan"></div>
</div>
<!-- 不知道宽高 table-cell布局 -->
<div class="table-cell">
  <div class="cell"></div>
</div>
<!-- 不知道宽高  flex布局 -->
<div class="flex">
  <div class="flex-1"></div>
</div>
</div>
</template>

<script>
export default {
  name: 'Sort',
  data () {
    return {
      arr: [12, 5, 10, 7, 1]
    }
  },
  methods: {
    // 交换两个数组项的位子
    arrExchange (a, b, arr) {
      let temp = arr[a]
      arr[a] = arr[b]
      arr[b] = temp
    },

    // 利用两层for循环实现(冒泡排序)
    sort (arr) {
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
    // 利用原生js的sort函数来实现（数据量很大时效率也可以）
    sortByES6 (arr) {
      arr.sort((a, b) => a - b)
    },
    // 插入排序  (适合数据量较小的排序 k级别)
    insertSort (elements) {
      // 假设第0个元素是一个有序的数列，第1个以后的是无序的序列，
      // 所以从第1个元素开始将无序数列的元素插入到有序数列中
      for (var i = 1; i < elements.length; i++) {
        // 升序
        if (elements[i] < elements[i - 1]) {
          // 取出无序数列中的第i个作为被插入元素
          var guard = elements[i]
          // 记住有序数列的最后一个位置，并且将有序数列位置扩大一个
          var j = i - 1
          elements[i] = elements[j]

          // 比大小，找到被插入元素所在的位置
          while (j >= 0 && guard < elements[j]) {
            elements[j + 1] = elements[j]
            j--
          }

          // 插入
          elements[j + 1] = guard
        }
      }
      return elements
    },
    // 数据量很大时 效率很高（K+级别推荐）
    quickSort (arr) {
      // 如果数组<=1,则直接返回
      if (arr.length <= 1) {
        return arr
      }
      var pivotIndex = Math.floor(arr.length / 2)
      // 找基准，并把基准从原数组删除
      var pivot = arr.splice(pivotIndex, 1)[0]
      // 定义左右数组
      var left = []
      var right = []

      // 比基准小的放在left，比基准大的放在right
      for (var i = 0; i < arr.length; i++) {
        if (arr[i] <= pivot) {
          left.push(arr[i])
        } else {
          right.push(arr[i])
        }
      }
      // 递归
      return this.quickSort(left).concat([pivot], this.quickSort(right))
    }
  }
}
</script>

<style lang="scss">
.page {
  font-size: 16px;
}
.only-x-center {
  margin-left: 50%;
  transform: translateX(-50%);
  width: 100px;
  height: 50px;
  background: coral;
}
.layout {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%)
}
.table-cell {
  display: table-cell;
  vertical-align: middle;
  width: 100vw;
  height: 300px;
  background-color: greenyellow;
  .cell {
    margin: 0 auto;
    width: 100px;
    height: 100px;
    background-color: hotpink;
  }
}
.flex {
  display: flex; // flex布局
  align-items: center; // 垂直居中
  justify-content: center; // 水平居中
  width: 100vw;
  height: 300px;
  background: cornflowerblue;
  .flex-1 {
    width: 200px;
    height: 200px;
    background: orange;
  }
}
</style>
