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

:root {
  --hud-margin: 0.5rem;
}
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
      position: relative;
      display: flex;
      flex-direction: column;
      align-items: center;
      padding-bottom: 4rem;
      grid-column: 1/-1;
   }

   .tag-btn {
      border: none;
      font-size: var(--text-sm);
      letter-spacing: 1px;
      background: transparent;
      border: solid thin var(--black);
      border-radius: 2px;
      color: var(--black);
      padding: 0.5rem;
      margin: 0.1rem;
      transition: all 0.2s ease;
      white-space: nowrap;
   }

   .tag-btn:hover {
      background-color: #555;
      color: white;
      transition: all 0.2s ease;
   }
 
   /* .tags {
      position: fixed;
      top: 3rem;
      right: 0.5rem;
      max-width: 30%;
      height: 100%;
      text-align: right;
   } */

   .flex {
      display: flex;
      align-items: baseline;
   }

   svg {
      transition: all 0.2s ease;
      pointer-events: none;
   }

   svg:hover {
      fill: red;
      transition: all 0.2s ease;
   }

   button {
      border:  none;
      background-color: transparent;
   }
/* 
   .tag-toggle {
      position: fixed;
      top: var(--hud-margin);
      right: var(--hud-margin);
      padding: 0;
      z-index: 10;
   } */

   h2 {
      font-weight: normal;
      margin: 0;
   }


   .clear-tag {
      margin-left: 0.75rem;
      padding: 0;
   }

   .clear-tag__icon {
      height: var(--text-base);
      opacity: 0.3;
   }

   button:focus {
      outline: none;
      /* this is bad. how to do focus? invert? v.solid line? */
   }

   .shavings {
      position: absolute;
      top: 7rem;
      left: -10rem;
      bottom: 0;
      opacity: 0.5;
      z-index: -1;
      transform: rotate(-20deg);
	}

   @media (min-width: 945px) {
      .page-header {
         align-items: center;
      }
   }
</style>

<svelte:head>
	<title>Blog</title>
</svelte:head>

<TransitionWrapper>

  


<div class="grid">
<div class="page-header">
   <h1>Blog</h1>
      <div class="flex">
         {#if tagFilter}
            <h2>
               {tagFilter}
            </h2>
           <button class="clear-tag" on:click={clearTagFilter}>
               <svg class="clear-tag__icon" viewbox="0 0 20 20">
                  <polygon in:fade points="10 8.58578644 2.92893219 1.51471863 1.51471863 2.92893219 8.58578644 10 1.51471863 17.0710678 2.92893219 18.4852814 10 11.4142136 17.0710678 18.4852814 18.4852814 17.0710678 11.4142136 10 18.4852814 2.92893219 17.0710678 1.51471863 10 8.58578644"></polygon>
               </svg>
            </button>
         {:else}
            <h2>all posts</h2>
         {/if}
         <button class="tag-toggle" on:click={toggleTags}>
            <svg width="30" height="30" viewbox="0 0 20 20">
               {#if showTags}
                  <polygon in:fade points="10 8.58578644 2.92893219 1.51471863 1.51471863 2.92893219 8.58578644 10 1.51471863 17.0710678 2.92893219 18.4852814 10 11.4142136 17.0710678 18.4852814 18.4852814 17.0710678 11.4142136 10 18.4852814 2.92893219 17.0710678 1.51471863 10 8.58578644"></polygon>
               {:else}
                  <path in:fade d="M0,10 L0,2 L2,0 L10,0 L20,10 L10,20 L0,10 Z M4.5,6 C5.32842712,6 6,5.32842712 6,4.5 C6,3.67157288 5.32842712,3 4.5,3 C3.67157288,3 3,3.67157288 3,4.5 C3,5.32842712 3.67157288,6 4.5,6 Z"></path>
               {/if}
            </svg>
         </button> 
      </div>
      <!-- <img class="shavings" src="https://res.cloudinary.com/dthkwbvgt/image/upload/v1586378624/shavings_ogvg1s.png" alt="pencil shavings"> -->
   </div>
 
{#if showTags}
<div class="tags" >
<ul transition:fade>
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
