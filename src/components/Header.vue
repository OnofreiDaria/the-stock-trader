<template>
  <div>
    <b-navbar toggleable="lg" type="dark" variant="info">
      <b-navbar-brand to="/">Stock Trader</b-navbar-brand>

      <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

      <b-collapse id="nav-collapse" is-nav>
        <b-navbar-nav>
          <b-nav-item to="/portfolio">Portfolio</b-nav-item>
          <b-nav-item to="/stocks">Stocks</b-nav-item>
        </b-navbar-nav>

        <!-- Right aligned nav items -->

        <b-navbar-nav class="ml-auto">
          <b-nav-item @click="endDay">End Day</b-nav-item>
          <b-nav-item-dropdown text="Save & Load" right>
            <b-dropdown-item @click="saveData">Save Data</b-dropdown-item>
            <b-dropdown-item @click="btnLoadData">Load Data</b-dropdown-item>
          </b-nav-item-dropdown>

        </b-navbar-nav>
        <b-nav-text class="font-weight-bold text-dark">Funds: {{ funds | currency }}</b-nav-text>
      </b-collapse>
    </b-navbar>
  </div>
</template>

<script>
  import { mapActions } from 'vuex';

  export default {
    computed: {
      funds() {
        return this.$store.getters.funds;
      }
    },
    methods: {
      ...mapActions([
        'randomizeStocks',
        'loadData'
      ]),
      endDay() {
        this.randomizeStocks();
      },
      saveData() {
        const data = {
          funds: this.$store.getters.funds,
          stockPortfolio: this.$store.getters.stockPortfolio,
          stocks: this.$store.getters.stocks
        };
        this.$http.put('data.json', data);
      },
      btnLoadData() {
        this.loadData();
      }
    }
  }
</script>
