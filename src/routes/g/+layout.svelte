<script>
	let theme = 'light';
	import Icon from '@iconify/svelte/dist/OfflineIcon.svelte';
	import sun from '@iconify/icons-line-md/moon-alt-to-sunny-outline-loop-transition';
	import moon from '@iconify/icons-line-md/sunny-outline-to-moon-alt-loop-transition';
	import { onMount } from 'svelte';
	// Theme related code
	const toggleTheme = () => {
		let newTheme = theme === 'light' ? 'dark' : 'light';
		theme = newTheme;
		localStorage.setItem('theme', newTheme);
	};
	onMount(() => {
		let storedTheme = localStorage.getItem('theme');
		if (storedTheme) {
			theme = storedTheme;
		} else {
			localStorage.setItem('theme', 'light');
		}
	});

	export const prerender = true;
</script>

<body id={theme}>
	<header>
		<h1><a href="/">Gamezzz header</a></h1>
		<button on:click={toggleTheme}>
			<Icon inline icon={theme === 'light' ? sun : moon} width={36} />
		</button>
	</header>
	<slot />
</body>
