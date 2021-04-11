<template>
  <div id="app">
    <DigitalClock id="digitalClock"/>
  </div>
</template>

<script>
import DigitalClock from './components/DigitalClock.vue'

export default {
  name: 'App',
  components: {
    DigitalClock
  }
}
</script>

<style>
  #app {
    font-family: 'Dosis', sans-serif;
    font-family: 'Exo', sans-serif;
    font-family: 'Geo', sans-serif;
    font-family: 'Orbitron', sans-serif;
    font-family: 'M PLUS 1p', sans-serif;
    font-family: 'Advent Pro', sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    --app-background-color: #000000;
    text-align: center;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    text-align: center;
    min-height: 98vh;
  }
  body {
    background-color: #000000;
    background-image: url('./assets/mosque.jpg');
    background-size: 100% 100%;
    background-repeat: no-repeat;
  }
</style>
