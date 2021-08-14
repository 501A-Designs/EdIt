<script lang="ts">
	import logo from "./assets/svelte.png";
	import Editor from "./lib/Editor.svelte";
</script>

<main>
	<!-- <img src={logo} alt="Svelte Logo" /> -->
	<header>
		<h1>EdIt</h1>
		<h2>Blazing quick image edits ⚡</h2>
	</header>
	<Editor />
	<footer>
		<p>Design And Developed By 501A</p>
	</footer>
</main>

<style>
	@import "./styles.css";
	:root {
		font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen,
			Ubuntu, Cantarell, "Open Sans", "Helvetica Neue", sans-serif;
	}
	main {
		margin: 0 10%;
	}

	header h1 {
		font-weight: bold;
		margin-bottom: 0;
		font-size: 4rem;
	}
	header h2 {
		color: var(--editGrey);
		font-style: italic;
		margin-top: 0;
	}
	footer {
		position: sticky;

		bottom: 1em;
	}
</style>
