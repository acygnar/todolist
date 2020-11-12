<template>
  <div id="app">
    <HeroImage />
    <img alt="Vue logo" src="./assets/logo.png">
    <Header />
    <Tasks />
  </div>
</template>

<script>
import HeroImage from './components/HeroImage.vue'
import Header from './components/Header.vue'
import Tasks from './components/Tasks.vue'

export default {
  name: 'App',
  components: {
    HeroImage,
    Header,
    Tasks,
  }
}
</script>

<style lang="scss">
@import url('https://use.fontawesome.com/releases/v5.7.1/css/all.css');
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
