<template>
  <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
  <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
  <ApiInfoBlock apiUrl="https://random-data-api.com/api/v2/banks"></ApiInfoBlock>
  <ApiInfoBlock apiUrl="https://randomuser.me/api/"></ApiInfoBlock>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import ApiInfoBlock from './components/ApiInfoBlock.vue';

export default {
  name: 'App',
  components: {
    // HelloWorld
    ApiInfoBlock
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
