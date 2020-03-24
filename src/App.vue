<template>
  <div id="app">
    <app-header/>
    <b-container fluid>
        <router-view></router-view>

    </b-container>
  </div>
</template>

<script>
import Header from './components/Header'

export default {
  name: 'App',
  components: {
    appHeader: Header
  },
  created() {
    this.$store.dispatch('initStocks');
  }
}
</script>

<style>
  body {
    padding: 30px;
  }
</style>
