<script setup>
    const props = defineProps({
        name: {
            type: String,
            required: true,
        },
        completed: {
            type: Boolean,
            default: false,
        },
        id: {
            type: String,
            default: "not-completed"
        }
    });
</script>

<template>
    <button
        v-bind:class="['task']"
        v-bind:style="{
            backgroundColor: completed ? 'darkgreen' : 'darkred',
        }"
        v-on:click="completed = !completed"
        v-bind:id="completed ? 'completed' : 'not-completed'"

    >
        <span v-if="completed">✔</span>
        <span v-else>✖</span>
        {{ name }}
    </button>
</template>

<style scoped>
    .task {
        color: white;
        padding: 1rem;
        border: none;
        margin: 0.5rem;
        border-radius: 1rem;
        font-weight: bold;
        cursor: pointer;
    }
</style>