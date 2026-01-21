<template>
    <div class="user-root">
        <div class="name">name: Sergey</div>
        <div class="age">age: 40</div>
        <div class="role">role: Teacher</div>
        <img class="avatar" src="https://avatars.mds.yandex.net/i?id=b7add193de701e6d161b01a876c09b0e_l-5205087-images-thumbs&n=13" alt="avatar">
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
    setup () {
        

        return {}
    }
})
</script>

<style scoped>
.user-root {
    width: 300px;
    height: 500px;
    border: 1px solid black;
    border-radius: 5px;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    padding: 10px;
}
.avatar {
    width: 100%;
    height: auto;
    border: 1px solid black;
    border-radius: 5px;
}
</style>