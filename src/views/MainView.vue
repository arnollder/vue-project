<template>
  <div class="root"
    :style="switchTheme"
  >
    <HeaderV 
      @is-dark-theme="isDarkThemeHandler" 
      title="Header" 
      :style="switchTheme"
    />
    <div class="container">
      <MainContent
        class="border"
        title="Main Page"
        :style="switchTheme"
      />
      <SidebarNav
        :style="switchTheme"
        class="border"
      />
    </div>
    <FooterV 
      title="Footer"
      :style="switchTheme"      
    />
  </div>
</template>

<script lang="ts">
import MainContent from '@/components/layouts/MainContent.vue'
import FooterV from '@/components/layouts/FooterV.vue'
import HeaderV from '@/components/layouts/HeaderV.vue'
import SidebarNav from '@/components/layouts/SidebarNav.vue'
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'TestComponent',
  components: { SidebarNav, MainContent, HeaderV, FooterV },
  data() {
    return {
      isDarkTheme: false,
    }
  },
  computed: {
    switchTheme() {
      return {
          'background-color': this.isDarkTheme ? '#36373a' : 'white',
          color: this.isDarkTheme ? 'darkgray' : 'black',
        }
    }
  },
  methods: {
    isDarkThemeHandler(isDark: Boolean) {
      this.isDarkTheme = isDark ? true : false
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
