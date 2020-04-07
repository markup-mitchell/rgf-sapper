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
   let postsByDate = posts.sort((a,b) => {
         a = new Date(a.date);
         b = new Date(b.date);
    return a > b ? -1 : a < b ? 1 : 0;
   });
   
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

<h1 class="pageHeading">Recent posts</h1>

<ul class="grid">
	{#each posts as {title,lede,date,featured_image, slug}}
		<!-- we're using the non-standard `rel=prefetch`  attribute to
				tell Sapper to load the data for the page as soon as
				the user hovers over the link or taps it, instead of
				waiting for the 'click' event -->
      <li><a rel='prefetch' href='blog/{slug}'>
		<BlogCard
         {title}
         {lede}
         {date}
         {featured_image}
      />
   </a>
      </li>
	{/each}
</ul>
