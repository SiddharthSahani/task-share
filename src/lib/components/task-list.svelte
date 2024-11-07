<script lang="ts">
	import TaskCard from '$lib/components/task-card.svelte';
	import { ScrollArea } from '$lib/components/ui/scroll-area';

	interface Props {
		tasks: TTask[];
		compactView?: boolean;
	}

	let { tasks, compactView }: Props = $props();
</script>

<ScrollArea class="h-[calc(100vh-28rem)]">
	<div class="space-y-1">
		{#each tasks as task}
			<TaskCard {task} {compactView} />
		{/each}
	</div>
</ScrollArea>
