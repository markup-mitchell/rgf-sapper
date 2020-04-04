<script>
  import { onMount } from 'svelte';

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
		/* color: white; */
		font-weight: 700;
		margin: 0 0 0.5em 0;
		line-height: 0;
		/* text-shadow: 0 0 6px #0008; */
		/* background: #0008; */
		/* padding: 0.5rem; */
	}

p {
  font-size: 1.25rem;
}

	@media (min-width: 480px) {
		h1 {
			font-size: 4em;
		}
	}
</style>

<svelte:head>
	<title>Sapper project template</title>
	<script src="https://identity.netlify.com/v1/netlify-identity-widget.js"></script>
</svelte:head>

<h1>Rather Good Fatherhood</h1>
<p>
	Scientists are not sure yet exactly what the term "father" actually means - and if scientists don't know something, nobody does.
</p>
<p>
	So it's up for grabs, basically, and this is me staking my claim. <strong>I will tell you</strong> what it means to <strong>me<strong> over the course of as many blog posts as I can be bothered to write.
</p>
<p><strong>You</strong> will digest these words of wisdom and internalise them, papering over whatever internal inconsistencies you discover using your own initiative and experience with self-deceit.</p>
<p><strong>THAT'S THE DEAL, OK?</strong></p>
