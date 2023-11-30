<script lang="ts">
	import angle1 from '$lib/images/1.jpg';
	import angle2 from '$lib/images/2.jpg';
	import angle3 from '$lib/images/3.jpg';
	import angle4 from '$lib/images/4.jpg';
	import angle5 from '$lib/images/5.jpg';
	import angle6 from '$lib/images/6.jpg';
	import angle7 from '$lib/images/7.jpg';
	import angle8 from '$lib/images/8.jpg';
	import angle9 from '$lib/images/9.jpg';
	import angle10 from '$lib/images/10.jpg';
	import angle11 from '$lib/images/11.jpg';
	import angle12 from '$lib/images/12.jpg';
	import angle13 from '$lib/images/13.jpg';
	import angle14 from '$lib/images/14.jpg';
	import angle15 from '$lib/images/15.jpg';
	import angle16 from '$lib/images/16.jpg';
	import henryCats from '$lib/images/HenryCats.jpg';
	import henryMiddle from '$lib/images/HenryMiddle.jpg';
	import { onMount } from 'svelte';

	let imageSrc = henryCats;

	function getImage(angle: number) {
		const sectionRadius = 360 / 16;

		if (angle < 5 * sectionRadius && angle >= 4 * sectionRadius) {
			return angle16;
		} else if (angle < 6 * sectionRadius && angle >= 5 * sectionRadius) {
			return angle15;
		} else if (angle < 7 * sectionRadius && angle >= 6 * sectionRadius) {
			return angle14;
		} else if (angle < 8 * sectionRadius && angle >= 7 * sectionRadius) {
			return angle13;
		} else if (angle < 4 * sectionRadius && angle >= 3 * sectionRadius) {
			return angle1;
		} else if (angle < 3 * sectionRadius && angle >= 2 * sectionRadius) {
			return angle2;
		} else if (angle < 2 * sectionRadius && angle >= sectionRadius) {
			return angle3;
		} else if (angle < sectionRadius && angle >= 0) {
			return angle4;
		} else if (angle < 0 && angle >= -sectionRadius) {
			return angle5;
		} else if (angle < -sectionRadius && angle >= 2 * -sectionRadius) {
			return angle6;
		} else if (angle < 2 * -sectionRadius && angle >= 3 * -sectionRadius) {
			return angle7;
		} else if (angle < 3 * -sectionRadius && angle >= 4 * -sectionRadius) {
			return angle8;
		} else if (angle < 4 * -sectionRadius && angle >= 5 * -sectionRadius) {
			return angle9;
		} else if (angle < 5 * -sectionRadius && angle >= 6 * -sectionRadius) {
			return angle10;
		} else if (angle < 6 * -sectionRadius && angle >= 7 * -sectionRadius) {
			return angle11;
		} else if (angle < 7 * -sectionRadius && angle >= 8 * -sectionRadius) {
			return angle12;
		} else {
			return henryCats;
		}
	}

	const handleMouseMove = (event: MouseEvent) => {
		const centerX = window.innerWidth / 2;
		const centerY = window.innerHeight / 2;
		const mouseX = event.clientX;
		const mouseY = event.clientY;
		const posX = mouseX - centerX;
		const posY = -(mouseY - centerY);
		const angleRadians = Math.atan2(posY, posX);
		const angle = (angleRadians * 180) / Math.PI;
		const isMouseInMiddle = posX < 20 && posX > -20 && posY < 20 && posY > -20;

		imageSrc = isMouseInMiddle ? henryMiddle : getImage(angle);
	};

	const handleSetImageToCats = () => {
		imageSrc = henryCats;
	};

	onMount(() => {
		window.addEventListener('mousemove', handleMouseMove);
		window.addEventListener('updateCatImageEnter', handleSetImageToCats);

		return () => {
			window.removeEventListener('mousemove', handleMouseMove);
			window.addEventListener('updateCatImageEnter', handleSetImageToCats);
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
