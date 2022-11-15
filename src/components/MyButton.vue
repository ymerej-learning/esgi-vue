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
    });
</script>

<template>
    <button
        v-bind:class="['button']"
        v-bind:style="{
            backgroundColor: background,
            border: '2px solid ' + color,
            borderRadius: rounded ? '0.5rem' : '0',
            color: color,
        }"
    >
        {{ title }}
    </button>
</template>

<style scoped>
    .button {
        cursor: pointer;
        font-weight: bold;
    }
</style>