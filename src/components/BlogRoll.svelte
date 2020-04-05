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
      height: auto;
   }

   .stack > * + * {
      margin-top: 1rem;      
   }

   .card-wrapper {
      display: flex;
      flex-direction: column;
      width: 100%;
      border: thin solid #eee;
      border-radius: 4px;
      box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1), 0 4px 6px -2px rgba(0, 0, 0, 0.05);
      transition: all 0.2s ease-in-out;
   }

   .card-wrapper:hover {
      transition: all 0.2s ease-in-out;
      transform: translateX(-0.25rem);
      box-shadow: 0 20px 25px -5px rgba(0, 0, 0, 0.1), 0 10px 10px -5px rgba(0, 0, 0, 0.04);
   }

   .card-text {
      padding: 1rem;
   }

   .img-wrapper {
      background-position: center;
      background-repeat: no-repeat;
      height: 12rem;
      background-size: cover;
      border-radius: 0.25rem 0.25rem 0 0;
   }
@media (min-width: 945px) {
      .card-wrapper {
         flex-direction: row;
      }
   
      .img-wrapper {
      flex: 1;
      height: unset;
      border-radius: 0.25rem 0 0 0.25rem;
      }

      .card-text {
         max-width: 50%;
      }
   }
   

</style>

<div class="stack">

   <article class="card-wrapper">
      <div class="img-wrapper" style="background-image: url({src});">
      </div>
      <div class="card-text">
         <h1>{title}</h1>
         <p>{description}</p>
      <time>{date}</time>
      </div>
   </article>

   <article class="card-wrapper">
      <div class="img-wrapper" style="background-image: url({src});">
      </div>
      <div class="card-text">
         <h1>{title}</h1>
         <p>{description}</p>
      <time>{date}</time>
      </div>
   </article>

</div>