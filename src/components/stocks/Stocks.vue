<template>
  <b-container fluid>
    <b-row>
      <app-stock v-for="stock in stocks" :key="stock.id" :stock="stock"></app-stock>
    </b-row>
  </b-container>

</template>
<script>
  import Stock from './Stock'

  export default {
    data() {
      return {
        stocks: [
          { id: 1, name: 'BMW', price: 120 },
          { id: 2, name: 'Google', price: 200 },
          { id: 3, name: 'Apple', price: 250 },
          { id: 4, name: 'Twitter', price: 40 }
        ]
      }
    },
    components: {
      appStock: Stock
    }
  }
</script>
