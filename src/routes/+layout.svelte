<script>
	import Header from '$lib/layout/Header.svelte';
	import Footer from '$lib/layout/Footer.svelte';
	import '$lib/styles/tailwind.css';
</script>

<svelte:head>
	<link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Caveat&display=swap" />
</svelte:head>

<main id="layout">
	<Header />
	<body>
		<slot />
	</body>
	<Footer />
</main>

<style lang="postcss">
	main {
		transition:
			background-color 0.2s ease-in-out,
			color 0.2s ease-in-out;
		font-family: 'Caveat';
		@apply bg-white dark:bg-black text-black dark:text-white text-center w-screen h-screen flex flex-col items-center justify-center gap-10;
	}
</style>
