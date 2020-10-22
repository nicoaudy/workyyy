<style lang="postcss">
  :global(p) {
    @apply text-lg;
  }
</style>

<script>
  import { onMount } from 'svelte';
  import { APP_NAME, API_URL } from '../constants';
  import data from '../data/db';
  import JobCard from '../components/JobCard.svelte';

  let jobs = [];
  let search = '';

  onMount(async () => {
    getJobs();
  });

  const getJobs = async () => {
    try {
      const request = await fetch(`${API_URL}/give-me-some-data`, {
        method: 'POST',
      });

      const response = await request.json();
      jobs = response;
    } catch (e) {}
  };

  const filter = async () => {
    try {
      const request = await fetch(`${API_URL}/give-me-some-data`, {
        method: 'POST',
        body: JSON.stringify({
          search: search,
        }),
        headers: { 'Content-Type': 'application/json' },
      });

      const response = await request.json();
      jobs = response;
    } catch (e) {}
  };
</script>

<svelte:head>
  <title>{APP_NAME}</title>
</svelte:head>

<div
  class="flex justify-center flex-col bg-white shadow-md my-16 mx-10 p-6 rounded"
>
  <h3 class="text-center text-2xl uppercase font-semibold mb-2">
    👇 search here 👇
  </h3>

  <input
    type="search"
    class="bg-gray-100 focus:outline-none focus:shadow-outline border border-gray-300 rounded-lg py-2 px-4 block w-full appearance-none leading-normal"
    placeholder="Search by: Position, 📍 Location/Remote, 💼  Company, Skill,"
    bind:value={search}
    on:change={filter}
  />
</div>

{#if jobs.length}
  {#each jobs as job}
    <JobCard {job} />
  {/each}
{:else}
  <div class="my-16 mx-10 p-6">
    <p>Please wait....</p>
  </div>
{/if}
