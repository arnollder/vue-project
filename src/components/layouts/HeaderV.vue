<template>
  <header class="header">{{ title }}
    <SwitchTheme />
  </header>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import SwitchTheme from '../SwitchTheme.vue';

export default defineComponent({
  name: 'VHeader',
  components: {SwitchTheme},
  props: {
    title: {
      type: String,
      default: 'default header',
    },
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
</style>
