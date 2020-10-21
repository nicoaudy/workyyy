<style lang="postcss">
  :global(p) {
    @apply text-lg;
  }
</style>

<script>
  import { APP_NAME } from '../constants';
</script>

<svelte:head>
  <title>{APP_NAME}</title>
</svelte:head>

<div class="space-y-8">
  <div>
    <h2 class="text-8xl font-semibold">{APP_NAME}</h2>
  </div>
  <p>Read the blog post if you want to know all the juicy details 🍊</p>
</div>
