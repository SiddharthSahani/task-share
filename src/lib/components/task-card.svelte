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
		class={`flex-row items-center justify-between space-y-0 ${compactView ? 'py-2' : ''}`}
	>
		<CardTitle>
			<Checkbox />
			{task.title}
		</CardTitle>
		<div class="flex items-center gap-2">
			<Badge
				variant="outline"
				class={`${task.priortiy === 'High' ? 'bg-red-100 text-red-800' : task.priortiy === 'Medium' ? 'bg-yellow-100 text-yellow-800' : 'bg-green-100 text-green-800'}`}
			>
				{task.priortiy}
			</Badge>
			<Badge
				variant="outline"
				class={`${task.status === 'Done' ? 'bg-blue-100 text-blue-800' : task.priortiy === 'Medium' ? 'bg-purple-100 text-purple-800' : 'bg-grey-100 text-grey-800'}`}
			>
				{task.status}
			</Badge>
		</div>
	</CardHeader>
	{#if !compactView}
		<CardContent class="px-12 pb-2 pt-1 text-sm text-gray-800">
			{#if task.description}
				{task.description}
			{:else}
				<i>No description</i>
			{/if}
		</CardContent>
	{/if}
</Card>
