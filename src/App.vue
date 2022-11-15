<script setup>
  import MyButton from './components/MyButton.vue'
  import TodoList from "./components/TodoList.vue"

  import { ref } from "vue"

  const isDark = ref(false);
  
  function toggleTheme() {
    isDark.value = !isDark.value;
  }

  const object = {
    first: {
      name: "first",
      completed: false,
    },
    second: {
      name: "second",
      completed: false,
    },
    third: {
      name: "third",
      completed: true,
    },
  };
</script>

<template>
  <div v-bind:class="['wrapper', { 'dark': isDark }]">
      <nav v-bind:class="['navbar']">
        <ul>
          <li v-show="isDark">
            😎
          </li>
          <li v-show="!isDark">
            😳
          </li>
          <li>
            <a href="/" title="Accueil" alt="Accueil">Home</a>
          </li>
          <li>
            <MyButton v-if="isDark" title="white mode" background="transparent" v-bind:rounded="true" v-on:click="toggleTheme"/>
            <MyButton v-else title="dark mode" background="transparent" v-bind:rounded="true" v-on:click="toggleTheme"/>
          </li>
        </ul>
      </nav>
      <main>
        <!-- TODO: sort by task completed -->
        List of tasks :
        <template v-for="(todo, key, index) in object" :key="key">
        <TodoList
          v-bind:name="todo.name"
          v-bind="todo"
        />
      </template>
      </main>
  </div>
</template>

<style scoped>
  main button {
    display: block;
  }
  main {
    margin: 2rem;
    color: white;
  }
  .wrapper {
    width: 100vw;
    height: 100vh;
  }
  .navbar {
    display: flex;
    background-color: grey;
    width: 100%;
  }
  .navbar ul {
    list-style-type: none;
    display: flex;
  }
  .navbar li {
    margin: 1rem;
  }
  .navbar li:nth-child(3) {
    padding-right: 10rem;
  }
  .navbar a {
    text-decoration: none;
    color: black;
  }
  .dark {
    background-color: black;
  }
</style>