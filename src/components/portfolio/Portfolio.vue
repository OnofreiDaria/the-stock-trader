<template>

  <b-row>
    <app-stock v-for="stock in stocks" :stock="stock" :key="stock.id"></app-stock>
  </b-row>

</template>

<script>
  import { mapGetters } from 'vuex';
  import Stock from './Stock';

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
