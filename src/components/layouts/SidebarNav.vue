<template>
  <nav class="sidebar">
    <ul class="menu">
      <li><a href="#">Главная</a></li>
      <li><a href="#">Счётчик кликов</a></li>
      <li><a href="#">Какая-то кнопка</a></li>
      <li><a href="#">Обратная связь</a></li>
      <li>Главная</li>
      <li>Счётчик кликов</li>
      <li>Какая-то кнопка</li>
      <li>Обратная связь</li>

    </ul>
  </nav>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'SidebarNav',
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
