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
   let tagFilter = null;

   // tags from each post get put in an array which is flattened with concat and duplicates eliminated by set
   let allTags = new Set([].concat.apply([], posts.map(post => {
      return post.tags;
   })));

   function filterPosts(tag) {
      tagPosts = posts.filter(post => post.tags.includes(tag));
      setTagFilter(tag);
   }

   function setTagFilter(tag) {
      tagFilter = tag;
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
      justify-content: flex-end;
      padding-bottom: 2rem;
   }

   .tag-btn {
      border: none;
      font-size: var(--text-base);
      /* font-weight: bold; */
      letter-spacing: 1px;
      /* text-transform: uppercase; */
      /* background: #555; */
      background: transparent;
      border: solid thin var(--black);
      border-radius: 0.25rem;
      /* color: white; */
      color: var(--black);
      /* opacity: 0.6; */
      padding: 0.5rem;
      margin: 0.1rem;
      transition: all 0.2s ease;
      
   }

   .tag-btn:hover {
      background-color: #555;
      color: white;
      transition: all 0.2s ease;
   }
 
   .tags{
      grid-column: 1;
      grid-row: 1;
   }

</style>

<svelte:head>
	<title>Blog</title>
</svelte:head>

<div class="page-header">
   <h1>Posts {#if tagFilter} tagged <strong>{tagFilter}</strong> {/if}</h1>
  
</div>


<ul class="grid">
<div class="tags">
<h2>Tags</h2>
<ul class="gridded">
   {#each [...allTags] as tag}
      <li>
         <button class="tag-btn" on:click={() => filterPosts(tag)}>{tag}</button>
      </li>
   {/each}
   </ul>
</div>
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
