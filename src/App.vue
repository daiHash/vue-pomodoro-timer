<template>
  <div id="app">
    <!-- <img src="./assets/logo.png"> -->
    <timer/>
  </div>
</template>

<script>
import Timer from './components/Timer'

export default {
  name: 'App',
  components: {
    Timer
  }
}
</script>

<style lang="scss">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  /* margin-top: 60px; */
  background-image: url('./assets/timer.jpg');
  background-position: center;
  background-size: cover;
  height: 100vh;
  width: 100%;
  @media all and (max-width: 768px) {
    background-position-y: 50px;
  }
}

body, html {
  margin: 0;
  padding: 0;
  font-size: 20px;
}
</style>
