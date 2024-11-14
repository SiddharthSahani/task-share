<script lang="ts">
	import { Badge } from '$lib/components/ui/badge';
	import { Card, CardContent, CardHeader, CardTitle } from '$lib/components/ui/card';
	import { Checkbox } from '$lib/components/ui/checkbox';

	interface Props {
		task: TTask;
		compactView?: boolean;
	}

	let { task, compactView = false }: Props = $props();
</script>

<Card class="flex flex-col gap-4 p-4">
	<CardHeader class="flex-row items-center justify-between space-y-0 p-0">
		<CardTitle>
			<Checkbox class="mr-1 size-5" />
			{task.title}
		</CardTitle>
		<div class="flex items-center gap-2">
			<Badge
				variant="outline"
				class={`${task.priority === 'High' ? 'bg-red-100 text-red-800 dark:bg-red-900 dark:text-red-200' : task.priority === 'Medium' ? 'bg-yellow-100 text-yellow-800 dark:bg-yellow-900 dark:text-yellow-200' : 'bg-green-100 text-green-800 dark:bg-green-900 dark:text-green-200'}`}
			>
				{task.priority}
			</Badge>
			<Badge
				variant="outline"
				class={`${task.status === 'Done' ? 'bg-blue-100 text-blue-800 dark:bg-blue-900 dark:text-blue-200' : 'bg-purple-100 text-purple-800 dark:bg-purple-900 dark:text-purple-200'}`}
			>
				{task.status}
			</Badge>
		</div>
	</CardHeader>

	<div
		class={`transition-all duration-500 ease-linear ${compactView ? 'max-h-0 opacity-0' : 'max-h-16 opacity-100'}`}
	>
		<CardContent class="p -mt-2 p-0 px-1 pb-2 text-sm text-gray-800 dark:text-gray-400">
			{#if task.description}
				{task.description}
			{:else}
				<i class="opacity-60">No description</i>
			{/if}
		</CardContent>
	</div>
</Card>
