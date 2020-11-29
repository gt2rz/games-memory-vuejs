<template>
  <div id="app">
    <MemoryGame></MemoryGame>
  </div>
</template>

<script>
import MemoryGame from './components/MemoryGame'
export default {
  name: 'App',
  components: {
    MemoryGame
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
