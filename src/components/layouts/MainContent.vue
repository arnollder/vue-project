<template>
    <section class="content">
      <h1 :style="{ color: isMainPageTitleGreen ? 'green' : 'black' }">{{ title }}</h1>
      <ClickCounter @decrement="decrementHandler" :title="$options.title" />
    </section>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import ClickCounter from '@/components/ClickCounter.vue'

export default defineComponent({
  name: 'MainContent',
  components: { ClickCounter },
  data() {
    return {
      isMainPageTitleGreen: false,
    }
  },
  props: {
    title: {
      type: String,
      default: 'default title',
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
.content {
  padding: 10px;
  flex-grow: 1;
}
</style>
