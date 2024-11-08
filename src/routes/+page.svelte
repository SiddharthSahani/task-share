<script lang="ts">
	import TaskList from '$lib/components/task-list.svelte';

	const tasks: TTask[] = [
		{ title: 'task-1', description: 'some description', priortiy: 'Low', status: 'In Progress' },
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
		},
		{
			title: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit.',
			description: '',
			priortiy: 'Low',
			status: 'Done'
		}
	];
</script>

<TaskList {tasks} compactView={false} />
<hr class="py-4" />
<TaskList {tasks} compactView={true} />
