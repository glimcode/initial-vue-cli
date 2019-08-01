<template>
  <div id="app">
    <xHeader></xHeader>
    <router-view/>
  </div>
</template>

<script>
import './assets/stylus/index.styl'
import xHeader from './components/common/header'
export default {
  name: 'App',
  components: {
    xHeader
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
