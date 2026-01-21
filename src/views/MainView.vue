<template>
  <div class="root"
    :style="switchThemeMain"
  >
    <HeaderV 
      @is-dark-theme="toggleThemeHandler" 
      title="Header" 
      :style="switchThemeHeaderFooter"
      :buttonsTheme="buttonsTheme"
    />
    <div class="container">
      <MainContent
        class="border"
        title="Main Page"
        :theme-styles="switchTheme"
        :buttonsTheme="buttonsTheme"
      />
      <SidebarNav
        :theme-styles="switchTheme"
        class="border"
      />
    </div>
    <FooterV 
      title="Footer"
      :style="switchThemeHeaderFooter"      
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
    },
    switchThemeMain() {
      return {
          'background-color': this.isDarkTheme ? 'darkgray' : undefined,
        }
    },
    switchThemeHeaderFooter() {
      return {
          'background-color': this.isDarkTheme ? '#36373a' : 'gray',
          color: this.isDarkTheme ? 'darkgray' : 'black',
        }
    },
    buttonsTheme() {
      return {
          'background-color': this.isDarkTheme ? 'gray' : undefined,
        }
    }
  },
  methods: {
    toggleThemeHandler() {
      this.isDarkTheme = !this.isDarkTheme
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
