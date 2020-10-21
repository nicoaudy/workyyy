<style lang="postcss">
  :global(p) {
    @apply text-lg;
  }
</style>

<script>
  import { onMount } from 'svelte';
  import { APP_NAME } from '../constants';
  import data from '../data/db';

  let jobs = [];

  onMount(async () => {
    setTimeout(() => {
      jobs = data;
    }, 3000);
  });
</script>

<svelte:head>
  <title>{APP_NAME}</title>
</svelte:head>

<div class="space-y-8">
  <div>
    <h2 class="text-8xl font-semibold">{APP_NAME}</h2>
  </div>

  {#if jobs.length}
    Jobs
  {:else}
    <p>Loading...</p>
  {/if}
</div>
