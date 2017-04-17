<template>
  <nav class="nav has-shadow">
    <div class="container">
      <div class="nav-left">
        <router-link class="nav-item nav-logo" to="/">Stock Trader</router-link>
        <router-link class="nav-item is-tab" activeClass="is-active" to="/portfolio">Portfolio</router-link>
        <router-link class="nav-item is-tab" activeClass="is-active" to="/stocks">Stocks</router-link>
      </div>
      <div class="nav-right nav-menu">
        <p class="nav-item">
          <strong>
            Funds: {{ funds | currency }}
          </strong>
        </p>
        <a href="#" class="nav-item is-tab" @click="endDay">End Day</a>
        <div class="has-dropdown" :class="{'is-open': isDropdownOpen}" @click="isDropdownOpen = !isDropdownOpen">
          <a href="#" class="button">
            <span>Save & Load</span>
            <span class="icon is-small">
              <i class="fa fa-angle-down"></i>
            </span>
          </a>
          <ul class="dropdown box">
            <li>
              <a href="#" @click="saveData">Save Data</a>
            </li>
            <li>
              <a href="#" @click="loadData">Load Data</a>
            </li>
          </ul>
        </div>
      </div>
    </div>
  </nav>
</template>

<script>
  import { mapActions } from 'vuex'
  export default {
    data () {
      return {
        isDropdownOpen: false
      }
    },
    computed: {
      funds () {
        return this.$store.getters.funds
      }
    },
    methods: {
      ...mapActions({
        randomizeStock: 'randomizeStock',
        fetchData: 'loadData'
      }),
      endDay () {
        this.randomizeStock()
      },
      saveData () {
        const data = {
          funds: this.$store.getters.funds,
          stockPortfolio: this.$store.getters.stockPortfolio,
          stocks: this.$store.getters.stocks
        }
        this.$http.put('data.json', data)
      },
      loadData () {
        this.fetchData()
      }
    }
  }

</script>

<style>

  .nav-logo {
    font-size: 24px;
    font-weight: bold;
  }

  .has-dropdown {
    position: relative;
    align-items: center;
    display: flex;
    flex-grow: 0;
    flex-shrink: 0;
    font-size: 1rem;
    justify-content: center;
    padding: .5rem .75rem
  }

  .dropdown {
    position: absolute;
    top: 84%;
    left: 0;
    display: none;
  }

  .is-open .dropdown {
    display: inline-block;
  }

</style>