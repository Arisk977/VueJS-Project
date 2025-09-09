<script setup>
import { ref, onMounted } from 'vue'
import BaseCard from './components/BaseCard.vue';
import { stockService } from './services/stockService.js';
import RevenueChart from './components/RevenueChart.vue';

const data = ref([])
const revenueData = ref([])

onMounted(async () => {
  data.value = await stockService.fetchData('AAPL')
  console.log('Loaded data', data.value);
})

onMounted(async () => {
  // getRevenue aufrufen
  revenueData.value = await stockService.getRevenue('AAPL')
  console.log('Loaded revenue data', revenueData.value)
})
</script>

<template>
  <div class="content-wrapper">
    <BaseCard class="base-card">
      <h1>Revenue last 3 years</h1>
      <div class="revenue-chart">
        <RevenueChart />
      </div>
    </BaseCard>

    <BaseCard class="base-card">
      <h1>Revenue Breakdown Magnificent Seven</h1>
      <p>Grafik</p>
    </BaseCard>
  </div>

</template>

<style scoped>
.base-card {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.content-wrapper {
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 32px;
}

.revenue-chart{
  width: 100%;
  height: 100%;
}
</style>
