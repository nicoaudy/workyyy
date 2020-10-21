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

<div class="flex bg-white shadow-md my-16 mx-10 p-6 rounded">
  <span>ruby on rails</span>
</div>

{#if jobs.length}
  {#each jobs as job}
    <JobCard {job} />
  {/each}
{:else}
  <p>Please wait....</p>
{/if}
