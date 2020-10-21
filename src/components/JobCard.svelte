<script>
  import { onMount } from 'svelte';

  export let job;
  let skills;

  onMount(async () => {
    skills = job.skills.split(',');
  });
</script>

<div class="flex bg-white shadow-md m-4 p-6 rounded">
  <div>
    <img src={job.logo} alt={job.name} class="h-20 w-20 rounded-full mx-auto" />
  </div>
  <div class="flex flex-col justify-between ml-4">
    <h3 class="font-bold text-purple-500">{job.company}</h3>
    <h3 class="font-bold text-xl">{job.position}</h3>
    <div class="flex items-center">
      <p class="mr-2 text-gray-700">💼 {job.contract}</p>
      <p class="text-gray-700">📍 {job.location}</p>
    </div>
  </div>
  <div class="flex items-center ml-auto">
    {#if skills}
      {#each skills as skill}
        <span
          class="font-semibold text-xs m-1 p-2 rounded-full text-purple-500 bg-purple-100"
        >{skill}</span>
      {/each}
    {/if}
  </div>
</div>
