<script setup>
import BaseCard from './components/BaseCard.vue';
</script>

<template>
  <div class="content-wrapper">
    <BaseCard class="base-card">
    <h1>Revenue last 3 years</h1>
    <p>Grafik</p>
  </BaseCard>
  <BaseCard class="base-card">
    <h1>Revenue Breakdown Magnificent Seven</h1>
    <p>Grafik</p>
  </BaseCard>
  </div>

</template>

<style scoped>
.base-card{
display: flex;
flex-direction: column;
justify-content: center;
align-items: center;
}

.content-wrapper{
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 32px;
}
</style>
