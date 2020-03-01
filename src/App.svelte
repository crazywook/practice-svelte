<script>
	import Todo from './pages/Todo.svelte'

	export let name
</script>

<main>
	<Todo />
</main>

<style>
	main {
		padding-top: 10rem;
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>