<script lang="ts">
	interface Props {
		isExpanded: boolean;
	}

	let { isExpanded }: Props = $props();
</script>

<div class={`flex ${isExpanded ? 'w-64' : 'w-16'} items-center justify-center rounded-lg border-2`}>
	{#if isExpanded}
		Property Bar
	{:else}
		PB
	{/if}
</div>
