<!-- https://juejin.cn/post/6985493062432587813 -->
<template>
  <div>
    <!-- 功能一模板 -->
    <button @click="show">显示</button>
    <button @click="hide">隐藏</button>
    <div class="box" v-if="showDiv">一个被控制显隐的div</div>
  </div>
  <div>
    <!-- 功能二模板 -->
    <button @click="changeRed">红色</button>
    <button @click="changeBlue">蓝色</button>
    <div class="box" :style="`color:${fontColor}`">一个被控制字体颜色的的div</div>
  </div>
</template>
<style scoped>
.box {
  /* width: 200px;
  height: 200px;
  line-height: 200px;
  background-color: cornflowerblue;
  text-align: center; */
}
</style>
<script>
import { ref } from 'vue'
export default {
  name: 'Fn1',
  setup() {
    // 功能一
    const showDiv = ref(true)
    function show() {
      showDiv.value = true
    }
    function hide() {
      showDiv.value = false
    }

    // 功能二
    const fontColor = ref('')
    function changeRed() {
      fontColor.value = 'red'
    }
    function changeBlue() {
      fontColor.value = 'blue'
    }
    return {
      showDiv, show, hide,
      fontColor, changeRed, changeBlue
    }
  }
}
</script>