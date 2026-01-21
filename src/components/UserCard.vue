<template>
    <div 
        class="user-root"
        :style="buttonsTheme"
    >
        <div class="user-info" :style="themeStyles">
            <slot name="prepend"/>
            <div class="name">{{ $props.user?.name }}</div>
            <div class="age">age: {{ $props.user?.age }}</div>
            <div class="role">role: {{ $props.user?.role }}</div>
        </div>
        <img 
            :src="$props.user?.img" 
            class="avatar" 
            alt="avatar"
        >
        <slot name="uppend"/>
    </div>
</template>

<script lang="ts">
import { defineComponent, type PropType, type CSSProperties, } from 'vue'

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
        themeStyles: {
            type: Object as PropType<CSSProperties>,
            default: () => ({})
        },
        buttonsTheme: {
            type: Object as PropType<CSSProperties>,
            default: () => ({})
        }              
    },
})
</script>

<style scoped>
.user-root {
    width: 300px;
    padding: 10px;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    row-gap: 10px;
    border: 1px solid black;
    border-radius: 5px;
    overflow: auto;
    /* background-color: gray; */
}
.user-info {
    border: 1px solid black;
    border-radius: 5px;
    padding-left: 5px;
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