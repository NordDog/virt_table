<template>
  <div id="app">
    <gridApp/>
  </div>
</template>

<script>
import gridApp from './components/gridApp.vue'

export default {
  name: 'App',
  components: {
    gridApp
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
