<script>
  import { onMount } from 'svelte';

  export let job;
</script>

<div class="flex bg-white shadow-md m-4 p-4">
  <div><img src={job.logo} alt={job.name} /></div>
  <div class="ml-2">
    <h3>{job.company}</h3>
    <h3>{job.position}</h3>
    <div class="flex">
      <p class="mr-2">💼 {job.contract}</p>
      <p>📍 {job.location}</p>
    </div>
  </div>
</div>
