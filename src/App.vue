<template>
  <div id="app" v-if="!isMobile()">
    <DashBoard/>
  </div>
  <div v-else>
    <DashBoardMobile/>
  </div>
</template>

<script>
import DashBoard from './components/DashBoard.vue'
import DashBoardMobile from './components/DashBoardMobile.vue'

export default {
  name: 'App',
  components: {
    DashBoard,
    DashBoardMobile
  },
  methods: {
    isMobile() {
     if(/Android|webOS|iPhone|iPad|iPod|BlackBerry|IEMobile|Opera Mini/i.test(navigator.userAgent)) {
       return true
     } else {
       return false
     }
    }
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
