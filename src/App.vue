<template>
  <div id="app">
    <Main></Main>
  </div>
</template>

<script>
//imports for the SPA components used in the template
import Main from './components/Main.vue'

//exports the view into the app in main.js
export default {
  name: 'App',
  components: {
    Main
  }
}
</script>

<!-- css styling for the App.vue -->
<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 20px;
}
</style>
