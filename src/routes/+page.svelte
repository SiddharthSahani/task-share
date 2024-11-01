<script lang="ts">
	import TaskCard from '$lib/components/task-card.svelte';

	const tasks: TTask[] = [
		{ title: 'task-1', description: 'some description', priortiy: 'Low', status: 'Todo' },
		{
			title: 'task-2',
			description:
				'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla et ligula elit. Ut suscipit nibh sit amet metus porta malesuada.',
			priortiy: 'Medium',
			status: 'In Progress'
		},
		{
			title: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit.',
			description: '',
			priortiy: 'High',
			status: 'Done'
		}
	];
</script>

{#each tasks as t}
	<TaskCard task={t} compactView={true} />
{/each}
<hr class="p-6" />
{#each tasks as t}
	<TaskCard task={t} compactView={false} />
{/each}
