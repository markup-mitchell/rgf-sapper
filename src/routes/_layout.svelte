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

	main {
		width: 100%;
		box-sizing: border-box;
		grid-column: 2/2;
		grid-row: 3;

	}

	.coffee-ring {
		position: fixed;
		top: -10%;
		right: -10rem;
		opacity: 0.3;
		z-index: -1;
	}



	@media (min-width: 640px) {
		.page-grid {
			grid-template-columns: 20px max-content 1fr 60px;
			align-items: start;
			grid-gap: 1rem;
		}
	}


	@media (min-width: 640px) {
		main {
			grid-column: 3;
			grid-row: 3;
		}
	}
	
</style>

<!-- <img class="coffee-ring" src="https://res.cloudinary.com/dthkwbvgt/image/upload/v1586371378/coffee__ring--transparent_a8y5x9.png" alt="coffee ring"> -->
<!-- <img class="shavings" src="https://res.cloudinary.com/dthkwbvgt/image/upload/v1586378624/shavings_ogvg1s.png" alt="pencil shavings" > -->
<div class="page-grid">
<Nav {segment}/>
<main>
	<slot></slot>
</main>

</div>