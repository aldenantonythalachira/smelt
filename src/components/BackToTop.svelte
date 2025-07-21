<script>
  import { onMount } from 'svelte';
  
  let showButton = false;

  onMount(() => {
    function handleScroll() {
      showButton = window.pageYOffset > 300;
    }

    window.addEventListener('scroll', handleScroll);
    
    return () => {
      window.removeEventListener('scroll', handleScroll);
    };
  });

  function scrollToTop() {
    window.scrollTo({
      top: 0,
      behavior: 'smooth'
    });
  }
</script>

{#if showButton}
  <button 
    on:click={scrollToTop}
    class="fixed bottom-6 right-6 bg-green-600 hover:bg-black text-white w-12 h-12 rounded-full shadow-lg z-50 transition-colors duration-300"
  >
    ↑
  </button>
{/if}
