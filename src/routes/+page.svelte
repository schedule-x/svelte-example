<div>
	<ScheduleXCalendar calendarApp="{calendarApp}" timeGridEvent="{TimeGridEvent}" />
</div>

<script lang="ts">
	import { ScheduleXCalendar } from '@schedule-x/svelte';
	import { createCalendar, viewDay, viewWeek } from '@schedule-x/calendar';
	import '@schedule-x/theme-default/dist/index.css';
	import TimeGridEvent from '$lib/TimeGridEvent.svelte';

	const calendarApp = createCalendar({
		views: [viewDay, viewWeek],
		events: [
			{
				id: '1',
				title: 'Event 1',
				start: '2024-07-06',
				end: '2024-07-06',
			},
			{
				id: '2',
				title: 'Event 2',
				start: '2024-07-06 02:00',
				end: '2024-07-06 04:00',
			},
		]
	})
</script>
