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

	const chartData = ref({
		labels: ['Job Boards', 'Website', 'Social Media', 'Referral'],

		datasets: [
			{
				data: [31, 28, 21, 20],
				backgroundColor: ['#ff43a9'],
				barThickness: 40, // Decrease bar width (adjust as needed)
				data: [31, 28, 21, 20],
			},
		],
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
