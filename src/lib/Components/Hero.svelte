<script lang="ts">
	import Navbar from './common/Navbar.svelte';
	import HeroOne from './HeroOne.svelte';
	import HeroTwo from './HeroTwo.svelte';

	let isFirstDone = false;
</script>

<section >
	{#if !isFirstDone}
		<HeroOne onDone={() => (isFirstDone = true)} />
	{:else}
		<Navbar />
		<HeroTwo/>
	{/if}
</section>
