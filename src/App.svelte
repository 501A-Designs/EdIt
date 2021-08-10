<script lang="ts">
	import logo from "./assets/svelte.png";
	import Counter from "./lib/Counter.svelte";
</script>

<main>
	<!-- <img src={logo} alt="Svelte Logo" /> -->
	<header>
		<h1>EdIt</h1>
		<p>By 501A</p>
	</header>

	<Counter />
	<p>
		Check out <a href="https://github.com/sveltejs/kit#readme">SvelteKit</a> for
		the officially supported framework, also powered by Vite!
	</p>
</main>

<style>
	:root {
		font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen,
			Ubuntu, Cantarell, "Open Sans", "Helvetica Neue", sans-serif;
	}
	main {
		margin: 0 10%;
	}

	header {
		display: flex;
		align-items: center;
		flex-direction: column;
		justify-content: center;
		border: 10px solid black;
	}
	header h1 {
		font-weight: bold;
		margin-bottom: 0;
		font-size: 4rem;
	}
</style>
