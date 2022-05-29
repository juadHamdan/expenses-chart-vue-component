<template>
  <ExpensesChart :balance="balance" />
</template>

<script>
import ExpensesChart from "./components/ExpensesChart.vue";
export default {
  name: "App",
  components: {
    ExpensesChart,
  },
  data() {
    return {
      balance: "921.48",
    };
  },
};
</script>

<style>
#app {
  font-family: DM sans;
  font-weight: 400, 700;
  font-size: 18px;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
}
</style>
