<script lang="ts">
  import HeroOne from './HeroOne.svelte';
  import HeroTwo from './HeroTwo.svelte';

  let showSecondHero = false;

  function handleDone() {
    showSecondHero = true;
  }
</script>

{#if !showSecondHero}
  <HeroOne on:done={handleDone} />
{:else}
  <HeroTwo />
{/if}
