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
   let tagPosts = posts;

   // tags from each post get put in an array which is flattened with concat and duplicates eliminated by set
   let allTags = new Set([].concat.apply([], posts.map(post => {
      return post.tags;
   })));

   function filterPosts(tag) {
      tagPosts = posts.filter(post => post.tags.includes(tag))
      console.log(tagPosts);
   }


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

   .page-header {
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      padding-bottom: 2rem;
   }

   .tag-btn {
      border: none;
      font-size: var(--text-base);
      /* background: var(--black); */
      background: transparent;
      border: solid thin var(--black);
      border-radius: 1rem;
      color: var(--black);
      padding: 0.5rem;
      margin: 0.1rem;
   }
 

</style>

<svelte:head>
	<title>Blog</title>
</svelte:head>

<div class="page-header">
   <h1>Posts</h1>
   <ul>
   {#each [...allTags] as tag}
      <li>
         <button class="tag-btn" on:click={() => filterPosts(tag)}>{tag}</button>
      </li>
   {/each}
   </ul>
</div>


<ul class="grid">
	{#each tagPosts as {title,lede,date,featured_image,tags, slug}}
		<!-- we're using the non-standard `rel=prefetch` attribute to
				tell Sapper to load the data for the page as soon as
				the user hovers over the link or taps it, instead of
				waiting for the 'click' event -->
		<!-- <li></li> -->
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
