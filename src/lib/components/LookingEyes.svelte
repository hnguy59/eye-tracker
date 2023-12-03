<script lang="ts">
	import { onMount } from 'svelte';

	let imageSrc = '/images/HenryCats.jpg';

	function getImage(posX: number, posY: number) {
		const angleRadians = Math.atan2(posY, posX);
		const angle = (angleRadians * 180) / Math.PI;
		const isMouseInMiddle = posX < 20 && posX > -20 && posY < 20 && posY > -20;

		const sectionRadius = 360 / 16;

		if (isMouseInMiddle) {
			return '/images/HenryMiddle.jpg';
		} else if (angle < 5 * sectionRadius && angle >= 4 * sectionRadius) {
			return '/images/16.jpg';
		} else if (angle < 6 * sectionRadius && angle >= 5 * sectionRadius) {
			return '/images/15.jpg';
		} else if (angle < 7 * sectionRadius && angle >= 6 * sectionRadius) {
			return '/images/14.jpg';
		} else if (angle < 8 * sectionRadius && angle >= 7 * sectionRadius) {
			return '/images/13.jpg';
		} else if (angle < 4 * sectionRadius && angle >= 3 * sectionRadius) {
			return '/images/1.jpg';
		} else if (angle < 3 * sectionRadius && angle >= 2 * sectionRadius) {
			return '/images/2.jpg';
		} else if (angle < 2 * sectionRadius && angle >= sectionRadius) {
			return '/images/3.jpg';
		} else if (angle < sectionRadius && angle >= 0) {
			return '/images/4.jpg';
		} else if (angle < 0 && angle >= -sectionRadius) {
			return '/images/5.jpg';
		} else if (angle < -sectionRadius && angle >= 2 * -sectionRadius) {
			return '/images/6.jpg';
		} else if (angle < 2 * -sectionRadius && angle >= 3 * -sectionRadius) {
			return '/images/7.jpg';
		} else if (angle < 3 * -sectionRadius && angle >= 4 * -sectionRadius) {
			return '/images/8.jpg';
		} else if (angle < 4 * -sectionRadius && angle >= 5 * -sectionRadius) {
			return '/images/9.jpg';
		} else if (angle < 5 * -sectionRadius && angle >= 6 * -sectionRadius) {
			return '/images/10.jpg';
		} else if (angle < 6 * -sectionRadius && angle >= 7 * -sectionRadius) {
			return '/images/11.jpg';
		} else if (angle < 7 * -sectionRadius && angle >= 8 * -sectionRadius) {
			return '/images/12.jpg';
		} else {
			return '/images/HenryCats.jpg';
		}
	}

	const handleMouseMove = (event: MouseEvent) => {
		const centerX = window.innerWidth / 2;
		const centerY = window.innerHeight / 2;
		const mouseX = event.clientX;
		const mouseY = event.clientY;
		const posX = mouseX - centerX;
		const posY = -(mouseY - centerY);

		imageSrc = getImage(posX, posY);
	};

	onMount(() => {
		window.addEventListener('mousemove', handleMouseMove);

		return () => {
			window.removeEventListener('mousemove', handleMouseMove);
		};
	});
</script>

<div id="looking-eyes">
	<img src={imageSrc} alt="henry's face" />
</div>

<style lang="postcss">
	img {
		@apply max-w-xs m-auto aspect-square object-cover border-double border-8 border-black dark:border-white rounded;
	}
</style>
