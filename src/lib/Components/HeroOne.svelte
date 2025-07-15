<script lang="ts">
  import { createEventDispatcher, onMount } from 'svelte';
  import gsap from 'gsap';

  const dispatch = createEventDispatcher();

  let words = ['welcome', 'স্বাগতম', 'Ola', 'Holla'];
  let currentWord = '';
  let index = 0;

  const typeWords = async () => {
    for (const word of words) {
      currentWord = word;
      await new Promise((r) => setTimeout(r, 1000));
    }

    const tl = gsap.timeline();
    tl.to(".first-hero", {
      y: -100,
      opacity: 0,
      duration: 1,
      ease: "power2.out",
      onComplete: () => {
        dispatch('done');
      }
    });
  };

  onMount(() => {
    typeWords();
  });
</script>

<style>
  .first-hero {
    height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 3rem;
    background: #111;
    color: white;
  }
</style>

<section class="first-hero">
  {currentWord}
</section>
