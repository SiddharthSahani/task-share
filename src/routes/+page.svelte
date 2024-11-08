<script lang="ts">
	import TaskList from '$lib/components/task-list.svelte';
	import { SunMoonIcon } from 'lucide-svelte';

	let compactView = false;

	const tasks: TTask[] = [
		{
			title: 'User Registration',
			description: 'Create a registration page.',
			priority: 'High',
			status: 'Done'
		},
		{
			title: 'Database Setup',
			description:
				'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.',
			priority: 'Medium',
			status: 'In Progress'
		},
		{
			title: 'Password Reset',
			description: 'Implement password reset functionality.',
			priority: 'High',
			status: 'In Progress'
		},
		{
			title: 'User Testing',
			description: 'Gather feedback from users.',
			priority: 'Medium',
			status: 'In Progress'
		},
		{
			title: 'Performance Optimization',
			description:
				'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Vivamus luctus egestas leo, vel scelerisque nisl consectetur et.',
			priority: 'High',
			status: 'In Progress'
		},
		{
			title: 'UI Update',
			description: '',
			priority: 'Low',
			status: 'In Progress'
		},
		{
			title: 'Make the Button Bigger',
			description:
				"Because who doesn't love a giant button? Lorem ipsum dolor sit amet, consectetur adipiscing elit. Make it so big that users can't miss it!",
			priority: 'Low',
			status: 'Done'
		},
		{
			title: 'Add Confetti Animation',
			description:
				'Every time a user logs in, lets shower them with confetti! Who needs functionality when you have flair? Lorem ipsum dolor sit amet.',
			priority: 'Medium',
			status: 'Done'
		}
	];
</script>

<div class="flex justify-center gap-8 pt-4">
	<button
		class="flex items-center rounded-md border-[1.5px] border-black bg-slate-100 px-4 dark:border-white dark:bg-slate-900"
		on:click={() => document.documentElement.classList.toggle('dark')}
	>
		Toggle Theme
		<SunMoonIcon class="ml-2 h-8 w-8 p-1" />
	</button>
	<button
		class="rounded-md border-[1.5px] border-black bg-slate-100 px-4 dark:border-white dark:bg-slate-900"
		on:click={() => (compactView = !compactView)}
	>
		Toggle Compact View
	</button>
</div>
<TaskList {tasks} {compactView} />
