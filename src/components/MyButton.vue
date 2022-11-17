<script setup>
    const props = defineProps({
        title: {
            type: String,
            required: true,
        },
        color: {
            type: String,
            required: true,
        },
    });
</script>

<template>
    <button
        v-bind:class="['button']"
        v-bind:style="{
            border: '2px solid ' + color,
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
        background-color: transparent;
        border-radius: 0.5rem;
    }
</style>