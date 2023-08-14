<script setup>
  import CarouselComponent from './components/CarouselComponent.vue'
  import PieChartComponent from "./components/PieChartComponent.vue"
</script>

<template>
  <div class="flex">
    <CarouselComponent />
    <div class="divider"></div>
    <PieChartComponent />
  </div>
</template>

<style scoped>
  .flex {
    display: flex;
  }

  .divider {
    width: 2px;
    background-color: #ccc;
    margin: 20px 20px;
  }
</style>
