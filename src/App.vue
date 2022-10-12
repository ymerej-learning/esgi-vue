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
      name: "dafgsdfghen",
      completed: false,
    },
    second: {
      name: "hfjhkljfdgf",
      completed: false,
    },
    third: {
      name: "rdsgnki",
      completed: true,
    },
  };
</script>

<template>
  <div v-bind:class="['wrapper', { 'dark': isDark }]">
      <nav v-bind:class="['navbar']">
        <ul>
          <li>
            <a href="/" title="Accueil" alt="Accueil">accueil</a>
          </li>
          <li>
            <MyButton v-if="isDark" title="white mode" background="transparent" v-bind:rounded="true" v-bind:onClick="toggleTheme"/>
            <MyButton v-else title="dark mode" background="transparent" v-bind:rounded="true" v-bind:onClick="toggleTheme"/>
          </li>
          <li v-show="isDark">
            😎
          </li>
          <li v-show="!isDark">
            😳
          </li>
        </ul>
      </nav>
      <main>
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
  .navbar a {
    text-decoration: none;
    color: black;
  }
  .dark {
    background-color: black;
  }
</style>