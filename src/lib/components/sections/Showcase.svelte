<script>
	import { REPOS } from '$lib/stores/github.svelte';
	import { motion } from '@humanspeak/svelte-motion';
	import Project from '../Project.svelte';
	import Section from './Section.svelte';
</script>

<Section class="-mt-24 space-y-16 lg:-mt-32">
	<div class="grid gap-2 md:grid-cols-2">
		{#each $REPOS
			?.sort((a, b) => b.stargazers_count - a.stargazers_count)
			.slice(0, 8) as repository (repository)}
			<div class="rounded-sm border-2 border-neutral-600/25 p-8">
				<a class="text-xl underline underline-offset-6" href={repository.html_url}>
					/{repository.name}
				</a>
				<p class="mb-6">
					{#if repository.description}
						{repository.description}
					{:else}
						<i class="opacity-50">No description</i>
					{/if}
				</p>

				<div class="space-x-4">
					{#if repository.language || repository.license}
						<div class="inline-flex space-x-3">
							{#if repository.language}
								<span>
									<img
										class="mr-1 inline size-4"
										src={`https://cdn.simpleicons.org/${repository.language}/_/white?viewbox=auto`}
										alt=""
									/>
									{repository.language}
								</span>
							{/if}

							{#if repository.license}
								<span>
									<i class="ri-scales-3-line"></i>
									{repository.license.name}
								</span>
							{/if}
						</div>
					{/if}

					<div class="inline-flex space-x-3 *:opacity-50 *:hover:opacity-100">
						<a href={undefined}>
							<i class="ri-star-line"></i>
							{repository.stargazers_count}
						</a>
						<a href={undefined}>
							<i class="ri-eye-line"></i>
							{repository.watchers}
						</a>
						<a href={undefined}>
							<i class="ri-git-fork-line"></i>
							{repository.forks_count}
						</a>
					</div>
				</div>
			</div>
		{/each}
	</div>

	<motion.div
		initial={{ opacity: 0, y: 28 }}
		whileInView={{ opacity: 1, y: 0 }}
		viewport={{ once: true, amount: 0.6, margin: '-48px' }}
		transition={{ duration: 0.6 }}
		class="flex gap-2 overflow-x-auto mask-r-from-80% pb-6 *:max-w-4xl *:shrink"
	>
		<Project
			link="https://im-yay-btw.io/"
			title="im-yay-btw.io"
			description=""
			stacks={['Svelte', 'TypeScript', 'TailwindCSS', 'Git']}
		/>
	</motion.div>

	<motion.div
		initial={{ opacity: 0, y: 28 }}
		whileInView={{ opacity: 1, y: 0 }}
		viewport={{ once: true, amount: 0.5 }}
		transition={{ duration: 0.6 }}
	>
		<p class="mb-8 text-3xl">Experiences</p>

		<ul class="sm:w-lg">
			<li class="relative pb-8 pl-8">
				<div class="absolute top-0 left-0 h-full w-px bg-neutral-800"></div>
				<div
					class="absolute top-1 -left-1.5 size-3 rounded-full border-2 border-neutral-800 bg-black"
				></div>

				<time>November 16st of 2023</time>
				<p class="mb-2 text-2xl">Eden Games</p>
				<p class="text-lg opacity-50">
					A short day of discovery within the company, it was fun, and made me even more intrested
					in creative fields of IT.
				</p>
			</li>

			<li class="relative pb-8 pl-8">
				<div
					class="absolute top-0 left-0 h-full w-px bg-linear-0 from-transparent to-neutral-800"
				></div>
				<div
					class="absolute top-1 -left-1.5 size-3 rounded-full border-2 border-neutral-800 bg-black"
				></div>

				<time>September 1st of 2026 - Now</time>
				<p class="mb-2 text-2xl">High School</p>
				<p class="text-lg opacity-50">
					<a
						class="underline decoration-dotted underline-offset-6"
						href="https://www.onisep.fr/ressources/univers-formation/formations/lycees/bac-pro-cybersecurite-informatique-et-reseaux-electronique"
					>
						Baccalauréat CIEL (Cybersecurity IT and Electronic)
					</a>
				</p>
			</li>
		</ul>
	</motion.div>
</Section>
