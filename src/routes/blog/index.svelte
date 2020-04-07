<script context="module">
	export function preload({ params, query }) {
		return this.fetch(`blog.json`).then(r => r.json()).then(posts => {
			return { posts };
		});
	}
</script>

<script>
   import moment from "moment";
   import BlogCard from "../../components/BlogCard.svelte";
   export let posts;
</script>

<style>
.grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
      grid-gap: 2rem;
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
   
   a {
      display: inline-flex;
      text-decoration-line: none;
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
		<!-- <li></li> -->
      <li><a rel='prefetch' href='blog/{post.slug}'>
		<BlogCard
         title={post.title}
         lede={post.lede}
         date={post.date}
         image={post.featured_image}
      />
   </a>
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