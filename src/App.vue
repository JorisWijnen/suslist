<template>
  <div id="app">
    <DashBoard/>
    <Card/>
  </div>
</template>

<script>
import DashBoard from './components/DashBoard.vue'

export default {
  name: 'App',
  components: {
    DashBoard
  }
}
</script>

<style>
html, body {
  height: 100%;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  height: 100%;
}
</style>
