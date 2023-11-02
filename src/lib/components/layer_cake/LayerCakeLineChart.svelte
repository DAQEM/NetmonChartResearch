<script lang="ts">
	import { LayerCake, Svg } from 'layercake';
	import AxisX from './components/AxisX.svelte';
	import AxisY from './components/AxisY.svelte';
	import Line from './components/Line.svelte';
	import Area from './components/Area.svelte';
	import interfaceDatasets from '$lib/datasets/interface';

	let x: string = 'date';
	let y: string = 'inOctets';
	let data: any[] = interfaceDatasets.map((data) => {
		return data.metrics;
	})[0];

	function formatX(value: number) {
		return new Date(value).toLocaleTimeString();
	}

	function formatY(value: number) {
		return value / 1000000;
	}
</script>

<LayerCake {x} {y} {data}>
	<Svg>
		<AxisX formatTick={formatX} />
		<AxisY formatTick={formatY} />
		<Line />
		<Area />
	</Svg>
</LayerCake>
