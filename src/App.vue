<template>
  <Home saludo="Hola" dia="23"></Home>
</template>

<script>
import Home from './components/Home'
import { provide } from 'vue'

export default {
  name: 'App',
  components: {
    Home
  },
  setup () {
    provide('username', 'fmanez')
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
