<script lang="ts">
  import { onMount } from 'svelte';
  import gsap from 'gsap';

  onMount(() => {
    const tl = gsap.timeline();
    tl.fromTo(".title", { y: 100, opacity: 0 }, { y: 0, opacity: 1, duration: 1, ease: "power2.out" })
      .fromTo(".button", { y: 50, opacity: 0 }, { y: 0, opacity: 1, duration: 0.8 }, "+=0.3")
      .fromTo(".text", { y: 30, opacity: 0 }, { y: 0, opacity: 1, duration: 0.6 }, "+=0.3");
  });
</script>

<section class="second-hero grid grid-cols-1 md:grid-cols-2 gap-6 p-12 bg-white text-gray-800 min-h-screen">
  <div class="flex flex-col gap-4">
    <h1 class="text-4xl font-bold opacity-0 title">Welcome to Hero Section 2</h1>
    <button class="bg-blue-600 text-white py-2 px-4 rounded opacity-0 button">Click Me</button>
  </div>
  <div class="opacity-0 text">
    <p>
      This is a paragraph with some detailed content about the hero section. It appears after the title and button.
    </p>
  </div>
</section>
