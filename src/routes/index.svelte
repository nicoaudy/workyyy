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
  let search = '';

  onMount(async () => {
    jobs = data;
  });

  const filter = () => {
    jobs = data;

    jobs = jobs.filter((item) => {
      const company = item.company.toLowerCase();
      const position = item.position.toLowerCase();
      const location = item.location.toLowerCase();
      const contract = item.contract.toLowerCase();

      return (
        company.includes(search.toLowerCase()) ||
        position.includes(search.toLowerCase()) ||
        location.includes(search.toLowerCase()) ||
        contract.includes(search.toLowerCase())
      );
    });
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
  <p>Please wait....</p>
{/if}
