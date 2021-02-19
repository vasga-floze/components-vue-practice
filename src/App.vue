<template>
  <div id="app">
    <Header titulo="Programacion Computacional IV"></Header>
    <Index titulo="Ejemplo componentes"></Index>
    
    
  </div>
</template>

<script>
/*import HelloWorld from './components/HelloWorld.vue'
import Ejemplo from './components/Ejemplo.vue'
import Prueba from './components/Prueba.vue'*/
import Header from './components/Header'
import Index from './components/Index'


export default {
  name: 'App',
  components: {
    Index,
    Header
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
