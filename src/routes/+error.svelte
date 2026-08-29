<script>
	import { page } from '$app/state';
</script>

<div class="flex min-h-screen items-center justify-center">
	<div class="text-center">
		<div class="mb-8 flex">
			{#each String(page.status) as item, i (i)}
				<img src={`digits/${item}.gif`} alt={item} title={item} />
			{/each}
		</div>
		<h1 class="mb-1 text-5xl">{page.status}</h1>
		<h1 class="text-2xl opacity-50">{page.error?.message}</h1>
	</div>
</div>
