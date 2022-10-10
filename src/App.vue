<script setup>
  import MyButton from './components/MyButton.vue'
  import { ref } from "vue"

  const isDark = ref(false);

  function toggleTheme() {
    isDark.value = !isDark.value;
  }
</script>

<template>
  <div :class="['wrapper', { 'dark': isDark }]">
      <nav :class="['navbar']">
        <ul>
          <li>
            <a href="/" title="Accueil" alt="Accueil">Accueil</a>
          </li>
          <li>
            <MyButton title="🌓" background="transparent" rounded=true :onClick="toggleTheme"/>
          </li>
        </ul>
      </nav>
  </div>
</template>

<style scoped>
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