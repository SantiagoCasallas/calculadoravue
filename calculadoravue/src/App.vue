<template>
  <MiCalculadora msg="Aqui va el titulo"/>
  </template>

<script>
import MiCalculadora from './components/MiCalculadora.vue'

export default {
  name: 'App',
  components: {
    
    MiCalculadora
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
