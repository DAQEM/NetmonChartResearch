<script lang="ts">
	import type { LayerCake } from 'layercake';
	import { getContext } from 'svelte';
	const { data, xGet, yGet }: LayerCake = getContext('LayerCake');

	export let stroke = '#003483';
	export let style = 'fill: none; stroke-linejoin: round; stroke-linecap: round; stroke-width: 3;';

	$: d = 'M' + $data.map((d: any) => $xGet(d) + ',' + $yGet(d)).join('L');
</script>

<path {style} {d} {stroke} />
