<script lang="ts" module>
	import { flip } from 'svelte/animate';
	import { fade } from 'svelte/transition';

	export type Schedule = {
		label: string;
		start: number;
		end: number;
	};

	export interface CalendarDayProps {
		schedules: Schedule[];
	}

	const DAY_START = 8;
	const COLS = 10;
	const DAY_END = DAY_START + COLS; // = 18
</script>

<script>
	let props: CalendarDayProps = $props();

	function position(s: Schedule) {
		const start = Math.max(DAY_START, Math.min(DAY_END, s.start));
		const end = Math.max(DAY_START, Math.min(DAY_END, s.end));
		const total = DAY_END - DAY_START;

		const leftPct = ((start - DAY_START) / total) * 100;
		const widthPct = Math.max(0, ((end - start) / total) * 100);

		return `left:${leftPct + 1}%;width:${widthPct - 2}%`;
	}
</script>

<div class="relative h-full w-full">
	<div class="grid h-full grid-cols-10">
		{#each Array(10) as _, i}
			<div
				class="flex items-center justify-center overflow-hidden border-r border-gray-100 last:border-r-0"
			>
				<span class="overflow-hidden text-[clamp(0.4rem,0.9vw,1.0rem)] text-gray-300 select-none"
					>{8 + i}</span
				>
			</div>
		{/each}
	</div>
	{#each props.schedules as schedule, i}
		<div
			class="ease-ou absolute top-[2%] flex h-[96%] items-center justify-center overflow-hidden rounded-md bg-orange-400 p-1 text-xs text-white opacity-70 transition-all duration-300"
			style={position(schedule)}
			transition:fade
		>
			{schedule.label}
		</div>
	{/each}
</div>
