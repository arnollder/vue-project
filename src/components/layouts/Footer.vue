<template>
    <footer class="footer">{{ title }} {{ new Date().getFullYear() }}</footer>

</template>

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
    props: {
        title: {
            type: String,
            default: 'default footer',
        },
    },
})
</script>

<style scoped></style>