<template>
  <b-col sm="6" md="4" class="mt-5">
    <b-card
        header-tag="h4"
        header-bg-variant="warning"
        text-variant="dark"
        style="max-width: 25rem;"
    >
      <template v-slot:header>{{ stock.name}}
        <small>(Price: {{ stock.price }} | {{ stock.quantity }})</small>
      </template>
      <b-card-text>
        <b-row>
          <b-col cols="9">
            <b-form-input placeholder="Quantity"
                          type="number"
                          v-model="quantity"></b-form-input>
          </b-col>
          <b-col cols="3">
            <b-button variant="warning"
                      class="float-right"
                      @click="btnSellStock"
                      :disabled="insufficientQuantity || quantity <= 0 || !Number.isInteger(+quantity)">
              {{ insufficientQuantity ? 'Not enough' : 'Sell'}}</b-button>
          </b-col>
        </b-row>


      </b-card-text>
    </b-card>
  </b-col>
</template>

<script>
  import { mapActions } from 'vuex'

  export default  {
    props: ['stock'],
    data() {
      return {
        quantity: 0
      }
    },
    computed: {
      insufficientQuantity() {
        return this.quantity > this.stock.quantity;
      }
    },
    methods: {
      ...mapActions([
        'sellStock'
      ]),
      btnSellStock() {
        const order = {
          stockId: this.stock.id,
          stockPrice: this.stock.price,
          quantity: this.quantity
        };
        this.sellStock(order);
        this.quantity = 0;

      }
    }
  }
</script>
