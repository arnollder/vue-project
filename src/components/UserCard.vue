<template>
    <div class="user-root">
        <div class="name">{{ $props.user?.name }}</div>
        <div class="age">{{ $props.user?.age }}</div>
        <div class="role">{{ $props.user?.role }}</div>
        <img 
            :src="$props.user?.img" 
            class="avatar" 
            alt="avatar"
        >
    </div>
</template>

<script lang="ts">
import { defineComponent, type PropType } from 'vue'

interface IUser {
    name: string,
    age: number,
    role: string,
    img: string
}

export default defineComponent({
    props: {
        user: {
            type: Object as PropType<IUser>,
            default: () => ({
                name: 'No Name',
                age: 18,
                role: 'No Role',
                img: 'https://static.bntu.by/bntu/new/staffs/photo_2163_8bd01886c446fc213afa7792f8f8e859.jpg'
            } as IUser),
        },
    },
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
.name {
    font-size: 32px;
}
.age, .role {
    font-size: 20px;
}
</style>