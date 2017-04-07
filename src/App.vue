<template>
  <div>
    <app-header></app-header>
    <div class="container">
      <router-view></router-view>
    </div>
  </div>
</template>

<script>
import Header from './components/Header.vue'
export default {
  components: {
    appHeader: Header
  }
}
</script>

<style lang="scss">
body {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}

h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
