<template>
  <div class="column is-4">
    <div class="card">
      <div class="card-header">
        <p class="card-header-title">
          {{ stock.name }}
          <small>Price: {{ stock.price }} | Quantity: {{ stock.quantity }}</small>
        </p>
      </div>
      <div class="card-content">
        <div class="level">
          <div class="level-left">
            <div class="level-item">
              <div class="field">
                <p class="control">
                  <input type="number" class="input" placeholder="Quantity" v-model="quantity" :class="{'is-danger': insufficientQuantity}">
                </p>
              </div>
            </div>
          </div>
          <div class="level-right">
            <div class="level-item">
              <button class="button is-primary" @click="sellStock" :disabled="insufficientQuantity || quantity <= 0">{{ insufficientQuantity ? 'Not Enough Stocks' : 'Sell' }}</button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  import { mapActions } from 'vuex'

  export default {
    props: [
      'stock'
    ],
    data () {
      return {
        quantity: 0
      }
    },
    computed: {
      insufficientQuantity () {
        return this.quantity > this.stock.quantity
      }
    },
    methods: {
      ...mapActions({
        placeSellOrder: 'sellStock'
      }),
      sellStock() {
        const order = {
          stockId: this.stock.id,
          stockPrice: this.stock.price,
          quantity: this.quantity
        }
        this.placeSellOrder(order)
        this.quantity = 0
      }
    }
  }
</script>