<template>
  <div id="app">
    <h1>UT weather info</h1>
      <WeatherInfo area="hongo" />
      <WeatherInfo area="komaba" />
      <WeatherInfo area="kashiwa" />
  </div>
</template>

<script>
import WeatherInfo from './components/WeatherInfo.vue'

export default {
  name: 'App',
  components: {
    WeatherInfo
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: left;
  color: #2c3e50;
}
h1 {
    font-size: 3em;
    padding: 20px;
    background-color: rgb(252, 186, 3);
    color: #fff;
}
h2 {
    text-align: center;
    font-size: 2.4em;
    margin-top: 80px;
}
</style>
