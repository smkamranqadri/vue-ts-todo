<template>
  <div id="app">
    <img src="./assets/logo.png">
    <todos></todos>
  </div>
</template>

<script lang="ts">
import Todos from './components/todos.vue';

export default {
  name: 'app',
  components: {
    Todos
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
