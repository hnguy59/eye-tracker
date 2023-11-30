<script lang="ts">
	import { createEventDispatcher } from 'svelte';

	const dispatch = createEventDispatcher();
	const links = [
		{
			title: 'CV',
			url: '/resume.pdf'
		},
		{ title: 'GitHub', url: 'https://github.com/hnguy59' },
		{ title: 'LinkedIn', url: 'https://www.linkedin.com/in/henry-nguyen-1a5980191/' },
		{ title: 'Email', url: 'mailto:riripishu@gmail.com' },
		{ title: 'Cats', url: 'https://www.instagram.com/apricot.taffy/' }
	];

	const handleMouseEnterLink = (type: string) => {
		switch (type) {
			case 'Cats':
				dispatch('updateCatImageEnter');
				break;
		}
	};

	const handleMouseLeaveLink = (type: string) => {
		switch (type) {
			case 'Cats':
				dispatch('updateCatImageLeave');
				break;
		}
	};
</script>

<div id="links">
	{#each links as { url, title } (title)}
		<a
			href={url}
			target="_blank"
			download={title === 'CV' ? 'Henry Nguyen Resume.pdf' : undefined}
			on:mouseenter={() => handleMouseEnterLink(title)}
			on:mouseleave={() => handleMouseLeaveLink(title)}><h2>{title}</h2></a
		>
	{/each}
</div>

<style lang="postcss">
	#links {
		@apply flex flex-row gap-10 items-center justify-center;
	}
	h2 {
		@apply text-center text-4xl;
	}
	a {
		@apply hover:underline;
	}
</style>
