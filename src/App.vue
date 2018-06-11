<template>
  <div id="app">
    <OwnerList/>    
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import OwnerList from './components/OwnerList.vue'

export default {
  name: 'app',
  components: {
    HelloWorld,
    OwnerList
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
