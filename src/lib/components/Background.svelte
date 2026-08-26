<script>
	let { ...props } = $props();
</script>

<video
	class="absolute top-0 left-0 -z-999 size-full mask-b-from-20% mask-b-to-80% object-cover opacity-15"
	volume={3 / 100}
	muted
	autoplay
	loop
	{...props}
></video>
