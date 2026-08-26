<script>
	let { icon, size = 4, light = '_', dark = '_' } = $props();
</script>

<img
	class="inline size-{size}"
	src="https://cdn.simpleicons.org/{icon.replaceAll(' ', '')}/{light}/{dark}?viewbox=auto"
	alt={icon}
/>
