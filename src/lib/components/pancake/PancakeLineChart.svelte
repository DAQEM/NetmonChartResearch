<script lang="ts">
	//@ts-ignore
	import * as Pancake from '@sveltejs/pancake';
	import interfaceDatasets from '$lib/datasets/interface.js';

	const dataset = interfaceDatasets[0].metrics.map((data) => ({ x: data.date, y: data.inOctets }));

	let x1 = +Infinity;
	let x2 = -Infinity;
	let y1 = +Infinity;
	let y2 = -Infinity;

	dataset.forEach((d: any) => {
		if (d.x < x1) x1 = d.x;
		if (d.x > x2) x2 = d.x;
		if (d.y < y1) y1 = d.y;
		if (d.y > y2) y2 = d.y;
	});
</script>

<Pancake.Chart {x1} {x2} {y1} {y2}>
	<Pancake.Grid horizontal count={5} let:value>
		<div class="grid-line horizontal"><span>{value / 1000000}</span></div>
	</Pancake.Grid>

	<Pancake.Grid vertical count={5} let:value>
		<span class="x-label">{new Date(value).toLocaleTimeString()}</span>
	</Pancake.Grid>

	<Pancake.Svg>
		<Pancake.SvgArea data={dataset} let:d floor={dataset[0].y}>
			<path class="area" {d} />
		</Pancake.SvgArea>
		<Pancake.SvgLine data={dataset} let:d>
			<path class="data" {d} />
		</Pancake.SvgLine>
	</Pancake.Svg>
</Pancake.Chart>

<style>
	.grid-line {
		position: relative;
		display: block;
	}

	.grid-line.horizontal {
		width: calc(100% + 2em);
		left: -2em;
		border-bottom: 1px dashed #ccc;
	}

	.grid-line span {
		position: absolute;
		left: 0;
		bottom: 2px;
		font-family: sans-serif;
		font-size: 14px;
		color: #999;
	}

	.x-label {
		position: absolute;
		/* width: 4em; */
		/* left: -2em; */
		bottom: -22px;
		font-family: sans-serif;
		font-size: 14px;
		color: #999;
		text-align: center;
	}

	path.data {
		stroke: rgb(0, 52, 131);
		stroke-linejoin: round;
		stroke-linecap: round;
		stroke-width: 2px;
		fill: none;
	}

	.area {
		fill: rgba(0, 52, 131, 0.063) !important;
		box-sizing: border-box;
		vector-effect: none;
	}
</style>
