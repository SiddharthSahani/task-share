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

<Card>
	<CardHeader
		class={`flex-row items-center justify-between space-y-0 ${compactView ? 'py-4' : ''}`}
	>
		<CardTitle>
			<Checkbox />
			{task.title}
		</CardTitle>
		<div class="flex items-center gap-2">
			<Badge
				variant="outline"
				class={`${task.priortiy === 'High' ? 'bg-red-100 text-red-800 dark:bg-red-900 dark:text-red-200' : task.priortiy === 'Medium' ? 'bg-yellow-100 text-yellow-800 dark:bg-yellow-900 dark:text-yellow-200' : 'bg-green-100 text-green-800 dark:bg-green-900 dark:text-green-200'}`}
			>
				{task.priortiy}
			</Badge>
			<Badge
				variant="outline"
				class={`${task.status === 'Done' ? 'bg-blue-100 text-blue-800 dark:bg-blue-900 dark:text-blue-200' : 'bg-purple-100 text-purple-800 dark:bg-purple-900 dark:text-purple-200'}`}
			>
				{task.status}
			</Badge>
		</div>
	</CardHeader>
	{#if !compactView}
		<CardContent class="px-12 pb-2 pt-1 text-sm text-gray-800 dark:text-gray-400">
			{#if task.description}
				{task.description}
			{:else}
				<i class="opacity-60">No description</i>
			{/if}
		</CardContent>
	{/if}
</Card>
