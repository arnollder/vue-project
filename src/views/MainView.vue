<template>
  <div class="root">
    <HeaderV title="Header" />
    <ContainerV />
    <FooterV title="Footer" />
  </div>
</template>

<script lang="ts">
import ContainerV from '@/components/layouts/ContainerV.vue'
import FooterV from '@/components/layouts/FooterV.vue'
import HeaderV from '@/components/layouts/HeaderV.vue'
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'TestComponent',
  components: { ContainerV, HeaderV, FooterV },  
})
</script>

<style scoped>
.root {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}
</style>
