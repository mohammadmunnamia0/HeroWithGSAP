
<script lang="ts">
	import { onMount } from 'svelte';
	import gsap from 'gsap';

	onMount(() => {
		const transition = gsap.timeline();

		transition.fromTo(
			'.line',
			{ y: 50, opacity: 0 },
			{ y: 0, opacity: 1, duration: 0.4, stagger: 0.15, ease: 'power2.out' }
		)
			.fromTo('.button', { y: 40, opacity: 0 }, { y: 0, opacity: 1, duration: 0.4 }, '+=0.2')
			.fromTo('.text', { y: 30, opacity: 0 }, { y: 0, opacity: 1, duration: 0.3 }, '+=0.2');
	});

	const heroTitleClass =
		'line text-[60px] leading-[1.1] font-extrabold opacity-0 md:text-[70px] lg:text-[90px]';
</script>

<section
	class="relative flex min-h-[91vh] flex-col justify-center bg-gradient-to-tr from-black via-black to-violet-900 px-2 text-white p-4"
>
	<div class="max-w-6xl">
		<div class="space-y-4">
			<h1 class={heroTitleClass}>Everything you need to</h1>
			<h1 class={heroTitleClass}>
				make a <span class="text-violet-500">Difference</span>
			</h1>
		</div>

		<button
			class="button mt-10 rounded-full border border-white px-10 py-5 text-lg font-medium opacity-0 transition-all duration-200 hover:bg-white hover:text-black"
		>
			Explore Us
		</button>
	</div>

	<div class="text absolute right-8 bottom-8 max-w-sm text-xl text-gray-200 opacity-0">
		<p>
			Our skilled team uses the latest tools and techniques to deliver memorable brand identities
			and digital experiences.
		</p>
	</div>
</section>
