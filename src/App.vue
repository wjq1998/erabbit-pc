<template>
  <h1>当前求和为:{{ $store.state.sum }}</h1>
  <select v-model.number="n">
    <option value="1">1</option>
    <option value="2">2</option>
    <option value="3">3</option>
  </select>
  <button @click="increment">+</button>
  <button @click="decrement">-</button>
  <button @click="incrementOdd">当前求和为奇数再加</button>
  <button @click="incrementWait">等一等再加</button>
</template>

<script>
import { mapState } from 'vuex'
export default {
  data() {
    return {
      n: 1
    }
  },

  methods: {
    increment() {
      this.$store.dispatch('jia', this.n)
    },
    decrement() {
      this.$store.dispatch('jian', this.n)
    },
    incrementOdd() {
      if (this.$store.state.sum % 2) {
        this.increment()
      }
    },
    incrementWait() {
      setTimeout(() => {
        this.increment()
      }, 500)
    }
  },

  mounted() {
    const x = mapState({ sum: 'sum' })
    console.log(x)
  }
}
</script>

<style lang="less" scoped></style>
