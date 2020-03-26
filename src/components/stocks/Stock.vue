<template>
  <b-col sm="6" md="4" class="mt-5">
    <b-card
        header-tag="h4"
        header-bg-variant="success"
        text-variant="white"
        style="max-width: 25rem;"
    >
      <template v-slot:header>{{ stock.name}}
        <small>(Price: {{ stock.price }})</small>
      </template>
      <b-card-text>
        <b-row>
          <b-col cols="9">
            <b-form-input placeholder="Quantity"
                          type="number"
                          v-model="quantity"
                          :class="{danger: insufficientFunds}"></b-form-input>
          </b-col>
          <b-col cols="3">
            <b-button variant="success"
                      class="float-right"
                      @click="buyStock"
                      :disabled="insufficientFunds || quantity <= 0 || !Number.isInteger(+quantity)">
              {{ insufficientFunds ? 'Insufficient Funds' : 'Buy'}}</b-button>
          </b-col>
        </b-row>


      </b-card-text>
    </b-card>
  </b-col>
</template>

<style scoped>
  .danger {
    border: 1px solid red;
  }
</style>

<script>
  export default  {
    props: ['stock'],
    data() {
      return {
        quantity: 0
      }
    },
    computed: {
      funds() {
        return this.$store.getters.funds;
      },
      insufficientFunds() {
        return this.quantity * this.stock.price > this.funds;
      }
    },
    methods: {
      buyStock() {
        const order = {
          stockId: this.stock.id,
          stockPrice: this.stock.price,
          quantity: +this.quantity
        };
        this.$store.dispatch('buyStock', order);
        this.quantity = 0;
      }
    }
  }
</script>
