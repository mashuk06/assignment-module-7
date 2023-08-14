<script setup>
  import { ref, onMounted, onBeforeUnmount } from 'vue'

  const newItem = ref(16)

  let chart = null

  const dataset = [
    300, 50, 100
  ]

  const data = {
    labels: [
      'Red',
      'Blue',
      'Yellow'
    ],
    datasets: [{
      label: 'My First Dataset',
      data: dataset,
      backgroundColor: [
        'rgb(255, 99, 132)',
        'rgb(54, 162, 235)',
        'rgb(255, 205, 86)',
        'rgb(43, 105, 86)',
        'rgb(21, 21, 186)',
      ],
      hoverOffset: 4
    }]
  };

  const config = {
    type: 'pie',
    data: data,
  };

  onMounted(() => {
    const ctx = document.getElementById('chart')
    chart = new Chart(ctx, config)
  })

  function updateChart() {
    if (chart) {
      dataset.push(newItem.value);
      chart.data.datasets[0].data = dataset;
      chart.update();
    }
  }

  onBeforeUnmount(() => {
    chart.destroy()
  })

</script>
<template>
  <div class="my-10 mx-5">
    <p>Pie Chart Component</p>
    <div class="chart-container mx-auto w-[400px] h-[400px] bg-gray-400">
      <div class="chart">
        <canvas id="chart"></canvas>
      </div>
      <div class="update-button">
        <div class="input-container">
          <input type="text" v-model="newItem" />
          <button @click="updateChart"
            class="update-btn ml-2 bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded">Add</button>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
  .chart-container {
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  .chart {
    margin-bottom: 20px;
  }

  .update-button {
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  .input-container {
    display: flex;
    align-items: center;
  }

  .input {
    margin-right: 10px;
  }

  .update-btn {
    background-color: #3490dc;
    color: white;
    border: none;
    padding: 8px 12px;
    border-radius: 4px;
    cursor: pointer;
    transition: background-color 0.3s;
  }

  .update-btn:hover {
    background-color: #2779bd;
  }
</style>
