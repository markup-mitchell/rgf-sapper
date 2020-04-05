<script>
   import BlogCard from "./BlogCard.svelte";
    export let src = "chess.jpg";
   export let title = "blogpost";
   export let description = "a blog post description which is probably longer than this. and what happens if it is longer than that? like, much, much longer? do things break?";
   export let date = "2020-04-05";
</script>

<style>
   .stack {
      width: 100%;
   }

   .stack > * + * {
      margin-top: 1rem;      
   }

   .card-wrapper {
      display: flex;
      width: 100%;
      height: 200px;
      background-size: cover;
      border: thin solid #eee;
      border-radius: 4px;
      box-shadow: 0 20px 25px -5px rgba(0, 0, 0, 0.1), 0 10px 10px -5px rgba(0, 0, 0, 0.04);
      transition: all 0.2s ease-in-out;
   }

   .card-wrapper:hover {
      transition: all 0.2s ease-in-out;
      transform: translateX(-0.25rem);
   }

   .card-text {
      padding: 1rem;
   }

   img {
      max-width: 50%;
   }
</style>

<div class="stack">

   <article class="card-wrapper">
<img {src} alt="">
   <div class="card-text">
   <h1>{title}</h1>
   <p>{description}</p>
   <time>{date}</time>
   </div>
</article>

<article class="card-wrapper">
<img {src} alt="">
   <div class="card-text">
   <h1>{title}</h1>
   <p>{description}</p>
   <time>{date}</time>
   </div>
</article>

</div>