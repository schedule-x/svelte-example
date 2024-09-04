<div>
	<ScheduleXCalendar calendarApp="{calendarApp}" timeGridEvent="{TimeGridEvent}" />

	<button on:click={addEvent}>add event</button>
</div>

<script lang="ts">
	import { ScheduleXCalendar } from '@schedule-x/svelte';
	import { createCalendar, viewDay, viewWeek } from '@schedule-x/calendar';
	import '@schedule-x/theme-default/dist/index.css';
	import TimeGridEvent from '$lib/TimeGridEvent.svelte';
	import { createEventsServicePlugin } from '@schedule-x/events-service';

	let eventsService = createEventsServicePlugin()

	const addEvent = () => {
		eventsService.add({
			id: '3',
			title: 'Event 3',
			start: '2024-09-06 06:00',
			end: '2024-09-06 08:00',
		})
	};

	const calendarApp = createCalendar({
		views: [viewDay, viewWeek],
		plugins: [eventsService],
		selectedDate: '2024-09-04',
		events: [
			{
				id: '1',
				title: 'Event 1',
				start: '2024-09-06',
				end: '2024-09-06',
			},
			{
				id: '2',
				title: 'Event 2',
				start: '2024-09-06 02:00',
				end: '2024-09-06 04:00',
			},
		]
	})
</script>
