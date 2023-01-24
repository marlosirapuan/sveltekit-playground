<script>
	import '../app.css'

	import Nav from '$lib/nav.svelte'
	import Footer from '$lib/footer.svelte'
</script>

<svelte:head>
	<title>SvelteKit Playground</title>
</svelte:head>

<Nav />

<main class="max-w mx-auto px-4">
	<div class="bg-slate-800 pt-4 pb-12 font-semibold text-red-300">
		<slot />
	</div>
</main>

<Footer />
