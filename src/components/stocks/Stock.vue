<template>
  <b-col sm="6" md="4" class="mt-5">
    <b-card
        title="Card Title"
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
                          v-model="quantity"></b-form-input>
          </b-col>
          <b-col cols="3">
            <b-button variant="success"
                      class="float-right"
                      @click="buyStock"
                      :disabled="quantity <= 0 || !Number.isInteger(+quantity)">
              Buy</b-button>
          </b-col>
        </b-row>


      </b-card-text>
    </b-card>
  </b-col>
</template>

<script>
  export default  {
    props: ['stock'],
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
        };
        console.log(order);
        this.quantity = 0;
      }
    }
  }
</script>
