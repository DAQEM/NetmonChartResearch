<script>
	import ChartJsLineChart from '$lib/components/chart_js/ChartJSLineChart.svelte';
	import LayerCakeBarChart from '$lib/components/layer_cake/LayerCakeLineChart.svelte';
	import PancakeBarChart from '$lib/components/pancake/PancakeLineChart.svelte';
</script>

<div class="grid">
	<LayerCakeBarChart />
	<PancakeBarChart />
	<ChartJsLineChart />
</div>

<style>
	.grid {
		display: grid;
		gap: 50px;
		height: 90vh;
		grid-template-columns: repeat(3, 1fr);
	}
</style>
