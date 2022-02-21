<template>
  <div>
    <cepComponet/>
  </div>
</template>

<script>
import cepComponet from './components/CEPComponent.vue'


export default {
  name: 'App',
  components: {
    cepComponet,
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
