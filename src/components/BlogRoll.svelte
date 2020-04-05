<script>
   import BlogCard from "./BlogCard.svelte";
</script>

<style>
   .grid {
      display: grid;
      width: 100%;
      grid-template-columns: 1fr 1fr;
      grid-auto-rows: min-content;
      grid-column: 2;
      grid-row: 1;
      grid-gap: 1rem;
   }
</style>

<div class="grid">
   <BlogCard />
    <BlogCard />
</div>