<template>
  <div class="container">
    <div class="columns is-multiline">
      <app-stock v-for="stock in stocks" :stock="stock"></app-stock>
    </div>
  </div>
</template>

<script>
  import { mapGetters } from 'vuex'
  import Stock from './Stock.vue'

  export default {
    computed: {
      ...mapGetters({
        stocks: 'stockPortfolio'
      })
    },

    components: {
      appStock: Stock
    }
  }
</script>