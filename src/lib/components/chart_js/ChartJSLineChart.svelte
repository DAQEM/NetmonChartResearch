<script lang="ts">
	import { Line } from 'svelte-chartjs';

	import {
		Chart,
		Tooltip,
		LineElement,
		LinearScale,
		PointElement,
		CategoryScale,
		Filler
	} from 'chart.js';
	import interfaceDatasets from '$lib/datasets/interface';

	Chart.register(Tooltip, LineElement, LinearScale, PointElement, CategoryScale, Filler);

	const data: any = {
		labels: interfaceDatasets[0].metrics.map((data2) => data2.date.toLocaleTimeString()),
		datasets: [
			{
				label: 'In Octets',
				borderColor: 'rgba(0, 52, 131)',
				backgroundColor: 'rgba(0, 52, 131, 0.063)',
				fill: true,
				pointRadius: 0.0,
				pointHitRadius: 10,
				data: interfaceDatasets[0].metrics.map((data2) => data2.inOctets)
			}
		]
	};

	function formatY(label: number | string) {
		return (label as number) / 1000000;
	}
</script>

<Line
	{data}
	style="width: 100%; height: 100%"
	options={{
		scales: {
			x: {
				ticks: {
					maxTicksLimit: 8
				}
			},
			y: {
				ticks: {
					maxTicksLimit: 5,
					callback: formatY
				}
			}
		}
	}}
/>
