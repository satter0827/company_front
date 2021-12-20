<template>
  <div id="app">
    <Header />

    <div class="container">
      <img alt="Vue logo" src="./assets/logo.png">
      <Top />
    </div>
    
    <Footer />
  </div>
</template>

<script>
import Top from './components/Top.vue'
import Header from "./components/Header.vue";
import Footer from "./components/Footer.vue";

export default {
  name: 'App',
  components: {
    Top,
    Header,
    Footer,
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
