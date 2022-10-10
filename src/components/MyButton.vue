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

    function handleClick(event) {
        console.info(event);
        props.onClick();
}
</script>

<template>
    <button
        v-bind:style="{
            backgroundColor: background,
            border: 'none',
            borderRadius: rounded ? '0.5rem' : '0',
            color: color,
            cursor: 'pointer',
        }"
        v-on:click="handleClick($event)"
    >
        {{ title }}
    </button>
</template>

<style scoped>
</style>