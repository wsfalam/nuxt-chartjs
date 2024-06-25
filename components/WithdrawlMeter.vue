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
	const emit = defineEmits(['percentage']);

	const modifiedDatasets = config.datasets.map((dataset) => {
		if (typeof dataset.data === 'number') {
			const percentage = ((dataset.data / 100) * 100).toFixed(2);
			emit('percentage', `${percentage}%`);

			return {
				...dataset,
				data: [dataset.data, 100 - dataset.data],
			};
		}
		return dataset; // return unchanged if data property is missing or not an array
	});

	const chartData = ref({
		datasets: modifiedDatasets,
	});

	const chartOptions = ref({
		responsive: true,
		maintainAspectRatio: false, // Allow custom dimensions

		plugins: {
			legend: {
				labels: false,
			},
			datalabels: {
				color: '#444',
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
