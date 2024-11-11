<script lang="ts">
	import { Button } from '$lib/components/ui/button';
	import { ChevronLeft, ChevronRight, ClipboardCopy, Copy, Link } from 'lucide-svelte';

	interface Props {
		isExpanded: boolean;
		taskList: Readonly<TTaskList>;
	}

	let { isExpanded, taskList }: Props = $props();

	// task counts
	const total = taskList.tasks.length;
	const completed = taskList.tasks.filter((task) => task.status === 'Done').length;
	const highPriority = taskList.tasks.filter((task) => task.priority === 'High').length;
	const mediumPriority = taskList.tasks.filter((task) => task.priority === 'Medium').length;
	const lowPriority = taskList.tasks.filter((task) => task.priority === 'Low').length;
</script>

<div
	class={`border-l border-gray-200 dark:border-gray-700 ${isExpanded ? 'w-72' : 'w-16'} overflow-hidden transition-all duration-300 ease-in-out`}
>
	<div class={`flex items-center justify-between ${isExpanded && 'p-4'}`}>
		{#if isExpanded}
			<div class="text-lg font-semibold">Properties</div>
		{/if}
		<button onclick={() => (isExpanded = !isExpanded)}>
			<Button variant="ghost" size="icon" class={`${!isExpanded && 'h-16 w-16'}`}>
				{#if isExpanded}
					<ChevronRight class="h-4 w-4" />
				{:else}
					<ChevronLeft class="h-4 w-4" />
				{/if}
			</Button>
		</button>
	</div>
	{#if isExpanded}
		<div class="flex flex-col gap-4 px-4">
			<hr class="border-gray-200 dark:border-gray-700" />

			<!-- Task Progression -->
			<div class="flex flex-col gap-2">
				<div class="font-medium text-gray-500 dark:text-gray-400">Task Progression</div>
				<div class="text-sm">{completed} of {total} tasks completed</div>
			</div>
			<hr />

			<!-- Priority Breakdown -->
			<div class="flex flex-col gap-2">
				<div class="font-medium text-gray-500 dark:text-gray-400">Task Breakdown</div>
				<div class="flex flex-col gap-1">
					<div class="flex justify-between text-sm">
						<span>High</span>
						<span>{highPriority}</span>
					</div>
					<div class="flex justify-between text-sm">
						<span>Medium</span>
						<span>{mediumPriority}</span>
					</div>
					<div class="flex justify-between text-sm">
						<span>Low</span>
						<span>{lowPriority}</span>
					</div>
				</div>
			</div>
			<hr />

			<!-- Actions -->
			<div>
				<div class="mb-2 text-sm font-medium text-gray-500 dark:text-gray-400">Actions</div>
				<div class="flex flex-col gap-2">
					<Button variant="outline" class="w-full justify-start">
						<Link class="mr-2 h-4 w-4" />
						Copy List Link
					</Button>
					<Button variant="outline" class="w-full justify-start">
						<Copy class="mr-2 h-4 w-4" />
						Clone List
					</Button>
					<Button variant="outline" class="w-full justify-start">
						<ClipboardCopy class="mr-2 h-4 w-4" />
						Export as CSV
					</Button>
				</div>
			</div>
		</div>
	{/if}
</div>
