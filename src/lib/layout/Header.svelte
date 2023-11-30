<script>
	import ThemeSwitcher from '$lib/components/ThemeSwitcher.svelte';
</script>

<header>
	<ThemeSwitcher />
	<h1>Henry Shi Jia Nguyen</h1>
</header>

<style lang="postcss">
	header {
		@apply flex flex-col items-center justify-center gap-2;
	}
	h1 {
		@apply text-center text-6xl;
	}
</style>
