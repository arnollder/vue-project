<template>
  <div class="root">
    <Header title="Header" />
    <section class="content">
      <h1 :style="{ color: isMainPageTitleGreen ? 'green' : 'black' }">Main Page</h1>
      <ClickCounter @decrement="decrementHandler" :title="$options.title" />
    </section>
    <Footer title="Footer" />
  </div>
</template>

<script lang="ts">
import ClickCounter from '@/components/ClickCounter.vue'
import Footer from '@/components/layouts/Footer.vue';
import Header from '@/components/layouts/Header.vue'
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'TestComponent',
  components: { ClickCounter, Header, Footer },
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
