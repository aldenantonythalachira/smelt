<script>
  const tournaments = [
    {
      name: "ICC T20 World Cup",
      location: "India and Sri Lanka",
      teams: "16 Teams Participating"
    },
    {
      name: "ICC Men's ODI World Cup",
      location: "South Africa, Namibia and Zimbabwe",
      teams: "10 Teams Participating"
    },
    {
      name: "Indian Premier League",
      location: "India",
      teams: "10 Teams Participating"
    },
    {
      name: "The Hundred",
      location: "England & Wales",
      teams: "8 Teams Participating"
    },
    {
      name: "Big Bash League",
      location: "Australia",
      teams: "8 Teams Participating"
    },
    {
      name: "Pakistan Super League",
      location: "Pakistan & UAE",
      teams: "6 Teams Participating"
    }
  ];
</script>

<section id="tournaments" class="py-16 bg-gray-100">
  <div class="container mx-auto px-4">
    <h3 class="text-3xl md:text-4xl font-bold text-center mb-12 text-gray-800">Cricket Tournaments & Events</h3>
    
    <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
      {#each tournaments as tournament}
        <div class="bg-white rounded-lg shadow-lg overflow-hidden transform hover:scale-105 transition duration-300">
          <div class="bg-green-600 p-4 text-white">
            <h4 class="text-xl font-bold">{tournament.name}</h4>
          </div>
          <div class="p-6">
            <div class="space-y-3">
              <div class="flex items-center">
                <i class="fas fa-map-marker-alt text-green-600 mr-3"></i>
                <span class="text-gray-700">{tournament.location}</span>
              </div>
              <div class="flex items-center">
                <i class="fas fa-users text-purple-600 mr-3"></i>
                <span class="text-gray-700">{tournament.teams}</span>
              </div>
            </div>
          </div>
        </div>
      {/each}
    </div>
  </div>
</section>
