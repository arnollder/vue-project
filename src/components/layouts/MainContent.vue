<template>
  <div class="content" :style="themeStyles">
    <section >
      <h1>{{ title }}</h1>
      <ClickCounter 
        @decrement="decrementHandler" 
        :title="$options.title" 
        :theme-styles="themeStyles"
        :buttonsTheme="buttonsTheme"
      />
    </section>
    <section>
      <h2>Пользователи</h2>
      <div class="user-list">
        <UserCard 
          :user="{
            name: 'Sergey',
            age: 40,
            role: 'Teacher',
            img: 'https://avatars.mds.yandex.net/i?id=b7add193de701e6d161b01a876c09b0e_l-5205087-images-thumbs&n=13'
          }"
        />
        <UserCard />
      </div>
    </section>
  </div>
</template>

<script lang="ts">
import { defineComponent, type CSSProperties, type PropType } from 'vue'
import ClickCounter from '@/components/ClickCounter.vue'
import UserCard from '@/components/UserCard.vue'


export default defineComponent({
  name: 'MainContent',
  components: { ClickCounter, UserCard },
  data() {
    return {
      isMainPageTitleGreen: false,
    }
  },
  props: {
    title: {
      type: String,
      default: 'default title',
    },
    themeStyles: {
      type: Object as PropType<CSSProperties>,
      default: () => ({})
    },
    buttonsTheme: {
      type: Object as PropType<CSSProperties>,
      default: () => ({})
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
.user-list {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
}
</style>
