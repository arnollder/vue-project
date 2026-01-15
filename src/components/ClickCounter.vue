<template>
  <div>
    <div class="counter">
      <h2 :style="counterTitleColor">{{ title }}</h2>
      <div>Count: {{ count }}</div>
      <div>Double count {{ doubleCount }}</div>
    </div>
    <button @click="increment">Increment++</button>
    <button @click="decrement">Decrement--</button>
    <button @click="reset">Reset</button>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
  data() {
    return {
      count: 0,
    }
  },
  props: {
    title: {
      type: String,
      default: 'Default counter title',
    },
  },
  emits: ['decrement'],
  computed: {
    doubleCount() {
      return this.count * 2
    },
    counterTitleColor() {
      return { color: this.count > 5 ? 'red' : 'black' }
    },
  },
  methods: {
    showDecrement() {
      console.log('decrement')
    },
    increment() {
      this.count++
    },

    decrement() {
        // this.showDecrement()
        this.count--
        this.$emit('decrement', this.count)
    },
    reset() {
      this.count = 0
    },
  },
  watch: {
    count: {
      handler(newValue, oldValue) {
        console.log('newValue', newValue)
        console.log('oldValue', oldValue)
        // if (newValue === 0) alert('Значение равно 0!')
      },
      immediate: true,
      deep: true,
    },
  },
})
</script>

<style scoped>
/* button {
  padding: 5px 10px;
  border: none;
  background-color: rgb(74, 226, 74);
  border-radius: 5px;
  margin-right: 5px;
  cursor: pointer;
}
button:hover {
  color: darkslategray;
  border: 1px solid darkslategray;
  font-weight: 700;
} */
button {
  margin-right: 5px;
  padding: 5px;
  width: 110px;
  border: 1px solid black;
  border-radius: 5px;
  cursor: pointer;
}
button:hover {
  color: darkslategray;
  border: 2px solid darkslategray;
  font-weight: 700;
}
</style>
