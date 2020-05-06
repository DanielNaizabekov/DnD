<template>
  <div id="app">
    <dragDrop/>
  </div>
</template>

<script>
import DragDrop from './components/DragDrop'

export default {
  name: 'App',
  components: {
    DragDrop,
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}

ul, li {
  display: block;
  padding: 0;
  margin: 0;
}

* {
  box-sizing: border-box;
}
</style>
