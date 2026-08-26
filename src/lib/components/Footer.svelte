<script>
	import { HUB } from "$lib/stores/github.svelte";

</script>
<footer class="p-12">
    <p class="text-xl">Made with &lt;3</p>
    <p>© 2026 {$HUB?.login}. All rights reserved.</p>
</footer>
