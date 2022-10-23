<template>
  <div>
    {{count}}
    <button @click="handleClick">btn</button>
  </div>
  <div>
    {{count2}}
    <button @click="handleClick2">btn2</button>
  </div>
  <div :style="`color:${sumColor}`">
    sum: {{sum}}
  </div>
</template>
<script>
import { ref, onMounted } from 'vue'
// const el = ref()
export default {

  setup() {
    const count = ref(0)

    // 返回值会暴露给模板和其他的选项式 API 钩子
    return {
      count
    }
  },

  data() {
    return {
      count2: 0,
      sumColor: ''
    }
  },

  computed: {
    sum () {
      return this.count + this.count2;
    }
  },

  watch: {
    sum (n, o) {
      console.log('watch', n, o);
      if (n % 2 === 0) {
        this.sumColor = 'red';
      } else {
        this.sumColor = 'blue';
      }
    }
  },

  methods: {
    handleClick (e) {
      console.log('handle click', e);
      this.count = this.count + 1;
    },
    handleClick2 (e) {
      console.log('handle click', e);
      this.count2 = this.count2 + 1;
    },
  },

  created () {
    console.log('created fetch', this.count) // 0
  },

  mounted() {
    console.log('mounted add', this.count) // 0
  }
}

// onMounted(() => {
//    // <div>
//   console.log('onMounted fn2 2222 ewewe', el);
// })

</script>