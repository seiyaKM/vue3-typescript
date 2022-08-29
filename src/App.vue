<script setup lang="ts">
import Todo from "./components/Todo.vue";
</script>

<template>
  <img alt="Vue logo" src="./assets/logo.png" />
  <Todo></Todo>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin: 60px auto 0;
  max-width: 800px;
}

ul {
  list-style: none;
  margin: 0;
  padding: 0;
}
</style>
