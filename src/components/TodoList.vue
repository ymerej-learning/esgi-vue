<!--
    Gestion de liste de tâches
    (pensez à la séparation des responsabilités)
    Part 1
        - Lister les tâches
        - Pouvoir filter ou pas les tâches terminées
-->

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
    });

    function handleClick() {
        console.log("hello")
}
</script>

<template>
    <button
        v-bind:style="{
            backgroundColor: completed ? 'darkgrey' : 'grey',
            color: 'white',
            padding: '1rem',
            border: 'none',
            margin: '0.5rem',
            borderRadius: '1rem',
            fontWeight: 'bold',
            cursor: 'pointer'
        }"
        v-on:click="handleClick"
    >
        <span v-if="completed">✔</span>
        <span v-else>✖</span>
        {{ name }}
    </button>
</template>

<style scoped>
</style>