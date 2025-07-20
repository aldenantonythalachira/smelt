<script>
  import { onMount } from 'svelte';
  import Navigation from './components/Navigation.svelte';
  import Hero from './components/Hero.svelte';
  import AboutCricket from './components/AboutCricket.svelte';
  import Tournaments from './components/Tournaments.svelte';
  import Players from './components/Players.svelte';
  import Statistics from './components/Statistics.svelte';
  import FAQ from './components/FAQ.svelte';
  import Footer from './components/Footer.svelte';
  import BackToTop from './components/BackToTop.svelte';

  // Easter Egg states
  let isBarrelRolling = false;
  let isDutchAngle = false;
  let isSupermanMode = false;
  let isBoundaryMode = false;
  let showEasterEggMessage = false;
  let easterEggPanelVisible = false;
  let easterEggMessage = '';
  
  let konamiSequence = [];
  const konamiCode = ['ArrowUp', 'ArrowUp', 'ArrowDown', 'ArrowDown', 'ArrowLeft', 'ArrowRight', 'ArrowLeft', 'ArrowRight', 'KeyB', 'KeyA'];
  let secretClickCount = 0;

  onMount(() => {
    // Check URL parameters for Easter eggs (keeping this as backup)
    const urlParams = new URLSearchParams(window.location.search);
    const query = urlParams.get('q');
    
    if (query) {
      checkUrlEasterEggs(query.toLowerCase());
    }
  });
  
  // Direct Easter Egg activation functions for buttons
  function activateBarrelRollEgg() {
    activateBarrelRoll();
  }
  
  function activateDutchAngleEgg() {
    activateDutchAngle();
  }
  
  function activateSupermanEgg() {
    activateSupermanMode();
  }
  
  function activateBoundaryEgg() {
    activateBoundaryMode();
  }
  
  function checkUrlEasterEggs(query) {
    if (query.includes('barrel roll') || query.includes('do a barrel roll')) {
      activateBarrelRoll();
    } else if (query.includes('dutch angle') || query.includes('tilt')) {
      activateDutchAngle();
    } else if (query.includes('flying') || query.includes('superman')) {
      activateSupermanMode();
    } else if (query.includes('boundary')) {
      activateBoundaryMode();
    }
  }
  
  function activateBarrelRoll() {
    isBarrelRolling = true;
    showMessage("🌀 Do a barrel roll! Website is spinning!");
    setTimeout(() => {
      isBarrelRolling = false;
    }, 4000);
  }
  
  function activateDutchAngle() {
    isDutchAngle = true;
    showMessage("📐 Dutch angle activated! Everything's tilted!");
    setTimeout(() => {
      isDutchAngle = false;
    }, 5000);
  }
  
  function activateSupermanMode() {
    isSupermanMode = true;
    showMessage("✈️ Flying mode activated! Soaring through the cricket clouds!");
    setTimeout(() => {
      isSupermanMode = false;
    }, 6000);
  }
  
  function activateBoundaryMode() {
    isBoundaryMode = true;
    showMessage("🚀 BOUNDARY! Six runs! The crowd goes wild!");
    setTimeout(() => {
      isBoundaryMode = false;
    }, 5000);
  }
  
  function showMessage(message) {
    easterEggMessage = message;
    showEasterEggMessage = true;
    setTimeout(() => {
      showEasterEggMessage = false;
    }, 3000);
  }

  function scrollToSection(event) {
    const section = event.detail;
    const element = document.getElementById(section);
    if (element) {
      element.scrollIntoView({
        behavior: 'smooth',
        block: 'start'
      });
    }
  }

  function openEasterEggPanel() {
    easterEggPanelVisible = true;
  }
</script>

<style>
  :global(body) {
    margin: 0;
    padding: 0;
    background-color: #f9fafb;
  }
  
  /* Easter Egg Animations */
  .easter-egg-container {
    transition: all 0.3s ease;
  }
  
  .barrel-roll {
    animation: barrelRoll 4s ease-in-out;
  }
  
  .dutch-angle {
    transform: rotate(-15deg);
    transition: transform 0.5s ease;
  }
  
  .superman-mode {
    animation: superman 6s ease-in-out;
    background: linear-gradient(45deg, #ff6b6b, #4ecdc4, #45b7d1, #96ceb4);
    background-size: 400% 400%;
    animation: superman 6s ease-in-out, gradientShift 2s ease-in-out infinite;
  }
  
  .boundary-mode {
    animation: boundary 5s ease-in-out;
    filter: hue-rotate(0deg);
  }
  
  /* Responsive adjustments for mobile */
  @media (max-width: 768px) {
    .dutch-angle {
      transform: rotate(-8deg); /* Less rotation on mobile */
    }
    
    .superman-mode {
      animation: supermanMobile 4s ease-in-out, gradientShift 2s ease-in-out infinite;
    }
    
    .barrel-roll {
      animation: barrelRollMobile 3s ease-in-out;
    }
  }
  
  @media (max-width: 480px) {
    .dutch-angle {
      transform: rotate(-5deg); /* Even less rotation on very small screens */
    }
    
    .superman-mode {
      animation: supermanMobile 3s ease-in-out, gradientShift 1.5s ease-in-out infinite;
    }
    
    .barrel-roll {
      animation: barrelRollMobile 2.5s ease-in-out;
    }
  }
  
  .easter-egg-message {
    position: fixed;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    z-index: 1001;
    background: linear-gradient(45deg, #ff6b6b, #4ecdc4);
    color: white;
    padding: 20px 40px;
    border-radius: 50px;
    box-shadow: 0 10px 30px rgba(0,0,0,0.3);
    font-size: 18px;
    font-weight: bold;
    text-align: center;
    animation: messageAppear 0.5s ease-out, messageBounce 3s ease-in-out infinite;
    max-width: 90vw;
    word-wrap: break-word;
  }

  /* Responsive Easter egg message */
  @media (max-width: 768px) {
    .easter-egg-message {
      padding: 15px 30px;
      font-size: 16px;
      border-radius: 25px;
    }
  }

  @media (max-width: 480px) {
    .easter-egg-message {
      padding: 12px 20px;
      font-size: 14px;
      border-radius: 20px;
      max-width: 95vw;
    }
  }
  
  @keyframes barrelRoll {
    0% { transform: rotate(0deg) scale(1); }
    25% { transform: rotate(90deg) scale(1.05); }
    50% { transform: rotate(180deg) scale(1.1); }
    75% { transform: rotate(270deg) scale(1.05); }
    100% { transform: rotate(360deg) scale(1); }
  }
  
  @keyframes superman {
    0%, 100% { transform: translateY(0) scale(1); }
    25% { transform: translateY(-30px) scale(1.03) rotateY(5deg); }
    50% { transform: translateY(-50px) scale(1.05); }
    75% { transform: translateY(-30px) scale(1.03) rotateY(-5deg); }
  }
  
  /* Mobile-optimized superman animation */
  @keyframes supermanMobile {
    0%, 100% { transform: translateY(0) scale(1); }
    25% { transform: translateY(-15px) scale(1.01); }
    50% { transform: translateY(-25px) scale(1.02); }
    75% { transform: translateY(-15px) scale(1.01); }
  }

  /* Mobile-optimized barrel roll animation */
  @keyframes barrelRollMobile {
    0% { transform: rotate(0deg) scale(1); }
    25% { transform: rotate(90deg) scale(0.98); }
    50% { transform: rotate(180deg) scale(0.95); }
    75% { transform: rotate(270deg) scale(0.98); }
    100% { transform: rotate(360deg) scale(1); }
  }
  
  @keyframes gradientShift {
    0% { background-position: 0% 50%; }
    50% { background-position: 100% 50%; }
    100% { background-position: 0% 50%; }
  }
  
  @keyframes boundary {
    0% { filter: hue-rotate(0deg) brightness(1) saturate(1); }
    25% { filter: hue-rotate(90deg) brightness(1.3) saturate(1.5); }
    50% { filter: hue-rotate(180deg) brightness(1.5) saturate(2); }
    75% { filter: hue-rotate(270deg) brightness(1.3) saturate(1.5); }
    100% { filter: hue-rotate(360deg) brightness(1) saturate(1); }
  }
  
  @keyframes messageAppear {
    0% { opacity: 0; transform: translate(-50%, -50%) scale(0.5); }
    100% { opacity: 1; transform: translate(-50%, -50%) scale(1); }
  }
  
  @keyframes messageBounce {
    0%, 100% { transform: translate(-50%, -50%) scale(1); }
    50% { transform: translate(-50%, -50%) scale(1.05); }
  }

  /* Easter Egg Panel Styles */
  .easter-egg-panel {
    position: fixed;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    background: rgba(0, 0, 0, 0.9);
    color: white;
    padding: 2rem;
    border-radius: 15px;
    z-index: 10000;
    opacity: 0;
    visibility: hidden;
    transition: all 0.3s ease;
    box-shadow: 0 20px 40px rgba(0, 0, 0, 0.3);
    border: 2px solid #4f46e5;
    max-width: 90vw;
    max-height: 90vh;
  }

  .easter-egg-panel.visible {
    opacity: 1;
    visibility: visible;
  }

  .easter-egg-panel h3 {
    text-align: center;
    margin-bottom: 1.5rem;
    font-size: 1.5rem;
    padding-right: 40px; /* Add padding to avoid close button overlap */
  }

  .close-panel {
    position: absolute;
    top: 15px;
    right: 20px;
    background: rgba(255, 255, 255, 0.1);
    border: 1px solid rgba(255, 255, 255, 0.3);
    border-radius: 50%;
    color: white;
    font-size: 1.2rem;
    cursor: pointer;
    padding: 0;
    width: 35px;
    height: 35px;
    display: flex;
    align-items: center;
    justify-content: center;
    transition: all 0.3s ease;
  }

  .close-panel:hover {
    background: rgba(255, 255, 255, 0.2);
    transform: scale(1.1);
  }

  .easter-egg-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 1rem;
    max-width: 400px;
  }

  .easter-egg-btn {
    background: linear-gradient(45deg, #667eea 0%, #764ba2 100%);
    color: white;
    border: none;
    padding: 1rem;
    border-radius: 10px;
    cursor: pointer;
    font-size: 1rem;
    transition: all 0.3s ease;
    box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
    min-height: 60px;
  }

  .easter-egg-btn:hover {
    transform: translateY(-2px);
    box-shadow: 0 6px 20px rgba(0, 0, 0, 0.3);
  }

  /* Mobile responsive styles for Easter egg panel */
  @media (max-width: 768px) {
    .easter-egg-panel {
      padding: 1.5rem;
      border-radius: 10px;
      max-width: 95vw;
    }
    
    .easter-egg-panel h3 {
      font-size: 1.3rem;
      margin-bottom: 1rem;
      padding-right: 35px;
    }
    
    .close-panel {
      top: 12px;
      right: 15px;
      width: 30px;
      height: 30px;
      font-size: 1.1rem;
    }
    
    .easter-egg-grid {
      gap: 0.8rem;
      max-width: 100%;
    }
    
    .easter-egg-btn {
      padding: 0.8rem;
      font-size: 0.9rem;
      min-height: 50px;
    }
  }

  @media (max-width: 480px) {
    .easter-egg-panel {
      padding: 1rem;
      border-radius: 8px;
    }
    
    .easter-egg-panel h3 {
      font-size: 1.2rem;
      padding-right: 30px;
    }
    
    .easter-egg-grid {
      grid-template-columns: 1fr;
      gap: 0.6rem;
    }
    
    .easter-egg-btn {
      padding: 0.7rem;
      font-size: 0.85rem;
      min-height: 45px;
    }
    
    .close-panel {
      top: 10px;
      right: 12px;
      width: 28px;
      height: 28px;
      font-size: 1rem;
    }
  }
</style>

<!-- Easter Egg Message -->
{#if showEasterEggMessage}
  <div class="easter-egg-message">
    {easterEggMessage}
  </div>
{/if}

<!-- Main Content with Easter Egg Effects -->
<div class="easter-egg-container 
  {isBarrelRolling ? 'barrel-roll' : ''} 
  {isDutchAngle ? 'dutch-angle' : ''} 
  {isSupermanMode ? 'superman-mode' : ''} 
  {isBoundaryMode ? 'boundary-mode' : ''}">
  
  <!-- Easter Egg Panel -->
  <div class="easter-egg-panel" class:visible={easterEggPanelVisible}>
    <button class="close-panel" on:click={() => easterEggPanelVisible = false}>×</button>
    <h3>🎮 Easter Eggs</h3>
    <div class="easter-egg-grid">
      <button class="easter-egg-btn" on:click={activateBarrelRollEgg}>
        🌪️ Barrel Roll
      </button>
      <button class="easter-egg-btn" on:click={activateDutchAngleEgg}>
        📐 Dutch Angle
      </button>
      <button class="easter-egg-btn" on:click={activateSupermanEgg}>
        ✈️ Flying Mode
      </button>
      <button class="easter-egg-btn" on:click={activateBoundaryEgg}>
        🎯 Boundary Mode
      </button>
    </div>
  </div>
  
  <Navigation on:navigate={scrollToSection} on:openEasterEggs={openEasterEggPanel} />
  <Hero />
  <AboutCricket />
  <Tournaments />
  <Players />
  <Statistics />
  <FAQ />
  <Footer />
  <BackToTop />
</div>
