<script>
   import BlogCard from "./BlogCard.svelte";
    export let src = "chess.jpg";
   export let title = "blogpost";
   export let description = "a blog post description which is probably longer than this.";
   export let date = "2020-04-05";
</script>

<style>
   .stack {
      /* display: grid; */
      width: 100%;
   }

   .stack > * + * {
      margin-top: 1rem;      
   }

   .cardWrapper {
      display: flex;
      width: 100%;
      height: 200px;
      background: red;
      background-size: cover;
   }

   img {
      max-width: 100%;
   }
</style>

<div class="stack">
   <article class="cardWrapper">
<img {src} alt="">
   <h1>{title}</h1>
   <p>{description}</p>
   <time>{date}</time>
</article>
<article class="cardWrapper">
<img {src} alt="">
   <h1>{title}</h1>
   <p>{description}</p>
   <time>{date}</time>
</article>
</div>