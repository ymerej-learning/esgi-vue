<script setup>
    const props = defineProps({
        title: {
            type: String,
            required: true,
        },
        rounded: {
            type: Boolean,
            default: false,
        },
        background: {
            type: String,
            required: true,
        },
        color: {
            type: String,
            required: true,
            default: "black",
            validator(value) {
                return ["black"].includes[value];
            },
        },
        onClick: {
            type: Function,
            required: true,
        },
    });

    function handleClick() {
    }
</script>

<template>
    <button
        v-bind:style="{
            backgroundColor: background,
            border: '2px solid ' + color,
            borderRadius: rounded ? '0.5rem' : '0',
            color: color,
            cursor: 'pointer',
            fontWeight: 'bold'
        }"
        v-on:click="handleClick"
    >
        {{ title }}
    </button>
</template>

<style scoped>
</style>