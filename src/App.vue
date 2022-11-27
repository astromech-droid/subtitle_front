<template>
  <!--<img alt="Vue logo" src="./assets/logo.png">-->
  <!--<HelloWorld msg="Welcome to Your Vue.js App"/>-->
  <SearchLines msg="Welcome to SubtitleDB!"/>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import SearchLines from './components/SearchLines.vue'

export default {
  name: 'App',
  components: {
    SearchLines
    //HelloWorld
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
