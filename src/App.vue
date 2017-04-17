<template>
  <div>
    <app-header></app-header>
    <main>
      <div class="container">
        <transition name="slide" mode="out-in">
          <router-view></router-view>
        </transition>
      </div>
    </main>
  </div>
</template>

<script>
import Header from './components/Header.vue'
export default {
  components: {
    appHeader: Header
  },
  created() {
    this.$store.dispatch('initStocks')
  }
}
</script>

<style lang="scss">
  body {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    font-size: 18px;
    color: #2c3e50;
  }

  main {
    padding: 50px 0;
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

  .slide-enter-active {
    animation: slide-in 0.2s ease-out forwards;
  }

  .slide-leave-active {
    animation: slide-out 0.2s ease-out forwards;
  }

  @keyframes slide-in {
    from {
      transform: translateY(-30px);
      opacity: 0;
    }
    to {
      transform: translateY(0);
      opacity: 1;
    }
  }

  @keyframes slide-out {
    from {
      transform: translateY(0);
      opacity: 1;
    }
    to {
      transform: translateY(-30px);
      opacity: 0;
    }
  }

</style>
