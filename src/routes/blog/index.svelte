<script context="module">
	export function preload({ params, query }) {
		return this.fetch(`blog.json`).then(r => r.json()).then(posts => {
			return { posts };
		});
	}
</script>

<script>
   import moment from "moment";

   import { fade, slide, blur } from "svelte/transition";
   import TransitionWrapper from '../../components/TransitionWrapper.svelte';
   import BlogCard from "../../components/BlogCard.svelte";
   
   export let posts;
   let tagPosts = posts;
   let tagFilter = null;
   let showTags = false;

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

   function clearTagFilter() {
      tagFilter = null;
      tagPosts = posts;
   }

   function toggleTags() { 
      showTags = !showTags;
      console.log(showTags);
   }


</script>

<style>
   .grid {
         display: grid;
         grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
         grid-gap: 2rem;
      }
   
   h2 {
      text-transform: capitalize;
      font-weight: bold;
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
      align-items: center;
      padding-bottom: 4rem;
   }

   .tag-btn {
      border: none;
      font-size: var(--text-sm);
      /* font-weight: bold; */
      letter-spacing: 1px;
      /* text-transform: uppercase; */
      /* background: #555; */
      background: transparent;
      border: solid thin var(--black);
      border-radius: 2px;
      /* color: white; */
      color: var(--black);
      /* opacity: 0.6; */
      padding: 0.5rem;
      margin: 0.1rem;
      transition: all 0.2s ease;
      white-space: nowrap;
      background-color: white;
   }

   .tag-btn:hover {
      background-color: #555;
      color: white;
      transition: all 0.2s ease;
   }
 
   .tags{
      /* grid-column: 1/-1;
      grid-row: 1; */
      /* text-align: center; */
      position: fixed;
      top: 20px;
      right: 0px;
      max-width: 40%;
      overflow: scroll;
      height: 100%;
      /* margin-right: 10px; */
      text-align: right;
   }

   .flex {
      display: flex;
   }

   svg {
      transition: all 0.2s ease;
   }

   svg:hover {
      fill: red;
      transition: all 0.2s ease;
   }
</style>

<svelte:head>
	<title>Blog</title>
</svelte:head>

<TransitionWrapper>
<div class="page-header">
<h1>Blog</h1>
   <div class="flex">
   {#if tagFilter}
      <h2>
         {tagFilter}
      </h2>
      <button on:click={clearTagFilter} class="tag-btn">clear</button>
   {:else}
   <h2>all posts</h2>
   {/if}
   </div>
   <input type="checkbox" bind:checked={showTags}/>

        <svg width="40" height="40">
    {#if showTags}
         <polygon in:fade points="10 8.58578644 2.92893219 1.51471863 1.51471863 2.92893219 8.58578644 10 1.51471863 17.0710678 2.92893219 18.4852814 10 11.4142136 17.0710678 18.4852814 18.4852814 17.0710678 11.4142136 10 18.4852814 2.92893219 17.0710678 1.51471863 10 8.58578644"></polygon>
      {:else}
         <path in:fade d="M0,10 L0,2 L2,0 L10,0 L20,10 L10,20 L0,10 Z M4.5,6 C5.32842712,6 6,5.32842712 6,4.5 C6,3.67157288 5.32842712,3 4.5,3 C3.67157288,3 3,3.67157288 3,4.5 C3,5.32842712 3.67157288,6 4.5,6 Z"></path>
      {/if}
      </svg>

</div>


<div class="grid">
{#if showTags}
<div class="tags" >
<ul transition:slide>
   {#each [...allTags] as tag}
      <li >
         <button class="tag-btn" on:click={() => filterPosts(tag)}>{tag}</button>
      </li>
   {/each}
   </ul>
</div>
{/if}
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
</div>
</TransitionWrapper>
