<style>
  @keyframes slideIn {
    from { opacity: 0; transform: translateX(-50px); }
    to { opacity: 1; transform: translateX(0); }
  }
  .slide-in {
    animation: slideIn 0.8s ease-out;
  }
</style>

<section id="home" class="bg-green-600 text-white py-20">
  <div class="container mx-auto px-4 text-center">
    <h2 class="text-4xl md:text-6xl font-bold mb-6 slide-in">
      Welcome to <span>Cricket World</span>
    </h2>
    <p class="text-xl md:text-2xl mb-8 slide-in">Your ultimate destination for cricket knowledge</p>
  </div>
</section>
