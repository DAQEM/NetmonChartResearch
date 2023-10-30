<script lang="ts">
	import { Line } from 'svelte-chartjs';

	import {
		Chart as ChartJS,
		Title,
		Tooltip,
		Legend,
		LineElement,
		LinearScale,
		PointElement,
		CategoryScale,
		Filler
	} from 'chart.js';
	import interfaceDatasets from '$lib/datasets/interface';
	import Area from '../layer_cake/components/Area.svelte';

	ChartJS.register(
		Title,
		Tooltip,
		Legend,
		LineElement,
		LinearScale,
		PointElement,
		CategoryScale,
		Filler
	);

	const data: any = {
		labels: interfaceDatasets[0].metrics.map((data2) => data2.date.toLocaleTimeString()),
		datasets: [
			{
				label: 'My Thrid dataset',
				fill: true,
				lineTension: 0,
				backgroundColor: 'rgba(184, 185, 210, .3)',
				borderColor: 'rgb(35, 26, 136)',
				borderCapStyle: 'butt',
				borderDash: [],
				borderDashOffset: 0.0,
				borderJoinStyle: 'miter',
				pointBorderColor: 'rgb(35, 26, 136)',
				pointBackgroundColor: 'rgb(255, 255, 255)',
				pointBorderWidth: 0.0,
				pointHoverRadius: 5,
				pointHoverBackgroundColor: 'rgb(0, 0, 0)',
				pointHoverBorderColor: 'rgba(220, 220, 220, 1)',
				pointHoverBorderWidth: 2,
				pointRadius: 0.0,
				pointHitRadius: 10,
				data: interfaceDatasets[0].metrics.map((data2) => data2.inOctets)
			}
		]
	};

	console.log(data.datasets[2]);
</script>

<div class="line">
	<Line {data} options={{ responsive: true, aspectRatio: 0.75 }} />
</div>

<style>
	.line {
		width: 100%;
		height: 100%;
	}
</style>
