<script setup>
	import {
		department,
		gender,
		application,
		withdrawl,
	} from '@/configs/charts.json';

	const percentage = ref(null);

	const getPercentage = (value) => {
		console.log(value);
		percentage.value = value;
	};
</script>

<template>
	<div class="max-w-screen-xl mx-auto my-12">
		<div class="grid grid-cols-[65fr_35fr] gap-4">
			<div class="bg-white shadow-sm rounded-sm px-6 py-4">
				<h2 class="text-lg font-semibold text-gray-700">
					Open Position by Department
				</h2>
				<div class="w-3/5 mx-auto mt-3">
					<DepartmentDoughnut :config="department" />
				</div>
			</div>
			<div class="bg-white shadow-sm rounded-sm px-6 py-4">
				<h2 class="text-lg font-semibold text-gray-700">Gender Ratio</h2>
				<div>
					<GenderDoughnut :config="gender" />
				</div>
			</div>
			<div class="bg-white shadow-sm rounded-sm px-6 py-4">
				<h2 class="text-lg font-semibold text-gray-700 mb-4">
					Application Received by Source
				</h2>
				<div class="h-60">
					<ApplicationBar :config="application" />
				</div>
			</div>
			<div class="bg-white shadow-sm rounded-sm px-6 py-4">
				<h2 class="text-lg font-semibold text-gray-700">
					Candidate Withdrawl Rate
				</h2>
				<div class="w-fit mx-auto">
					<WithdrawlMeter :config="withdrawl" @percentage="getPercentage" />
				</div>
				<!-- <div class="flex justify-center -mt-10">
					<p class="font-medium text-lg text-gray-700">{{ percentage }}</p>
				</div> -->
			</div>
		</div>
	</div>
</template>
