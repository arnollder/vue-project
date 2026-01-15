<template>
  <div>
    <button class="switch">Switch Theme</button>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
  setup() {
    return {}
  },
})
</script>

<style scoped>
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
