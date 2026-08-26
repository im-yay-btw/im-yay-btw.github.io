<script lang="ts">
	let { playlist = [''], play = $bindable(false) } = $props();

	let index = $state(0);
	let audio: HTMLAudioElement;

	let volume = $state(10.0);
	let muted = $state(false);

	function next() {
		audio.src = playlist[index];
		if (index >= playlist.length) index++;
		else index = 0;
	}

	$effect(() => {
		audio.src = playlist[index];
		if (play) audio.play();
		else audio.pause();

		if (audio.ended) next();
	});
</script>

<div class="fixed top-0 left-0 z-999 flex gap-2 p-4">
	<div
		class="group flex size-12 items-center gap-6 rounded-lg p-2 ring-2 ring-neutral-600/25 backdrop-blur-xs backdrop-brightness-80 transition-[width] duration-200 ease-in transform-content hover:w-auto"
	>
		<button class="text-2xl" aria-label="Volume toggle" onclick={() => (muted = !muted)}>
			<i class="ml-1 ri-volume-{!volume || muted ? 'mute' : volume <= 50.0 ? 'down' : 'up'}-fill"
			></i>
		</button>

		<input
			class="[&::-moz-range-thumb] mr-3 border-transparent transition-all duration-200 not-group-hover:transition-hidden [&::-moz-range-track]:bg-white/25"
			type="range"
			min="0"
			max="100"
			onpointerdown={() => (muted = false)}
			bind:value={volume}
		/>
	</div>

	<!-- <div
		class="flex h-12 items-center gap-3 rounded-lg p-4 ring-2 ring-neutral-600/25 backdrop-blur-xs backdrop-brightness-80"
	>
		<i class="ri-music-line"></i>
		<marquee class="max-w-36 truncate mask-x-from-90%" direction="left">
			Unknown by Artist 1, Artist 2 and Artist 3
		</marquee>

		<div class="flex gap-2">
			<button class="opacity-50" disabled aria-label="Back">
				<i class="ri-skip-back-fill"></i>
			</button>
			<button aria-label="Play/Pause" onclick={() => (play = !play)}>
				<i class="ri-{play ? 'play' : 'pause'}-fill"></i>
			</button>
			<button aria-label="Forward" onclick={() => next()}>
				<i class="ri-skip-forward-fill"></i>
			</button>
		</div>
	</div> -->
</div>

<audio bind:this={audio} volume={volume / 4 / 100} loop autoplay={play} {muted}> </audio>
