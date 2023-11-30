<script lang="ts">
	import { browser } from '$app/environment';
	let darkMode = true;

	function handleSwitchDarkMode() {
		darkMode = !darkMode;

		localStorage.setItem('theme', darkMode ? 'dark' : 'light');

		darkMode
			? document.documentElement.classList.add('dark')
			: document.documentElement.classList.remove('dark');
	}

	if (browser) {
		if (
			localStorage.theme === 'dark' ||
			(!('theme' in localStorage) && window.matchMedia('(prefers-color-scheme: dark)').matches)
		) {
			document.documentElement.classList.add('dark');
			darkMode = true;
		} else {
			document.documentElement.classList.remove('dark');
			darkMode = false;
		}
	}
</script>

<div id="theme-toggle">
	<input
		checked={darkMode}
		on:click={handleSwitchDarkMode}
		type="checkbox"
		id="theme-toggle-input"
	/>
	<label for="theme-toggle-input" />
</div>

<style lang="postcss">
	#theme-toggle {
		@apply absolute top-4 right-4;
	}

	#theme-toggle-input {
		@apply invisible absolute;
	}

	#theme-toggle-input + label {
		@apply inline-block cursor-pointer h-8 w-8 rounded-full duration-300 content-[''];
	}

	#theme-toggle-input:not(:checked) + label {
		@apply bg-amber-400;
	}

	#theme-toggle-input:checked + label {
		@apply bg-transparent;
		box-shadow: inset -10px -8px 1px 1px #ddd;
	}
</style>
