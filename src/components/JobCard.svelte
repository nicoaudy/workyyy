<script>
  import { onMount } from 'svelte';

  export let job;
  let skills;

  onMount(async () => {
    skills = job.skills.split(',');
  });
</script>

<div
  class="flex flex-col bg-white shadow-md my-16 mx-10 p-6 rounded sm:flex-row"
>
  <div>
    <img
      src={job.logo}
      alt={job.name}
      class="-mt-16 mb-4 h-20 w-20 rounded sm:mt-0 sm:h-24 sm:w-24 sm:my-0"
    />
  </div>
  <div class="flex flex-col justify-between ml-4">
    <a
      href={job.website}
      target="_blank"
      class="font-bold text-purple-500"
    >{job.company}</a>
    <h3 class="font-bold text-xl my-2">{job.position}</h3>
    <div class="flex items-center">
      <p class="mr-2 text-gray-700">📍 {job.location}</p>
      <a
        href={job.directUrl}
        target="_blank"
        class="bg-pink-100 text-pink-600 text-sm font-semibold border px-2 py-1 rounded-lg hover:border-pink-600"
      >APPLY 👉</a>
    </div>
  </div>
  <div
    class="flex items-center mt-4 mx-4 pt-4 border-t border-gray-200 border-solid sm:ml-auto sm:border-0 sm:pt-0 sm:items-center"
  >
    {#if skills}
      {#each skills as skill}
        <span
          class="font-semibold text-xs mr-4 mb-4 p-2 rounded text-purple-500 bg-purple-100 sm:mb-0"
        >{skill}</span>
      {/each}
    {/if}
  </div>
</div>
