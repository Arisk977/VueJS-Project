<script setup>
import BaseCard from './components/BaseCard.vue';
</script>

<template>
<BaseCard id="base-card">
    <h1>Überschrift</h1>
    <p>Dies ist ein Beispieltext, der in die Card-Komponente eingefügt wird.</p>
  </BaseCard>
</template>

<style scoped>
#base-card{
display: flex;
flex-direction: column;
justify-content: center;
align-items: center;
}
</style>
