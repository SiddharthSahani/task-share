<script lang="ts">
	import TaskCard from '$lib/components/task-card.svelte';
	import TaskList from '$lib/components/task-list.svelte';

	let tasks: TTask[] = [
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

	tasks.push(...tasks);
	tasks.push(...tasks);
</script>

<TaskList {tasks} compactView={false} />
<hr class="py-4" />
<TaskList {tasks} compactView={true} />
