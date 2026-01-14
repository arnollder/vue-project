<template>
  <div class="root">
    <header class="header">Header</header>
    <section class="content">
      <h1>Main Page</h1>
      <ClickCounter />
    </section>
    <footer class="footer">Footer {{ new Date().getFullYear() }}</footer>
  </div>
</template>

<script lang="ts">
import ClickCounter from '@/components/ClickCounter.vue'
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'TestComponent',
  components: { ClickCounter },
})
</script>

<style scoped>
.root {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}
.header,
.footer {
  height: 100px;
  background-color: gray;
  font-size: 32px;
  display: flex;
  justify-content: center;
  align-items: center;
}
.content {
  flex-grow: 1;
  padding: 10px;
}
</style>
