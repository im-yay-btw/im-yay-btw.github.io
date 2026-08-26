<script lang="ts">
	let props = $props();
</script>

<section class={['relative min-h-screen p-6 lg:p-16', props.class]}>
	{#if props.header}
		<div class="mb-6 space-y-1 text-lg *:not-first:opacity-50 *:first:text-2xl lg:w-xl">
			{@render props.header?.()}
		</div>
	{/if}

	{@render props.children?.()}
</section>
