<script setup>
	import { Bar } from 'vue-chartjs';
	import {
		Chart as ChartJS,
		Title,
		Tooltip,
		Legend,
		BarElement,
		CategoryScale,
		LinearScale,
	} from 'chart.js';

	ChartJS.register(
		Title,
		Tooltip,
		Legend,
		BarElement,
		CategoryScale,
		LinearScale
	);

	const { config } = defineProps(['config']);

	const chartData = ref({
		labels: config.labels,
		datasets: config.datasets,
	});

	const chartOptions = ref({
		responsive: true,
		maintainAspectRatio: false,

		scales: {
			x: {
				ticks: {
					font: {
						weight: 'bold', // Font weight of the labels
						size: 14, // Font size of the labels
					},
					color: '#444',
				},
			},
		},

		plugins: {
			legend: {
				labels: false,
			},
			datalabels: {
				color: '#fff', // Change the color of the bar labels
				font: {
					weight: 'bold',
					size: 14, // Adjust font size if needed
				},
			},
		},
	});
</script>

<template>
	<Bar id="my-chart-id" :options="chartOptions" :data="chartData" />
</template>
