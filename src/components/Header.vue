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
          <b-nav-item>End Day</b-nav-item>
          <b-nav-item-dropdown text="Save & Load" right>
            <b-dropdown-item href="#">Save Data</b-dropdown-item>
            <b-dropdown-item href="#">Load Data</b-dropdown-item>
          </b-nav-item-dropdown>

        </b-navbar-nav>
        <b-nav-text class="font-weight-bold text-dark">Funds: {{ funds }}</b-nav-text>
      </b-collapse>
    </b-navbar>
  </div>
</template>

<script>
  export default {
    computed: {
      funds() {
        return this.$store.getters.funds;
      }
    }
  }
</script>
