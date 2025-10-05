<script lang="ts" module>
	import { defineMeta } from '@storybook/addon-svelte-csf';
	import Calendar from './Calendar.svelte';

	const { Story } = defineMeta({
		title: 'Design/Elements/Calendar',
		component: Calendar,
		argTypes: {},
		args: {
			schedules: [
				{
					label: 'Repair',
					technician: 'Bob',
					day: 'Mo',
					start: 8.75,
					end: 11
				},
				{
					label: 'Windows',
					technician: 'Fred',
					day: 'Mo',
					start: 12.5,
					end: 16
				},
				{
					label: 'Windows',
					technician: 'Fred',
					day: 'Mo',
					start: 16,
					end: 17.5
				},
				{
					label: 'house',
					technician: 'Susi',
					day: 'Wed',
					start: 9,
					end: 16
				},
				{
					label: 'house',
					technician: 'Fred',
					day: 'Wed',
					start: 9,
					end: 16
				}
			]
		}
	});
</script>

<Story name="Calendar" exportName="CalendarStory"></Story>
