<template>
  <div>
    <div
      @mouseover="showSpendingAmount = true"
      @mouseleave="showSpendingAmount = false"
      class="chart-column"
      :style="{ height: `${amount * 2}px` }"
    >
      <Transition name="popover">
        <div v-if="showSpendingAmount" class="spending-amount-popover">${{ amount }}</div>
      </Transition>   
    </div>
    <p>{{ day }}</p>
  </div>
</template>

<script>
export default {
  name: "ExpensesChartColumn",
  props: {
    day: String,
    amount: String,
  },
  data() {
    return {
      showSpendingAmount: false,
    };
  },
};
</script>

<style scoped>
.chart-column {
  background-color: hsl(10, 79%, 65%);
  border-radius: 5px;
  width: 35px;
  cursor: pointer;
}

.chart-column:hover {
  background-color: hsl(186, 34%, 60%);
}

.spending-amount-popover {
  position: relative;
  top: -30px;
  right: 5px;
  width: 35px;
  background-color: hsl(25, 47%, 15%);
  color: white;
  font-weight: 600;
  border-radius: 3px;
  padding: 5px;
  margin-bottom: 5px;
}

.popover-enter-active,
.popover-leave-active {
  transition: all 0.2s ease;
}

.popover-enter-from,
.popover-leave-to {
  opacity: 0;
  transform: scale(0);
}
</style>