<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
  <Forms></Forms>
  </div>
</template>

<script>
import Forms from './components/Forms'

export default {
  name: 'App',
  components: {
    Forms
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
