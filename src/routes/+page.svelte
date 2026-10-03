<script lang="ts">
	import { ScheduleXCalendar } from '@schedule-x/svelte';
	import { createCalendar, viewDay, viewWeek } from '@schedule-x/calendar';
	import '@schedule-x/theme-default/dist/index.css';
	import TimeGridEvent from '$lib/TimeGridEvent.svelte';
	import { createEventsServicePlugin } from '@schedule-x/events-service';
	import ExampleShell from '$lib/ExampleShell.svelte';
	import '../app.css';
	import 'temporal-polyfill/global';
	import { Temporal } from 'temporal-polyfill';

	let eventsService = createEventsServicePlugin();

	const addEvent = () => {
		eventsService.add({
			id: '3',
			title: 'Event 3',
			start: Temporal.ZonedDateTime.from('2024-09-06T06:00:00+00:00[UTC]'),
			end: Temporal.ZonedDateTime.from('2024-09-06T08:00:00+00:00[UTC]')
		});
	};

	const calendarApp = createCalendar({
		views: [viewDay, viewWeek],
		plugins: [eventsService],
		selectedDate: Temporal.PlainDate.from('2024-09-04'),
		timezone: 'UTC',
		events: [
			{
				id: '1',
				title: 'Event 1',
				start: Temporal.PlainDate.from('2024-09-06'),
				end: Temporal.PlainDate.from('2024-09-06')
			},
			{
				id: '2',
				title: 'Event 2',
				start: Temporal.ZonedDateTime.from('2024-09-06T02:00:00+00:00[UTC]'),
				end: Temporal.ZonedDateTime.from('2024-09-06T04:00:00+00:00[UTC]')
			}
		]
	});
</script>

<ExampleShell demo="Svelte basics">
	<ScheduleXCalendar {calendarApp} timeGridEvent={TimeGridEvent} />

	<button on:click={addEvent}>add event</button>
</ExampleShell>
