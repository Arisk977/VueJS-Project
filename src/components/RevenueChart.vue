<script setup>
import { ref, onMounted } from 'vue'
import { Line } from 'vue-chartjs'
import {
  Chart as ChartJS,
  Title,
  Tooltip,
  Legend,
  LineElement,
  CategoryScale,
  LinearScale,
  PointElement
} from 'chart.js'

import { stockService } from '../services/stockService.js'

ChartJS.register(Title, Tooltip, Legend, LineElement, CategoryScale, LinearScale, PointElement)

const chartData = ref({
  labels: [], // z.B. Q1 2021, Q2 2021, ...
  datasets: []
})

onMounted(async () => {
  // Beispiel: Holen der Daten für Apple
  const appleRevenue = await stockService.getRevenue('AAPL')
  const metaRevenue = await stockService.getRevenue('META')
  // weitere Aktien analog

  chartData.value.labels = [
    'Q1 2021','Q2 2021','Q3 2021','Q4 2021',
    'Q1 2022','Q2 2022','Q3 2022','Q4 2022',
    'Q1 2023','Q2 2023','Q3 2023','Q4 2023','Q1 2024'
  ]

  chartData.value.datasets = [
    {
      label: 'Apple',
      data: appleRevenue,
      borderColor: '#999',
      backgroundColor: 'transparent',
      tension: 0.2
    },
    {
      label: 'Meta',
      data: metaRevenue,
      borderColor: '#0ff',
      backgroundColor: 'transparent',
      tension: 0.2
    }
    // weitere Aktien hier hinzufügen
  ]
})
</script>

<template>
  <div>
    <Line :data="chartData" :options="{ responsive: true, plugins: { legend: { position: 'right' } } }" />
  </div>
</template>

<style scoped>
div {
  background-color: #011F35;
  padding: 16px;
  border-radius: 12px;
}
</style>
