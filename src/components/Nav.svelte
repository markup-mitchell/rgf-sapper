<script>
	export let segment;
</script>

<style>
	/* .circle {
		width: 6rem;
		height: 6rem;
		border-radius: 50%;
		background-color: #333;
		position: fixed;
		top: -2rem;
		left: -1rem;
} */
	nav {
		grid-column: 2;
		grid-row: 2 ;
		padding-top: 0.5rem;
		position: sticky;
		top: 0;
		z-index: 8;
	}

	

	svg {
		width: 30px;
		height: auto;
		fill: #333;
		/* stroke-width: 5px; */
		stroke: #333;
		transition: all 0.3s ease-in-out;
		mix-blend-mode: difference;
	}


	svg:hover {
		/* fill: white; */
		transition: all 0.2s ease-in-out;
		transform: scale(1.1);
	}

	ul {
		margin: 0;
		padding: 0;
	}

	/* clearfix */
	ul::after {
		content: '';
		display: block;
		clear: both;
	}

	li {
		display: block;
		float: left;
	}

	a {
		text-decoration: none;
		display: block;
	}
	@media (min-width: 640px) {
		nav {
			grid-row: 2;
			grid-column: 2;
		}
		svg {
			width: 45px;
		}
	}
</style>

<nav>
	<ul>
		<li><a aria-current='{segment === undefined ? "page" : undefined}' href='.'>
		<!-- <div class="circle"></div> -->
		<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 462.408 605.663"><path d="M249.546 122.08c9.16-3.95 15.07-7.36 21.82-15 17.93-20.31 18.43-53.65 4.09-76-5.96-9.3-14.19-16.49-23.91-21.68-20.47-10.91-43.66-9.32-66-9.32h-105c-3.68.01-7.62-.23-10.79 2.01-5.16 3.64-6.12 16.31-4.49 21.99 2.48 8.62 9.6 7.37 14.06 11.42 4.75 4.3 5.21 13.55 5.22 19.58v103c-.1 8.64-1.85 29.64-5.56 37-4.87 9.69-13.46 7.64-14.35 22-.8 12.93 3.94 18.94 16.91 19h104c3.14-.01 7.11.3 9.72-1.74 4.93-3.84 3.87-20.09 1.36-25.24-4.42-9.07-10.88-4.94-18.04-11.24-8.4-7.4-9.91-23.1-10.04-33.78v-4c.05-3.72 1.06-14.93 2.57-17.98 1.43-2.9 3.93-5.63 7.42-4.06 73.82 69.86 71.477 132.808 80.991 190.493 2.4 8.593 7.46 18.058 12.9 18.15 2.35 1 5.43.85 7.96.85h47c14.17 0 30.33 1.63 37.48-14 1.37-3 2.04-5.77 2.39-9 .78-4.38 1.63-8.62 0-12.89-2.13-4.85-8.49-5.44-12.87-7.18-4.86-1.92-7.33-4.11-10.83-7.93-20.087-59.115-33.55-116.793-94.011-174.452zm-71-82.23c30.81 1.52 30.61 59.02-1 57.58-8.55-.39-8.97-12.98-9-19.35-.03-7.17-.49-20.52.81-27 1.22-6.09 2.5-10.1 9.19-11.23zM100.99 258.578c-23.47 3.55-43.64 8.36-62 24.75-22.3 19.91-35.01 49.36-37.96 78.83v8l-1.03 9 .9 13c1.15 16.74 3.19 29.26 9.49 45 6.01 15.01 16.39 33.04 28.6 43.71 16.7 14.6 41.87 23.26 64 23.29h19c26.32-.31 50.65-12.04 76-17.19l22-2.53c3.61-.47 6.79-.44 9.78-2.93 5.17-4.31 4.23-14.21 4.22-20.35l-1-17v-25c.09-12.64 30.995-15.047 34.355-11.177 2.84 3.26 3.83 19.85 3.89 24.67v99l-.91 12c-.5 7.29.07 14.38-4.08 21-4.67 7.43-10.58 7.05-14.5 12.1-3.02 3.89-2.56 9.24-2.51 13.9.17 13.63 8.36 14.98 20 15h109c3.57-.01 7.79.38 10.49-2.43 2.95-3.07 2.51-8.6 2.51-12.57 0-2.98.1-6.13-.8-9-3.88-12.31-19.35-8.57-26.81-16.34-3.13-3.26-4.67-9.3-5.59-13.66-2-9.51-3.5-23.41-2.22-33 .5-3.75.36-8.7 2.35-11.95 4.21-6.84 12.29-4.62 16.42.99 5.96 8.09 1.72 25.67 14.65 30.35 14.81 5.35 22.93-2.6 23-17.39l-1-36 1-16v-18c-.07-4.64-.47-8.17-4.21-11.44-7.21-6.31-21.3-5.66-27.14 2.46-3.95 5.46-3.2 10.91-9.74 16.75-1.25 1.12-2.36 1.89-3.91 2.53-9.31 3.84-10.44-3.51-11.16-10.3l-.84-9c-.07-6.49 0-22.03 4.42-26.73 3.85-4.09 9.49-3.93 14.58-4.44 11.55-1.15 32.12-.57 42 6.02 4.36 2.91 8.43 7.33 10.53 12.15 2.3 5.25 5.08 15.89 8.86 19.61 5.36 5.28 21.39 5.16 24.91-2.65 3.75-8.32.71-24.73.7-33.96v-21c-.01-5.31-.06-13.77-4.23-17.58-6.26-5.75-19-3.43-26.77-3.42h-39c-83.292.104-167.537-.493-249.245-.493-4.91.01-8.88-.18-12.79 3.39-5.72 5.23-5.89 20.78-.93 26.52 6.92 8.01 14.46 5.96 18.57 12.15 2.48 3.72 3.09 10.51 3.15 14.94.06 5.5-.22 22.77-3.01 26.81-3.17 4.61-7.96 4.9-12.99 4.3-11.2-1.33-18.5-7.19-25.08-16.11-11.79-15.99-15.58-41.51-17.01-61l-.91-10v-12c.04-24 9.27-57.05 38-58.63 3.74-.2 16.08 1.18 20 2.05 8 1.79 13.17 3.64 20 8.25 11.2 7.55 17.31 16.93 25.42 27.33 4.78 6.11 10.01 12.74 18.58 12.72 12.26-.03 12.99-23.94 13-32.72.02-12.51.89-31.29-1.67-43-1.56-7.18-4.04-13.48-12.33-13.96-12.43-.71-14.85 5.63-24 5.36l-30-5.13c-13.87-2.14-43.34-3.51-57-1.85z"/></svg>

		</a></li>
		<!-- <li><a aria-current='{segment === "about" ? "page" : undefined}' href='about'>about</a></li> -->

		<!-- for the blog link, we're using rel=prefetch so that Sapper prefetches
		     the blog data when we hover over the link or tap it on a touchscreen -->
		<!-- <li><a rel=prefetch aria-current='{segment === "blog" ? "page" : undefined}' href='blog'>blog</a></li> -->
	</ul>
</nav>
