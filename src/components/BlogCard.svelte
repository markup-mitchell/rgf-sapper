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

   .img-wrapper {
      max-width: 50%;
   }

   img {
      object-fit: scale-down;
   }
</style>



<article class="cardWrapper">
<div class="img-wrapper">
<img {src} alt="">
</div>
   <h1>{title}</h1>
   <p>{description}</p>
   <time>{date}</time>
</article>