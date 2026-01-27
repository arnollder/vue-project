<template>
  <div>
    <div class="counter">
      <h2       
        :style="[themeStyles, counterTitleColor]"
      >
        {{ title }}
      </h2>
      <div>Count: {{ count }}</div>
      <div>Double count {{ doubleCount }}</div>
    </div>
    <button :style="buttonsTheme" @click="increment">Increment++</button>
    <button :style="buttonsTheme" @click="decrement">Decrement--</button>
    <button :style="buttonsTheme" @click="reset">Reset</button>  </div>
</template>

<script lang="ts">
import { defineComponent, type CSSProperties, type PropType } from 'vue'

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
      type: Object as PropType<CSSProperties>,
      default: () => ({})
    },
    buttonsTheme: {
      type: Object as PropType<CSSProperties>,
      default: () => ({})
    }
  },
  emits: ['decrement'],
  computed: {
    doubleCount() {
      return this.count * 2
    },
    counterTitleColor() {
      const styles = {...this.themeStyles}
      if (this.count > 5) {
        styles.color = 'red'
      }
      return styles
    }    
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
        console.log('decrement from CC')
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
