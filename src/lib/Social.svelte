<script lang="ts">
  import { Facebook, Twitter } from "svelte-share-buttons-component"

  export let url: string
  export let title: string
</script>

{#if url}
  <div class="mt-4 flex gap-2 pr-4 sm:pr-0 justify-end sm:justify-center center">
    <Facebook class="h-10 w-10" {url} />
    <Twitter class="h-10 w-10" text={title} {url} />
  </div>
{/if}
