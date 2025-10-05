<script lang="ts" module>
	import { defineMeta } from '@storybook/addon-svelte-csf';
	import CalendarDay from './CalendarDay.svelte';

	const { Story } = defineMeta({
		title: 'Design/Elements/CalendarDay',
		component: CalendarDay,
		argTypes: {},
		args: {}
	});
</script>

<Story name="CalendarDay" exportName="CalendarDayStory"></Story>
