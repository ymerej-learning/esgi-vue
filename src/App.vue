<script setup>
  import MyButton from './components/MyButton.vue'
  import TodoList from "./components/TodoList.vue"

  import { ref } from "vue"

  const isDark = ref(false);
  const isFilter = ref(false);
  
  function toggleTheme() {
    isDark.value = !isDark.value;
  }

  function filterTask() {
    isFilter.value = !isFilter.value;
    
    let states = document.querySelectorAll('#not-completed');
    states.forEach(state => {
      if(isFilter.value === true) {
        state.style.display = 'none';
      }
      else {
        state.style.display = 'block';
      }
    });
  }

  const object = {
    first: {
      name: "first",
      completed: false,
      id: "not-completed"
    },
    second: {
      name: "second",
      completed: false,
      id: "not-completed"
    },
    third: {
      name: "third",
      completed: true,
      id: "completed"
    },
  };
</script>

<template>
  <div v-bind:class="[isDark ? 'wrapper dark' : 'wrapper white']">
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
            <MyButton v-if="isDark" title="white mode" color="white" v-on:click="toggleTheme"/>
            <MyButton v-else title="dark mode" color="black" v-on:click="toggleTheme"/>
          </li>
        </ul>
      </nav>
      <main>
        <button v-bind:class="[isDark ? 'dark' : 'white']" v-on:click="filterTask">✅ Filter task by completed state</button>
        <template v-for="(todo, key, index) in object" :key="key">
        <TodoList
          v-bind:name="todo.name"
          v-bind="todo"
          v-bind:id="todo.id"
        />
      </template>
      </main>
  </div>
</template>

<style scoped>
  main button {
    display: block;
    border: none;
    background: transparent;
    font-size: 1rem;
    margin-bottom: 2rem;
    cursor: pointer;
    border: 2px solid transparent;
    padding: 1rem;
    font-weight: bold;
  }
  main button:first-child:hover {
    border: 2px solid grey;
    border-radius: 0.5rem;
  }
  main {
    margin: 2rem;
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
    font-weight: bold;
  }
  .navbar a:hover {
    color: white;
  }
  .dark {
    background-color: black;
    color: white;
  }
  .white {
    background-color: white;
    color: black;
  }
</style>