<template>
	<div class="max-w-screen-xl mx-auto my-12">
		<div class="grid grid-cols-[65fr_35fr] gap-4">
			<div class="bg-white shadow-sm rounded-sm px-6 py-4">
				<h2 class="text-lg font-semibold text-gray-700">
					Open Position by Department
				</h2>
				<div class="w-3/5 mx-auto mt-3">
					<DepartmentDoughnut />
				</div>
			</div>
			<div class="bg-white shadow-sm rounded-sm px-6 py-4">
				<h2 class="text-lg font-semibold text-gray-700">Gender Ratio</h2>
				<div>
					<GenderDoughnut />
				</div>
			</div>
			<div class="bg-white shadow-sm rounded-sm px-6 py-4">
				<h2 class="text-lg font-semibold text-gray-700">Gender Ratio</h2>
				<div class="h-60">
					<ApplicationBar />
				</div>
			</div>
			<div class="bg-white shadow-sm rounded-sm px-6 py-4">
				<h2 class="text-lg font-semibold text-gray-700">
					Candidate Withdrawl Rate
				</h2>
				<div class="w-fit mx-auto">
					<WithdrawlMeter />
				</div>
			</div>
		</div>
	</div>
</template>
