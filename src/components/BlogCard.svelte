<script>
   export let src = "chess.jpg";
   export let title = "blogpost";
   export let description = "a blog post description which is probably longer than this.";
   export let date = "2020-04-05";
</script>

<style>
   .cardWrapper {
      display: flex;
      width: 100%;
      background: red;
      background-size: cover;
   }

   img {
      max-width: 100%;
   }
</style>



<article class="cardWrapper">
<img {src} alt="">
   <h1>{title}</h1>
   <p>{description}</p>
   <time>{date}</time>
</article>