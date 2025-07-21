<script>
  import { createEventDispatcher } from 'svelte';
  
  const dispatch = createEventDispatcher();
  let showMobileMenu = false;

  function toggleMobileMenu() {
    showMobileMenu = !showMobileMenu;
  }

  function navigateTo(section) {
    dispatch('navigate', section);
    showMobileMenu = false;
  }

  function openEasterEggs() {
    dispatch('openEasterEggs');
  }
</script>

<nav class="bg-green-600 shadow-lg sticky top-0 z-50">
  <div class="container mx-auto px-4 relative">
    <div class="flex justify-between items-center py-4">
      <div class="flex items-center space-x-3">
        <h1 class="text-white text-2xl font-bold">ICC Cricket World</h1>
      </div>
      
      <!-- Center Easter Egg Button -->
      <div class="absolute left-1/2 transform -translate-x-1/2 hidden sm:block">
        <button on:click={openEasterEggs} class="mysterious-button" title="Something special awaits...">
          <span class="mystery-text">?</span>
          <span class="glow-effect"></span>
        </button>
      </div>
      
      <div class="flex items-center space-x-4">
        <!-- Mobile Easter Egg Button -->
        <button on:click={openEasterEggs} class="mysterious-button-mobile sm:hidden" title="Something special awaits...">
          <span class="mystery-text-mobile">?</span>
        </button>
        
        <!-- Mobile menu button -->
        <button on:click={toggleMobileMenu} class="md:hidden text-white">
          Menu
        </button>
        
        <!-- Desktop menu -->
        <ul class="hidden md:flex space-x-6 text-white">
          <li><button on:click={() => navigateTo('home')} class="hover:text-black transition duration-300">Home</button></li>
          <li><button on:click={() => navigateTo('about')} class="hover:text-black transition duration-300">About Sport</button></li>
          <li><button on:click={() => navigateTo('tournaments')} class="hover:text-black transition duration-300">Tournaments</button></li>
          <li><button on:click={() => navigateTo('players')} class="hover:text-black transition duration-300">Players</button></li>
          <li><button on:click={() => navigateTo('stats')} class="hover:text-black transition duration-300">Statistics</button></li>
        </ul>
      </div>
    </div>
    
    <!-- Mobile menu -->
    {#if showMobileMenu}
      <ul class="md:hidden pb-4 text-white space-y-2">
        <li><button on:click={() => navigateTo('home')} class="block hover:text-black transition duration-300">Home</button></li>
        <li><button on:click={() => navigateTo('about')} class="block hover:text-black transition duration-300">About Sport</button></li>
        <li><button on:click={() => navigateTo('tournaments')} class="block hover:text-black transition duration-300">Tournaments</button></li>
        <li><button on:click={() => navigateTo('players')} class="block hover:text-black transition duration-300">Players</button></li>
        <li><button on:click={() => navigateTo('stats')} class="block hover:text-black transition duration-300">Statistics</button></li>
      </ul>
    {/if}
  </div>
</nav>

<style>
  .mysterious-button {
    position: relative;
    width: 50px;
    height: 50px;
    border-radius: 50%;
    background: linear-gradient(45deg, #ff6b6b, #4ecdc4, #45b7d1, #96ceb4);
    background-size: 300% 300%;
    border: 2px solid rgba(255, 255, 255, 0.3);
    cursor: pointer;
    transition: all 0.3s ease;
    animation: mysteryglow 3s ease-in-out infinite, gradientShift 4s ease-in-out infinite;
    box-shadow: 0 0 20px rgba(255, 255, 255, 0.3);
  }

  .mysterious-button:hover {
    transform: scale(1.1);
    box-shadow: 0 0 30px rgba(255, 255, 255, 0.5);
    animation: mysteryglow 1s ease-in-out infinite, gradientShift 2s ease-in-out infinite;
  }

  .mystery-text {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    color: white;
    font-size: 1.5rem;
    font-weight: bold;
    text-shadow: 0 0 10px rgba(255, 255, 255, 0.8);
    animation: pulse 2s ease-in-out infinite;
  }

  .glow-effect {
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    border-radius: 50%;
    background: radial-gradient(circle, transparent 30%, rgba(255, 255, 255, 0.1) 70%);
    animation: rotate 6s linear infinite;
  }

  @keyframes mysteryglow {
    0%, 100% { 
      box-shadow: 0 0 20px rgba(255, 255, 255, 0.3), 
                  0 0 40px rgba(255, 255, 255, 0.1);
    }
    50% { 
      box-shadow: 0 0 40px rgba(255, 255, 255, 0.6), 
                  0 0 80px rgba(255, 255, 255, 0.2);
    }
  }

  @keyframes gradientShift {
    0% { background-position: 0% 50%; }
    50% { background-position: 100% 50%; }
    100% { background-position: 0% 50%; }
  }

  @keyframes pulse {
    0%, 100% { transform: translate(-50%, -50%) scale(1); }
    50% { transform: translate(-50%, -50%) scale(1.1); }
  }

  @keyframes rotate {
    0% { transform: rotate(0deg); }
    100% { transform: rotate(360deg); }
  }

  /* Mobile version of mysterious button */
  .mysterious-button-mobile {
    position: relative;
    width: 35px;
    height: 35px;
    border-radius: 50%;
    background: linear-gradient(45deg, #ff6b6b, #4ecdc4, #45b7d1, #96ceb4);
    background-size: 300% 300%;
    border: 1px solid rgba(255, 255, 255, 0.3);
    cursor: pointer;
    transition: all 0.3s ease;
    animation: mysteryglow 3s ease-in-out infinite, gradientShift 4s ease-in-out infinite;
    box-shadow: 0 0 15px rgba(255, 255, 255, 0.3);
  }

  .mysterious-button-mobile:hover {
    transform: scale(1.1);
    box-shadow: 0 0 25px rgba(255, 255, 255, 0.5);
  }

  .mystery-text-mobile {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    color: white;
    font-size: 1.2rem;
    font-weight: bold;
    text-shadow: 0 0 8px rgba(255, 255, 255, 0.8);
    animation: pulse 2s ease-in-out infinite;
  }

  /* Responsive adjustments */
  @media (max-width: 640px) {
    .mysterious-button-mobile {
      width: 30px;
      height: 30px;
    }
    
    .mystery-text-mobile {
      font-size: 1rem;
    }
  }

  @media (min-width: 640px) and (max-width: 768px) {
    .mysterious-button {
      width: 40px;
      height: 40px;
    }
    
    .mystery-text {
      font-size: 1.3rem;
    }
  }
</style>
