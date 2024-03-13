<script setup>
  import { getRelativePosition } from 'chart.js/helpers';
  import { ref, onMounted, watchEffect } from 'vue';
  import Chart from 'chart.js/auto';
  import "./../../../../css/app.css"
  import { Link } from '@inertiajs/vue3';

  const { dados } = defineProps({
    dados: Object
  });

  const chartCanvasLine = ref(null);
  const chartCanvasBar = ref(null);
  const chartType = ref('line');

  function showChart(type) {
    chartType.value = type;
  }

  onMounted(() => {
    watchEffect(() => {
      if (chartType.value === 'line' && chartCanvasLine.value) {
        const ctx = chartCanvasLine.value.getContext('2d');
        if (ctx) {
          new Chart(ctx, {
            type: 'line',
            data: dados,
            options: {
              onClick: (e, chart) => handleClick(e, chart)
            }
          });
        }
      } else if (chartType.value === 'bar' && chartCanvasBar.value) {
        const ctxBar = chartCanvasBar.value.getContext('2d');
        if (ctxBar) {
          new Chart(ctxBar, {
            type: 'bar',
            data: dados,
            options: {
              onClick: (e, chart) => handleClick(e, chart)
            }
          });
        }
      }
    });
  });

  function handleClick(e, chart) {
    const canvasPosition = getRelativePosition(e, chart);
    const dataX = chart.scales.x.getValueForPixel(canvasPosition.x);
    const dataY = chart.scales.y.getValueForPixel(canvasPosition.y);
    console.log('Clicked at:', { x: dataX, y: dataY });
  }
</script>

<template>
  <div
    class=" sm:flex sm:items-center sm:flex-col min-h-screen bg-dots-darker bg-center bg-gray-100 dark:bg-dots-lighter dark:bg-gray-900 selection:bg-red-500 selection:text-white">
    <div class="sm:flex w-full h-20 sm:items-center sm:flex-row p-4 justify-between">
      <div>
        <Link class="link" href="/">
        <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5"
          class="self-center shrink-0 stroke-red-500 w-6 h-6 mx-6" transform="rotate(180)">
          <path stroke-linecap="round" stroke-linejoin="round" d="M4.5 12h15m0 0l-6.75-6.75M19.5 12l-6.75 6.75" />
        </svg>
        <h2 class="text-xl font-bold text-white">Voltar para Home</h2>
        </Link>
      </div>
      <div>
        <Link class="link" href="/mapa">
        <h2 class="text-xl font-bold text-white">Ir para mapa</h2>
        <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5"
          class="self-center shrink-0 stroke-red-500 w-6 h-6 mx-6">
          <path stroke-linecap="round" stroke-linejoin="round" d="M4.5 12h15m0 0l-6.75-6.75M19.5 12l-6.75 6.75" />
        </svg>
        </Link>
      </div>
    </div>
    <h1 class="text-5xl font-bold text-white">
      Grafico
    </h1>
    <div class="max-w-7xl mx-auto p-6 lg:p-8">
      <canvas v-if="chartType === 'line'" ref="chartCanvasLine" width="500"></canvas>
      <canvas v-else-if="chartType === 'bar'" ref="chartCanvasBar" width="500"></canvas>
    </div>

    <div class="sm:flex sm:justify-center sm:item-center w-full lg:w-1/2">
      <button type="button" class="bg-red-500 hover:bg-red-700 text-white font-bold py-2 px-4 rounded m-2"
        @click="showChart('line')">Mostrar Gráfico de temperatura</button>
      <button type="button" class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded m-2"
        @click="showChart('bar')">Mostrar Gráfico de precipitação</button>

    </div>
  </div>
</template>
