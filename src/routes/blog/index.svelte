<script context="module">
	export function preload({ params, query }) {
		return this.fetch(`blog.json`).then(r => r.json()).then(posts => {
			return { posts };
		});
	}
</script>

<script>
	export let posts;
	console.log(posts)
</script>

<style>
.grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
      grid-gap: 1rem;
   }

   .stack > * + * {
      margin-top: 1rem;      
   }

   .card-wrapper {
      display: inline-flex;
      flex-wrap: wrap;
      flex-basis: 300px;
      flex-grow: 1; 
      min-width: 300px;

      border: thin solid #eee;
      border-radius: 4px;
      box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1), 0 4px 6px -2px rgba(0, 0, 0, 0.05);
      transition: all 0.2s ease-in-out;
   }

   .card-wrapper:hover {
      transition: all 0.2s ease-in-out;
      transform: scale(1.01);
      box-shadow: 0 20px 25px -5px rgba(0, 0, 0, 0.1), 0 10px 10px -5px rgba(0, 0, 0, 0.04);
   }

   .card-text {
      padding: 1rem;
      flex-shrink: 1; 
      flex-grow: 1; 
      flex-basis: 60%;
   }

   .img-wrapper {
       flex-grow: 1;
      flex-shrink: 0;
      flex-basis: 10rem;
   }

   .img-wrapper > img {
      width: 100%;
      height: 100%;
      object-fit: cover;
   }
   
	ul {
      margin: 0;
      padding: 0;
		line-height: 1.5;
   }

   li {
      list-style-type: none;
      display: inline-flex;
   }
   
</style>

<svelte:head>
	<title>Blog</title>
</svelte:head>

<h1>Recent posts</h1>

<ul class="grid">
	{#each posts as post}
		<!-- we're using the non-standard `rel=prefetch` attribute to
				tell Sapper to load the data for the page as soon as
				the user hovers over the link or taps it, instead of
				waiting for the 'click' event -->
		<!-- <li><a rel='prefetch' href='blog/{post.slug}'>{post.title}</a></li> -->
      <li>
		<article class="card-wrapper">
      <div class="img-wrapper">
         <img src={post.featured_image} alt="">
      </div>
      <div class="card-text">
         <h1>{post.title}</h1>
         <p>{post.lede}</p>
      <time>{post.date}</time>
      </div>
   </article>
      </li>
	{/each}
</ul>


<div class="stack">

   <!-- <article class="card-wrapper">
      <div class="img-wrapper" style="background-image: url({src});">
      </div>
      <div class="card-text">
         <h1>{title}</h1>
         <p>{post.lede}</p>
      <time>{date}</time>
      </div>
   </article> -->

   <ul>
	<!-- {#each posts as post} -->

		<!-- we're using the non-standard `rel=prefetch` attribute to
				tell Sapper to load the data for the page as soon as
				the user hovers over the link or taps it, instead of
				waiting for the 'click' event -->

		<!-- <li><a rel='prefetch' href='blog/{post.slug}'>{post.title}</a></li>
	{/each}
</ul> -->
</div>