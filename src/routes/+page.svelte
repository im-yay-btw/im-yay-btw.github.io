<script>
	import Background from '$lib/components/Background.svelte';
	import Loading from '$lib/components/Loading.svelte';
	import Player from '$lib/components/Player.svelte';
	import Showcase from '$lib/components/sections/Showcase.svelte';
	import { DISCORD_ID } from '$lib';
	import { HUB } from '$lib/stores/github.svelte';

	let ready = $state(false);
</script>

<Loading bind:clicked={ready} />

<Player playlist={['bg-music-1.mp3', 'bg-music-2.mp3', 'bg-music-3.mp3']} play={ready} />

<Background src="bg-movie-1.mp4" autoplay={ready} />

<div class="flex min-h-screen items-center justify-center p-8">
	<div class="flex gap-24 not-sm:w-full not-lg:flex-col">
		<div>
			<p class="text-4xl text-shadow-[0_0_12px]">{$HUB?.login}</p>
			<p class="mb-4 text-xl font-light">Junior developer</p>

			<div class="mb-6 space-x-3">
				<a href="https://discord.com/users/{DISCORD_ID}" aria-label="Discord link">
					<i class="ri-discord-fill"></i>
				</a>

				<a href="https://figma.com/@im_yay_btw/" aria-label="Figma link">
					<i class="ri-figma-line"></i>
				</a>

				<a href="mailto:{$HUB?.email}" aria-label="E-Mail link">
					<i class="ri-mail-line"></i>
				</a>
			</div>

			<ul class="space-y-6 sm:w-xs">
				<p class="mb-12">
					Hello, I am a fifteen-year-old developer and I love exploring fields of programming and
					digital arts.
				</p>

				<li>
					<p><i class="ri-map-line mr-1"></i> Location</p>
					<p class="text-lg">
						{$HUB?.location}
					</p>
				</li>

				<li>
					<p><i class="ri-user-3-line mr-1"></i> Availabilities</p>
					<p class="text-lg">
						{#if $HUB?.hireable}
							<span class="relative mr-2 inline-flex size-3">
								<span
									class="absolute inline-flex h-full w-full animate-ping rounded-full bg-radial from-green-500 to-transparent"
								></span>
								<span class="relative inline-flex size-3 rounded-full bg-green-500"></span>
							</span>
							Actively looking for opportunities
						{:else}
							<i class="opacity-50">Not looking for opportunities</i>
						{/if}
					</p>
				</li>
			</ul>
		</div>

		<div class="not-md:hidden">
			<div class="flex size-full items-center">
				<div class="flex w-lg flex-col items-center text-center">
					<p class="mb-6 text-6xl text-shadow-[0_0_12px]">/ᐠ - ˕ -マ ᶻ 𝗓 𐰁</p>

					<p class="mb-8 w-xs opacity-50">
						“Well... I'm not working today, sorry, come back tomorrow...” - The cat
					</p>
				</div>
			</div>
		</div>
	</div>
</div>

<Showcase />
