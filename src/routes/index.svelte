<script>
  import { onMount } from 'svelte';
  import BlogRoll from '../components/BlogRoll.svelte';
  onMount(() => {
    if (window.netlifyIdentity) {
      window.netlifyIdentity.on("init", user => {
        if (!user) {
          window.netlifyIdentity.on("login", () => {
            document.location.href = "/admin/";
          });
        }
      });
    }
  });
</script>

<style>

	h1 {
		font-size: 2.8em;
		font-weight: 700;
		margin: 0 0 0.5em 0;
	}

p {
  font-size: 1.25rem;
}


  
  .grid {
		display: grid;
		width: 100%;
		background-color: transparent;
		box-sizing: border-box;
		letter-spacing: 1px;
		line-height: 1.5;
		grid-template-columns: 1fr;
		grid-gap: 6rem;
	}

  .text {
    grid-column: 1;
    grid-row: 1;
  }

  .blogroll {
    grid-column: 2;
    grid-row: 1;
  }

  	@media (min-width: 480px) {
		h1 {
			font-size: 4em;
		}
	}

	/* @media (min-width: 640px) {
		.grid {
			grid-column: 1;
			grid-row: 2;
		}
	} */


	@media (min-width: 945px) {
		.grid {
			grid-template-columns: 1fr 1fr;
		}
	}
</style>

<svelte:head>
	<title>Sapper project template</title>
	<script src="https://identity.netlify.com/v1/netlify-identity-widget.js"></script>
</svelte:head>

<div class="grid">
<div class="text">
<h1>Rather Good Fatherhood</h1>
<p>
	Scientists are not sure yet exactly what the term "father" actually means - and if scientists don't know something, nobody does.
</p>
<p>
	So it's up for grabs, basically, and this is me staking my claim. <strong>I will tell you</strong> what it means to <strong>me<strong> over the course of as many blog posts as I can be bothered to write.
</p>
<p><strong>You</strong> will digest these words of wisdom and internalise them, papering over whatever internal inconsistencies you discover using your own initiative and experience with self-deceit.</p>
<p><strong>THAT'S THE DEAL, OK?</strong></p>
</div>
</div>
<div class="blogroll">
<BlogRoll/>
</div>

