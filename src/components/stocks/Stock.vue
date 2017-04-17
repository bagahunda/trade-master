<template>
  <div class="column is-4">
    <div class="card">
      <div class="card-header">
        <p class="card-header-title">
          {{ stock.name }}
          <small>Price: {{ stock.price }}</small>
        </p>
      </div>
      <div class="card-content">
        <div class="level">
          <div class="level-left">
            <div class="level-item">
              <div class="field">
                <p class="control">
                  <input type="number" class="input" placeholder="Quantity" v-model="quantity" :class="{ 'is-danger': insufficientFunds }">
                </p>
              </div>
            </div>
          </div>
          <div class="level-right">
            <div class="level-item">
              <button class="button is-primary" @click="buyStock" :disabled=" insufficientFunds || quantity <= 0">{{ insufficientFunds ? 'Insufficient Funds' : 'Buy' }}</button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    props: [
      'stock'
    ],
    data() {
      return {
        quantity: 0
      }
    },
    computed: {
      funds () {
        return this.$store.getters.funds
      },
      insufficientFunds () {
        return this.quantity * this.stock.price > this.funds
      }
    },
    methods: {
      buyStock() {
        const order = {
          stockId: this.stock.id,
          stockPrice: this.stock.price,
          quantity: this.quantity
        }
        this.$store.dispatch('buyStock', order)
        this.quantity = 0
      }
    }
  }
</script>

<style>

  small {
    padding: 0 0.5em;
  }

</style>