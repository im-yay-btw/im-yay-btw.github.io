<script>
	import { navigating } from '$app/state';
	let { clicked = $bindable() } = $props();
</script>

<div
	class="fixed top-0 left-0 z-999 flex size-full items-center justify-center bg-black/96 backdrop-blur-xs transition-block transition-all duration-200 ease-in-out"
	class:transition-hidden={clicked}
	role="presentation"
	onclick={() => (clicked = true)}
>
	<div>
		<p class="text-4xl">
			{#if navigating.complete}
				Loading
			{:else}
				Click to enter!
			{/if}
		</p>
	</div>
</div>
