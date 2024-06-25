<script setup>
	import { Doughnut } from 'vue-chartjs';
	import ChartDataLabels from 'chartjs-plugin-datalabels';

	import {
		Chart as ChartJS,
		Title,
		Tooltip,
		Legend,
		ArcElement,
	} from 'chart.js';

	ChartJS.register(Title, Tooltip, Legend, ArcElement, ChartDataLabels);

	const { config } = defineProps(['config']);

	const chartData = ref({
		labels: config.labels,
		datasets: config.datasets,
	});

	const chartOptions = ref({
		responsive: true,
		maintainAspectRatio: true, // Allow custom dimensions

		plugins: {
			legend: {
				labels: {
					font: {
						weight: 'bold', // Increase font weight
						size: 12, // Increase font size
					},
				},
			},
			datalabels: {
				color: '#fff',
				font: {
					weight: 'bold',
					size: 14, // Optional: Adjust font size if needed
				},
				anchor: 'center',
				align: 'center',
				formatter: (value, context) => {
					const dataset = context.chart.data.datasets[0];
					const total = dataset.data.reduce((acc, value) => acc + value, 0);
					const percentage = ((value / total) * 100).toFixed(2);
					return `${percentage}%`;
				},
			},
		},
	});
</script>

<template>
	<Doughnut :data="chartData" :options="chartOptions" />
</template>
