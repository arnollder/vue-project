<template>
  <div>
    <div class="counter">
      <h2 
        :style="counterTitleColor"
        :theme-styles="themeStyles"
      >
        {{ title }}
      </h2>
      <div>Count: {{ count }}</div>
      <div>Double count {{ doubleCount }}</div>
    </div>
    <button :style="themeStyles" @click="increment">Increment++</button>
    <button :style="themeStyles" @click="decrement">Decrement--</button>
    <button :style="themeStyles" @click="reset">Reset</button>  </div>
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
    themeStyles: {
      type: Object,
      default: () => ({})
    }
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
