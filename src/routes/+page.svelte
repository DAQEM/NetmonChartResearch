<script>
	import ChartJsLineChart from '$lib/components/chart_js/ChartJSLineChart.svelte';
	import LayerCakeBarChart from '$lib/components/layer_cake/LayerCakeLineChart.svelte';
	import PancakeBarChart from '$lib/components/pancake/PancakeLineChart.svelte';
	import interfaceDatasets from '$lib/datasets/interface';
</script>

<h1>Welcome to SvelteKit</h1>
<p>Visit <a href="https://kit.svelte.dev">kit.svelte.dev</a> to read the documentation</p>

<div class="grid">
	<LayerCakeBarChart
		x="date"
		y="inOctets"
		data={interfaceDatasets.map((data) => {
			return data.metrics;
		})[0]}
	/>
	<PancakeBarChart />
	<ChartJsLineChart />
</div>

<style>
	.grid {
		display: grid;
		margin: 100px;
		gap: 20px;
		grid-template-columns: repeat(3, 1fr);
	}
</style>
