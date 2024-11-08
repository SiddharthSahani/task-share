<script lang="ts">
	import TaskCard from '$lib/components/task-card.svelte';
	import { ScrollArea } from '$lib/components/ui/scroll-area';
	import { Select, SelectContent, SelectItem, SelectTrigger } from '$lib/components/ui/select';
	import { SortAsc, SortDesc } from 'lucide-svelte';

	interface Props {
		tasks: TTask[];
		compactView?: boolean;
	}

	let { tasks, compactView }: Props = $props();
	const sortFilter = $state({
		sortBy: 'Priority',
		sortDirection: 'desc',
		statusFilter: ['In Progress', 'Done']
	});

	const visibleTasks = $derived(
		tasks
			.filter((task) => sortFilter.statusFilter.includes(task.status))
			.sort((a, b) => {
				if (sortFilter.sortBy === 'Priority') {
					const map = { Low: 0, Medium: 1, High: 2 };
					return (
						(map[a.priortiy] - map[b.priortiy]) * (sortFilter.sortDirection === 'desc' ? -1 : 1)
					);
				} else {
					const map = { 'In Progress': 1, Done: 0 };
					return (map[a.status] - map[b.status]) * (sortFilter.sortDirection === 'desc' ? -1 : 1);
				}
			})
	);
</script>

<div class="flex gap-4 p-4">
	<Select
		type="single"
		value={sortFilter.sortBy}
		onValueChange={(value: string) => (sortFilter.sortBy = value || sortFilter.sortBy)}
	>
		<SelectTrigger class="w-44">{sortFilter.sortBy}</SelectTrigger>
		<SelectContent>
			<SelectItem value="Priority">Priority</SelectItem>
			<SelectItem value="Status">Status</SelectItem>
		</SelectContent>
	</Select>
	<Select
		type="single"
		value={sortFilter.sortDirection}
		onValueChange={(value: string) =>
			(sortFilter.sortDirection = value || sortFilter.sortDirection)}
	>
		<SelectTrigger class="w-20">
			{#if sortFilter.sortDirection === 'desc'}
				<SortDesc />
			{:else}
				<SortAsc />
			{/if}
		</SelectTrigger>
		<SelectContent>
			<SelectItem value="desc"><SortDesc /></SelectItem>
			<SelectItem value="asc"><SortAsc /></SelectItem>
		</SelectContent>
	</Select>
	<Select
		type="multiple"
		value={sortFilter.statusFilter}
		onValueChange={(values: string[]) => (sortFilter.statusFilter = values)}
	>
		<SelectTrigger class="w-44">
			{#if sortFilter.statusFilter.length === 0}
				<i>No option is selected</i>
			{:else if sortFilter.statusFilter.length === 1}
				{sortFilter.statusFilter[0]}
			{:else}
				All
			{/if}
		</SelectTrigger>
		<SelectContent>
			<SelectItem value="In Progress">In Progress</SelectItem>
			<SelectItem value="Done">Done</SelectItem>
		</SelectContent>
	</Select>
</div>

<ScrollArea class="h-[calc(100vh-28rem)]">
	<div class="space-y-1">
		{#each visibleTasks as task}
			<TaskCard {task} {compactView} />
		{/each}
	</div>
</ScrollArea>
