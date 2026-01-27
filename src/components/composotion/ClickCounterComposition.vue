<template>
  <div>
    <div class="counter">
      <h2 :style="[themeStyles, counterTitleColor]">
        {{ title }}
      </h2>
      <div>Count: {{ count }}</div>
      <div>Double count {{ doubleCount }}</div>
    </div>
    <button :style="buttonsTheme" @click="increment">Increment++</button>
    <button :style="buttonsTheme" @click="decrement">Decrement--</button>
    <button :style="buttonsTheme" @click="reset">Reset</button>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue';

const count = ref(0);

const increment = () => count.value++;
const decrement = () => count.value--;
const reset = () => count.value = 0;


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
