<script lang="ts">
	import gsap from "gsap";
	import { onMount } from "svelte";

	const words = ["Welcome", "to", "Munna's", "World"];

	let sectionRef: HTMLElement;
	const wordRefs: HTMLSpanElement[] = [];

	// Assign each word element to its index
	function setWordRef(index: number) {
		return (el: HTMLSpanElement) => {
			wordRefs[index] = el;
		};
	}

	onMount(() => {
		const tl = gsap.timeline();

		tl.fromTo(
			wordRefs,
			{ opacity: 0, y: 20 },
			{
				opacity: 1,
				y: 0,
				duration: 0.5,
				stagger: 0.3,
				ease: "power2.out"
			}
		);

		tl.to(sectionRef, {
			y: -100,
			opacity: 0,
			duration: 1,
			delay: 0.5,
			ease: "power2.inOut"
		});
	});
</script>

<style>
	section {
		display: flex;
		gap: 0.5rem;
		font-size: 2rem;
		font-weight: bold;
		justify-content: center;
		align-items: center;
		height: 100vh;
		flex-wrap: wrap;
		overflow: hidden;
	}
	.word {
		opacity: 0;
		transform: translateY(20px);
	}
</style>

<section bind:this={sectionRef}>
	{#each words as word, i}
		<span class="word" bind:this={setWordRef(i)}>
			{word}
		</span>
	{/each}
</section>
