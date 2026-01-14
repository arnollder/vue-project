<template>
    <header class="header">{{ title }}</header>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
    props: {
        title: {
            type: String,
            default: 'default header',
        }
        
    }
})
</script>

<style scoped></style>