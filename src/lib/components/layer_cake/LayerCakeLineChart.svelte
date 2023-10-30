<script lang="ts">
	import { LayerCake, Svg } from 'layercake';
	import AxisX from './components/AxisX.svelte';
	import AxisY from './components/AxisY.svelte';
	import Line from './components/Line.svelte';

	export let x: string;
	export let y: string;
	export let data: any[];
</script>

<div class="chart-container">
	<LayerCake {x} {y} {data}>
		<Svg>
			<AxisX />
			<AxisY />
			<Line stroke="#f0c" />
		</Svg>
	</LayerCake>
</div>

<style>
	.chart-container {
		width: 100%;
		height: 500px;
	}
</style>
