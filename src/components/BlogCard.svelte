<script>
   import moment from "moment";
   export let title, lede, date, featured_image;
   const longDate = moment(date).format("LL");
</script>

<style>
.card-wrapper {
      display: inline-flex;
      flex-wrap: wrap;
      flex-basis: 300px;
      flex-grow: 1; 
      min-width: 300px;
      overflow: hidden;
      border: thin solid #ddd;
      border-radius: 0.25rem;
      box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1), 0 4px 6px -2px rgba(0, 0, 0, 0.05);
      transition: all 0.2s ease-in-out;
      background-color: white;
   }

   .card-wrapper:hover {
      transition: all 0.2s ease-in-out;
      box-shadow: 0 25px 50px -12px rgba(0, 0, 0, 0.25);

   }

   .card-text {
      padding: 1rem;
      flex-shrink: 1; 
      flex-grow: 1; 
      flex-basis: 60%;
      min-height: 10rem;
      display: flex;
      flex-direction: column;
      justify-content: space-between;
      pointer-events: none;
   }

   h1 {
      font-size: var(--text-2xl);
      font-weight: bold;
   }

   p {
      font-size: 1.125rem;
   }

   .img-wrapper {
      flex-grow: 1;
      flex-shrink: 0;
      flex-basis: 10rem;
   }

   .img-wrapper > img {
      width: 100%;
      height: 100%;
      object-fit: cover;
   }

   time {
      text-transform: uppercase;
      font-size: var(--font-xs);
   }

   hr {
      color: var(--black);
      opacity: .3;
      height: 0;
      margin: 0 0 0.5rem;
   }

</style>


<article class="card-wrapper">
     
      <div class="card-text">
         <div>
            <h1>{title}</h1>
            <p>{lede}</p>
         </div>
         <div>
            <hr>
         <time>{longDate}</time>
         </div>
      </div>
      <div class="img-wrapper">
         <img src={featured_image} alt="">
      </div>
   </article>