<style lang="postcss">
  :global(p) {
    @apply text-lg;
  }
</style>

<script>
  import { onMount } from 'svelte';
  import { APP_NAME } from '../constants';
  import data from '../data/db';
  import JobCard from '../components/JobCard.svelte';

  let jobs = [];

  onMount(async () => {
    jobs = data;
  });
</script>

<svelte:head>
  <title>{APP_NAME}</title>
</svelte:head>

<div class="space-y-8">
  {#if jobs.length}
    {#each jobs as job}
			<JobCard job={job} />
    {/each}
  {:else}
    <p>Please wait....</p>
  {/if}
</div>
