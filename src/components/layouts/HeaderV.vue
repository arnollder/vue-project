<template>
  <header class="header">{{ title }}
    <!-- <SwitchTheme /> -->
    <button class="switch" @click="toggleTheme">
      Switch Theme
    </button>
  </header>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
// import SwitchTheme from '../SwitchTheme.vue';

export default defineComponent({
  name: 'VHeader',
  // components: { SwitchTheme },
  data() {
    return {
      isDark: false,
    }
  },
  props: {
    title: {
      type: String,
      default: 'default header',
    },
  },
  emits: ['isDarkTheme'],
  methods: {
    toggleTheme() {
      !this.isDark ? this.isDark = true : this.isDark = false;
      this.$emit('isDarkTheme', this.isDark)
      // console.log(this.isDark);
    }
  },
})
</script>

<style scoped>
.header {
  height: 100px;
  background-color: gray;
  font-size: 32px;
  display: flex;
  justify-content: center;
  align-items: center;
}

.switch {
  padding: 5px;
  width: 110px;
  position: absolute;
  top: 10px;
  right: 10px;
  border: 3px solid black;
  border-radius: 5px;
  cursor: pointer;
}

.switch:hover {
  color: darkslategray;
  border: 3px solid darkslategray;
  font-weight: 700;
}
</style>
