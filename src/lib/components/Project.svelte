<script>
	import Logos from './Logos.svelte';

	let {
		link = 'https://www.example.com/',
		// bg = '',
		title = 'Project',
		description = 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Assumenda ex minus accusantium sapiente illum, et amet, blanditiis doloribus vel atque magnam, voluptatibus facere at?',
		stacks = ['']
	} = $props();
</script>

<a
	href={link}
	class="group transform-all relative flex h-128 w-4xl items-end rounded-2xl border-2 border-neutral-600/25 p-6 transition-all duration-200 ease-in-out active:scale-98"
>
	<div
		class="transition-block absolute top-0 left-0 z-99 flex size-full items-center justify-center backdrop-brightness-25 transition-all duration-200 ease-in-out not-group-hover:transition-hidden"
	>
		<div>
			<p class="text-4xl">Visit</p>
		</div>
	</div>

	<div class="min:w-xs">
		<p class="text-4xl text-shadow-[0_0_12px]">{title}</p>
		<p class="mb-4">{description}</p>

		<div class="-mb-2 space-y-2">
			{#each stacks as stack (stack)}
				<span
					class="mr-2 inline-flex items-center gap-2 rounded-xs border-2 border-neutral-600 px-3.5 py-1 backdrop-blur-xs backdrop-brightness-80"
				>
					<Logos icon={stack} light="_" dark="white" />
					{stack}
				</span>
			{/each}
		</div>
	</div>
</a>
