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
                  <input type="number" class="input" placeholder="Quantity" v-model="quantity">
                </p>
              </div>
            </div>
          </div>
          <div class="level-right">
            <div class="level-item">
              <button class="button is-primary" @click="buyStock" :disabled="quantity <= 0">Buy</button>
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