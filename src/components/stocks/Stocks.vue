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
    components: {
      appStock: Stock
    },
    computed: {
      stocks() {
        return this.$store.getters.stocks;
      }
    }
  }
</script>
