<template>
  <MainLayout
    @click="toggleTheme"
    :switchThemeHeaderFooter="switchThemeHeaderFooter"
    :switchThemeMain="switchThemeMain"
    :buttonsTheme="buttonsTheme"
  >
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
  </MainLayout>
</template>

<script lang="ts">
import MainContent from '@/components/MainContent.vue'
import SidebarNav from '@/components/SidebarNav.vue'
import MainLayout from '@/components/layouts/MainLayout.vue'
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'MainView',
  components: { SidebarNav, MainContent, MainLayout},
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
    toggleTheme() {
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
