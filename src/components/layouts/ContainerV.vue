<template>
  <div class="container">
    <nav class="sidebar">
      <ul class="menu">
        <li><a href="#">Главная</a></li>
        <li><a href="#">Счётчик кликов</a></li>
        <li><a href="#">Какая-то кнопка</a></li>
        <li><a href="#">Обратная связь</a></li>
      </ul>
    </nav>
    <section class="content">
      <h1 :style="{ color: isMainPageTitleGreen ? 'green' : 'black' }">Main Page</h1>
      <ClickCounter @decrement="decrementHandler" :title="$options.title" />
    </section>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import ClickCounter from '@/components/ClickCounter.vue'

export default defineComponent({
  components: { ClickCounter },
  data() {
    return {
      isMainPageTitleGreen: false,
    }
  },
  title: 'Our counter title',
  methods: {
    decrementHandler(event: number) {
      this.isMainPageTitleGreen = event < -5 ? true : false
      console.log('decrement-handler', event)
    },
  },
})
</script>

<style scoped>
.container {
  display: flex;
  flex-grow: 1;
  padding: 10px;
}

.sidebar {
  padding: 10px;
  border: 3px solid gray;
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

.content {
  padding: 10px;
  flex-grow: 1;
}
</style>
