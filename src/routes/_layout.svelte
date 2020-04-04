<script>
	import Nav from '../components/Nav.svelte';
	export let segment;
</script>

<style>
	.page-grid {
		display: grid;
		grid-template-columns: 20px 1fr 20px;
		/* grid-template-rows: ; */
		grid-auto-rows: min-content;

		
	}

	@media (min-width: 640px) {
		.page-grid {
			grid-template-columns: 20px max-content 1fr 40px;
			align-items: start;
		grid-gap: 1rem;
		}
	}

	main {
		position: relative;
		width: 100%;
		max-width: 28em;
		background-color: transparent;
		box-sizing: border-box;
		grid-column: 2/2;
		grid-row: 3;
		/* text-align: justify; */
		letter-spacing: 1px;
		line-height: 1.5;
	}
	@media (min-width: 640px) {
		main {
			grid-column: 3;
			grid-row: 3;
	}
	}
</style>

<div class="page-grid">
<Nav {segment}/>

<main>
	<slot></slot>
</main>

</div>