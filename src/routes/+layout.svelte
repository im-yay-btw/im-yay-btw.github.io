<script lang="ts">
	import './layout.css';
	import favicon from '$lib/assets/favicon.png';
	import Footer from '$lib/components/Footer.svelte';

	let { children } = $props();
</script>

<svelte:head>
	<title>im-yay-btw.io</title>
	<link rel="icon" href={favicon} />
</svelte:head>
{@render children()}

<Footer />
