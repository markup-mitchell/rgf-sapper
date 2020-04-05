<script>
   export let image = "../../static/chess.jpg" ;
   export let title = "blogpost";
   export let description = "a blog post description which is probably longer than this.";
   export let date = "2020-04-05";
</script>

<style>
   .cardWrapper {
      width: 100%;
      background: red;
   }
</style>



<article class="cardWrapper" style="background-image: url(`${image}`);">
   <h1>{title}</h1>
   <p>{description}</p>
   <time>{date}</time>
</article>