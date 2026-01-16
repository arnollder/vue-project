<template>
  <div class="root">
    <HeaderV @is-dark-theme="isDarkThemeHandler" title="Header" />
    <div class="container">
      <MainContent class="border" title="Main Page"/>
      <SidebarNav class="border"/>
    </div>
    <FooterV title="Footer" />
  </div>
</template>

<script lang="ts">
import MainContent from '@/components/layouts/MainContent.vue'
import FooterV from '@/components/layouts/FooterV.vue'
import HeaderV from '@/components/layouts/HeaderV.vue'
import SidebarNav from '@/components/layouts/SidebarNav.vue';
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'TestComponent',
  components: { SidebarNav, MainContent, HeaderV, FooterV },    
  data() {
    return {
      isDarkTheme: false,
    }
  },  
  methods: {
    isDarkThemeHandler(isDark: Boolean) {
      this.isDarkTheme = isDark === true ? true : false
      console.log('parent say:', isDark)
    }
  }
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
.border {
  border: 3px solid gray;
}
</style>
