<script>
  let faqs = [
    {
      id: 1,
      question: "How are ICC rankings calculated?",
      answer: "ICC rankings are calculated using a complex points system based on recent match results, strength of opposition, and match importance. Teams earn points for wins and lose points for defeats.",
      isOpen: false
    },
    {
      id: 2,
      question: "When is the next Cricket World Cup?",
      answer: "The next ICC Men's Cricket World Cup is scheduled for 2027, while the ICC Men's T20 World Cup will be held in 2026. The Women's Cricket World Cup is planned for 2025.",
      isOpen: false
    },
    {
      id: 3,
      question: "How many teams participate in ICC tournaments?",
      answer: "The number varies by tournament. The Cricket World Cup typically features 10-12 teams, T20 World Cup has 16 teams, and the World Test Championship involves the top 9 Test-playing nations.",
      isOpen: false
    }
  ];

  function toggleFAQ(id) {
    faqs.forEach(faq => {
      if (faq.id === id) {
        faq.isOpen = !faq.isOpen;
      } else {
        faq.isOpen = false;
      }
    });
    faqs = [...faqs];
  }
</script>

<section class="py-16 bg-white">
  <div class="container mx-auto px-4">
    <h3 class="text-3xl md:text-4xl font-bold text-center mb-12 text-gray-800">Frequently Asked Questions</h3>
    
    <div class="max-w-3xl mx-auto space-y-4">
      {#each faqs as faq}
        <div class="bg-white border-2 border-green-600 rounded-lg shadow-md">
          <button 
            on:click={() => toggleFAQ(faq.id)} 
            class="w-full text-left p-6 flex justify-between items-center"
          >
            <span class="font-semibold text-black">{faq.question}</span>
            <i class="fas fa-chevron-down text-green-600 transition-transform duration-300 {faq.isOpen ? 'transform rotate-180' : ''}"></i>
          </button>
          {#if faq.isOpen}
            <div class="p-6 pt-0 text-gray-600">
              {faq.answer}
            </div>
          {/if}
        </div>
      {/each}
    </div>
  </div>
</section>
