<template>
  <div id="app">
    <todolist></todolist>
  </div>
</template>

<script>
import Todolist from './components/Todolist'

export default {
  name: 'app',
  components: {
    Todolist
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
