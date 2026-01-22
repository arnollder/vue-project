<template>
  <div class="root"
    :style="switchThemeMain"
  >
    <HeaderV 
        title="Header" 
        :style="switchThemeHeaderFooter"
        :buttonsTheme="buttonsTheme"
    />
    <div class="container">
        <slot />
    </div>
    <FooterV 
        title="Footer"
        :style="switchThemeHeaderFooter"      
    />
  </div>
</template>

<script lang="ts">
import FooterV from '@/components/FooterV.vue'
import HeaderV from '@/components/HeaderV.vue'
import { defineComponent, type CSSProperties, type PropType } from 'vue'

export default defineComponent({
  name: 'MainLayout',
  components: { HeaderV, FooterV },
  props: {
    switchThemeHeaderFooter: {
        type: Object as PropType<CSSProperties>,
        default: () => ({}),
    },
    switchThemeMain: {
        type: Object as PropType<CSSProperties>,
        default: () => ({}),
    },
    buttonsTheme: {
        type: Object as PropType<CSSProperties>,
        default: () => ({}),
    }
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
.container {
  display: flex;
  column-gap: 10px;
  flex-grow: 1;
  padding: 10px;
}
</style>
