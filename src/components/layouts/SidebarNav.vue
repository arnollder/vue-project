<template>
  <nav class="sidebar" :style="themeStyles">
    <ul class="menu">
      <li><a href="#" :style="themeStyles">Главная</a></li>
      <li><a href="#" :style="themeStyles">Счётчик кликов</a></li>
      <li><a href="#" :style="themeStyles">Какая-то кнопка</a></li>
      <li><a href="#" :style="themeStyles">Обратная связь</a></li>    
    </ul>
  </nav>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'SidebarNav',
  props: {
    themeStyles: {
      type: Object,
      default: () => ({})
    }
  }
})
</script>

<style scoped>
.sidebar {
  padding: 10px;
  color: inherit;
}
.menu {
  list-style: none;
}
li {
  margin: 5px;
}
a {
  color: black;
}
</style>
