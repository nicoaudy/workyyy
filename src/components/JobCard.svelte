<script>
  import { onMount } from 'svelte';

  export let job;
  let skills;

  onMount(async () => {
    skills = job.skills.split(',');
  });
</script>

<div class="flex flex-col bg-white shadow-md my-16 mx-10 p-6 rounded">
  <div>
    <img src={job.logo} alt={job.name} class="-mt-16 mb-4 h-20 w-20 rounded" />
  </div>
  <div class="flex flex-col justify-between ml-4">
    <h3 class="font-bold text-purple-500">{job.company}</h3>
    <h3 class="font-bold text-xl my-2">{job.position}</h3>
    <div class="flex items-center">
      <p class="mr-2 text-gray-700">💼 {job.contract}</p>
      <p class="text-gray-700">📍 {job.location}</p>
    </div>
  </div>
  <div
    class="flex items-center mt-4 mx-4 pt-4 border-t border-gray-200 border-solid"
  >
    {#if skills}
      {#each skills as skill}
        <span
          class="font-semibold text-xs mr-4 p-2 rounded text-purple-500 bg-purple-100"
        >{skill}</span>
      {/each}
    {/if}
  </div>
</div>
