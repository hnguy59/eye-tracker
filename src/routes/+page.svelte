<script>
	import Links from '$lib/components/Links.svelte';
	import LookingEyes from '$lib/components/LookingEyes.svelte';
</script>

<svelte:head>
	<title>Henry Nguyen</title>
	<meta name="description" content="Henry Nguyen" />
</svelte:head>

<div id="home">
	<LookingEyes />
	<Links />
</div>

<style lang="postcss">
	#home {
		@apply flex flex-col gap-5;
	}
</style>
