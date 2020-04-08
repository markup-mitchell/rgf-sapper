<script>
   import { onMount } from "svelte";
   import { fade } from "svelte/transition";

   let show = true;
</script>

<style>
 div {
    position: relative;
 }
</style>

{#if show}
<div in:fade="{{ duration: 100 }}">
   <slot><!-- optional fallback --></slot>
</div>
{/if}