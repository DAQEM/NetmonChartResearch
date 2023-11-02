<script lang="ts">
	import type { LayerCake } from 'layercake';
	import { getContext } from 'svelte';
	const { data, xGet, yGet, xScale, yScale, extents }: LayerCake = getContext('LayerCake');
	export let fill = '#00348310';

	$: path =
		'M' +
		$data
			.map((d: any) => {
				return $xGet(d) + ',' + $yGet(d);
			})
			.join('L');

	let d: string;

	$: {
		const yRange = $yScale.range();
		d =
			path +
			('L' +
				$xScale($extents.x ? $extents.x[1] : 0) +
				',' +
				yRange[0] +
				'L' +
				$xScale($extents.x ? $extents.x[0] : 0) +
				',' +
				yRange[0] +
				'Z');
	}
</script>

<path {d} {fill} />
