<template>
  <div>
    <canvas id="statistik"></canvas>
  </div>  
</template>

<script setup>
import Chart from 'chart.js/auto';

const labels = [
  'January',
  'February',
  'March',
  'April',
  'May',
  'June',
];

const data = {
  labels: labels,
  datasets: [{
    label: 'Pengunjung',
    backgroundColor: [ 
      'rgb(153, 171, 41)',
      'rgb(29, 46, 16)',
      'rgb(197, 43, 43)',
      'rgb(91, 7, 7)',
      'rgb(197, 16, 16)',
      'rgb(39, 177, 255)',
    ],
    borderColor: 'rgb(255, 100, 132)',
    data: [15, 18, 20, 17, 17, 18],
  }]
};

const config = {
  type: 'bar',
  data: data,
  options: {}
};

onMounted(() => {
  const myChart = new Chart(
  document.getElementById('statistik'),
  config
);
})
</script>