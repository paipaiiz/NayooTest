<template>
  <div id="app" class="mt-0">
    <Menu></Menu>
    <br>
    <div class="container">
      <Content></Content>
    </div>
    <Footer></Footer>
  </div>
</template>

<script>
import Menu from './components/Menu.vue'
import Content from './components/Content.vue'
import Footer from './components/Footer.vue'

export default {
  name: 'App',
  components: {
    Menu,
    Content,
    Footer
  }
}
</script>

<style>
#app {
  font-family: 'Kanit', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
