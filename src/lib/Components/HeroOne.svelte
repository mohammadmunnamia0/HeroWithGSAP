<script lang="ts">
	import { onMount } from 'svelte';
	import gsap from 'gsap';

 export let onDone: () => void;
	let words = ['welcome', 'স্বাগতম', 'Ola', 'Holla'];
	let currentWord = '';

	const typeWords = async () => {
		for (const word of words) {
			currentWord = word;
			await new Promise((r) => setTimeout(r, 400));
		}

		const tl = gsap.timeline();

		// Bottom curve during lift up the 1st section
		tl.to('.first-hero', {
			borderBottomLeftRadius: '999px',
			borderBottomRightRadius: '999px',
			duration: 0.6,
			ease: 'power3.out'
		});

		// LiftUp the hero section
		tl.to('.first-hero', {
			y: -300,
			opacity: 0,
			duration: 1.2,
			ease: 'expo.inOut',
			onComplete: () => {
				 onDone?.();
			}
		});
	};

	onMount(() => {
		typeWords();
	});
</script>

<div class="hero-wrapper relative">
	<section class="first-hero relative z-10 w-full text-white shadow-xl overflow-visible">
		<span class="text-4xl font-bold flex justify-center items-center">.</span>{currentWord}
	</section>
</div>


<style>
	.hero-wrapper {
		position: relative;
		overflow: hidden;
		background: black;
	}

	.first-hero {
		height: 100vh;
		display: flex;
		align-items: center;
		justify-content: center;
		font-size: 3rem;
		background: linear-gradient(to bottom, #0f0f0f, #5b21b6);
		color: white;
		will-change: transform, border-radius, opacity;
	}

</style>

