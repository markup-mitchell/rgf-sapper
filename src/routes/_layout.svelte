<script>
	import Nav from '../components/Nav.svelte';

	export let segment;
</script>

<style>
	.page-grid {
		display: grid;
		grid-template-columns: 20px 1fr 20px;
		grid-auto-rows: max-content;
	}



	@media (min-width: 640px) {
		.page-grid {
			grid-template-columns: 20px max-content 1fr 80px;
			align-items: start;
			grid-gap: 1rem;
		}
	}

	main {
		width: 100%;
		box-sizing: border-box;
		grid-column: 2/2;
		grid-row: 3;

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