<script>
	import '../app.css'

	import Nav from '$lib/nav.svelte'
	import Footer from '$lib/footer.svelte'
</script>

<svelte:head>
	<title>SvelteKit Playground</title>
</svelte:head>

<body class="h-screen w-screen bg-slate-600">
	<Nav />

	<main class="max-w mx-auto bg-slate-600 px-4">
		<div class="bg-slate-800 pt-4 pb-12 font-semibold text-red-300">
			<slot />
		</div>
	</main>

	<Footer />
</body>
