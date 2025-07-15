<script lang="ts">
  import HeroOne from './HeroOne.svelte';
  import HeroTwo from './HeroTwo.svelte';

let isFirstDone = false;


</script>

{#if !isFirstDone}
  <HeroOne onDone={() => (isFirstDone = true)} />
{:else}
  <HeroTwo />
{/if}
