<script>
import data from "../assets/data.json";
import ExpensesChartColumn from "./ExpensesChartColumn.vue";

export default {
  name: "ExpensesChart",
  props: {
    balance: String,
  },
  components: {
    ExpensesChartColumn,
  },
  data() {
    return {
      weekData: data,
    };
  },
  computed: {
    computeTotal() {
      const amountsList = this.weekData.map((dayData) => dayData.amount);
      return amountsList.reduce((amount1, amount2) => amount1 + amount2);
    },
  },
};
</script>



<template>
  <div class="container">
    <div class="header">
      <div class="balance">
        <small>My balance</small>
        <br />
        <div class="balance-amount">${{ balance }}</div>
      </div>
      <div class="logo">
        <svg
          width=""
          height=""
          viewBox="0 0 72 48"
          xmlns="http://www.w3.org/2000/svg"
        >
          <g fill="none" fill-rule="evenodd">
            <circle fill="#382314" cx="48" cy="24" r="24" />
            <circle stroke="#FFF" stroke-width="2" cx="24" cy="24" r="23" />
          </g>
        </svg>
      </div>
    </div>

    <br />

    <div class="spending">
      <h3>Spending - Last 7 days</h3>
      <div class="chart">
        <div v-for="dayData in weekData" :key="dayData.day">
          <ExpensesChartColumn :day="dayData.day" :amount="dayData.amount" />
        </div>
      </div>
      <hr />
      <div class="total">
        <div class="total-amount">
          <div class="total-text">Total this month</div>
          <h2>${{ computeTotal }}</h2>
        </div>
        <div class="last-month-comp">
          <strong>+2.4%</strong>
          <div class="total-text">from last month</div>
        </div>
      </div>
    </div>
  </div>
</template>



<style scoped>
.chart {
  height: 180px;
  display: flex;
  justify-content: space-evenly;
  align-items: flex-end;
  color: #aaa;
  font-size: 12px;
}

.logo {
  width: 50px;
  height: 50%;
  margin-top: 5px;
}

p {
  display: inline;
}
h2 {
  margin-top: 0;
  margin-bottom: 10px;
}
h3 {
  text-align: left;
}
small {
  font-size: 11px;
}
h3 {
  font-size: 18px;
}
hr {
  border-top: 1px solid #f8f8f8;
}
strong {
  font-size: 12px;
}

.container {
  margin: 0;
  border: 0;
  min-height: 100vh;
  background-color: hsl(27, 66%, 92%);
  position: absolute;
  top: 0;
  left: 0;
  width: 100vw;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
.header {
  background-color: hsl(10, 79%, 65%);
  border-radius: 10px;
  padding: 10px 20px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  color: white;
  width: 350px;
}

.header.balance-amount {
  font-weight: 500;
}

.spending {
  width: 350px;
  padding: 2px 20px;
  border-radius: 10px;
  background-color: white;
  color: hsl(25, 47%, 15%);
}

.total {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 10px;
}

.total-amount {
  text-align: left;
}

.last-month-comp {
  text-align: right;
}

.total-text {
  font-size: 12px;
  color: #aaa;
  font-weight: 600;
}

.balance {
  text-align: left;
}
.balance-amount {
  font-size: 20px;
  font-weight: 700;
  margin: 5px 0;
}
</style>