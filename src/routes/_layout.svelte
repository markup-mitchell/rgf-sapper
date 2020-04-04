<script>
	import Nav from '../components/Nav.svelte';

	export let segment;
</script>

<style>
	/* .page-grid {
		display: grid;
		grid-template-columns: 40px 1fr 40px;
		grid-template-rows: min-content min-content;
	} */

	main {
		position: relative;
		margin: 40px auto;
		max-width: 56em;
		background-color: transparent;
		box-sizing: border-box;
		grid-column: 2;
		grid-row: 2;
	}
</style>

<Nav {segment}/>

<main>
	<slot></slot>
</main>
