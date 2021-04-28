<template>
    <button @click="addTask()" class="btn" :style="{background: bg_color}">
        {{ name }}
    </button>
</template>

<script>
    export default {
        name: 'Button',
        props: {
            name: String,
            bg_color: String
        },
        methods: {
            addTask() {
                console.log('Task Added')
            }
        }
    }
</script>
