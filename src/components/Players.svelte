<script>
  let selectedFilter = 'all';
  
  const players = [
    {
      name: "Virat Kohli",
      handle: "@virat.kohli",
      followers: "254M",
      country: "India",
      role: "Batsman",
      category: "batsmen",
      handleColor: "text-blue-100"
    },
    {
      name: "MS Dhoni",
      handle: "@mahi7781",
      followers: "46.8M",
      country: "India",
      role: "Batsman",
      category: "batsmen",
      handleColor: "text-yellow-100"
    },
    {
      name: "David Warner",
      handle: "@davidwarner31",
      followers: "4.2M",
      country: "Australia",
      role: "Batsman",
      category: "batsmen",
      handleColor: "text-green-100"
    },
    {
      name: "Jasprit Bumrah",
      handle: "@jaspritb1",
      followers: "12.1M",
      country: "India",
      role: "Fast Bowler",
      category: "bowlers",
      handleColor: "text-red-100"
    },
    {
      name: "AB de Villiers",
      handle: "@abdevilliers17",
      followers: "8.7M",
      country: "South Africa",
      role: "Batsman",
      category: "batsmen",
      handleColor: "text-indigo-100"
    },
    {
      name: "Ben Stokes",
      handle: "@benstokes38",
      followers: "3.8M",
      country: "Great Britain",
      role: "All-rounder",
      category: "allrounders",
      handleColor: "text-blue-100"
    },
    {
      name: "Kane Williamson",
      handle: "@kane_williamson",
      followers: "2.1M",
      country: "New Zealand",
      role: "Batsman",
      category: "batsmen",
      handleColor: "text-gray-100"
    },
    {
      name: "Marnus Labuschagne",
      handle: "@marnuslabuschagne",
      followers: "1.8M",
      country: "Australia",
      role: "Batsman",
      category: "batsmen",
      handleColor: "text-yellow-100"
    },
    {
      name: "Josh Hazlewood",
      handle: "@joshhazlewood",
      followers: "1.4M",
      country: "Australia",
      role: "Fast Bowler",
      category: "bowlers",
      handleColor: "text-emerald-100"
    }
  ];

  $: filteredPlayers = selectedFilter === 'all' 
    ? players 
    : players.filter(player => player.category === selectedFilter);

  function setFilter(filter) {
    selectedFilter = filter;
  }
</script>

<section id="players" class="py-16 bg-white">
  <div class="container mx-auto px-4">
    <h3 class="text-3xl md:text-4xl font-bold text-center mb-4 text-gray-800">My Favourite Cricketers on Instagram</h3>
    <p class="text-center text-gray-600 mb-12">Discover the most followed cricketers on social media</p>
    
    <!-- Filter Controls -->
    <div class="max-w-2xl mx-auto mb-8">
      <div class="flex flex-wrap justify-center gap-4 mb-6">
        <button 
          on:click={() => setFilter('all')} 
          class="px-6 py-2 rounded-full border-2 border-green-600 transition duration-300 {selectedFilter === 'all' ? 'bg-green-600 text-white' : 'bg-white text-black hover:bg-green-600 hover:text-white'}"
        >
          All Players
        </button>
        <button 
          on:click={() => setFilter('batsmen')} 
          class="px-6 py-2 rounded-full border-2 border-green-600 transition duration-300 {selectedFilter === 'batsmen' ? 'bg-green-600 text-white' : 'bg-white text-black hover:bg-green-600 hover:text-white'}"
        >
          Batsmen
        </button>
        <button 
          on:click={() => setFilter('bowlers')} 
          class="px-6 py-2 rounded-full border-2 border-green-600 transition duration-300 {selectedFilter === 'bowlers' ? 'bg-green-600 text-white' : 'bg-white text-black hover:bg-green-600 hover:text-white'}"
        >
          Bowlers
        </button>
        <button 
          on:click={() => setFilter('allrounders')} 
          class="px-6 py-2 rounded-full border-2 border-green-600 transition duration-300 {selectedFilter === 'allrounders' ? 'bg-green-600 text-white' : 'bg-white text-black hover:bg-green-600 hover:text-white'}"
        >
          All-rounders
        </button>
      </div>
    </div>
    
    <!-- Players Grid -->
    <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6 mb-12">
      {#each filteredPlayers as player}
        <div class="bg-white rounded-xl shadow-lg overflow-hidden transform hover:scale-105 transition duration-300">
          <div class="bg-green-600 p-6 text-white">
            <div class="flex items-center justify-between mb-4">
              <div class="flex items-center space-x-3">
                <div class="w-16 h-16 bg-white rounded-full flex items-center justify-center">
                  <i class="fab fa-instagram text-3xl text-purple-600"></i>
                </div>
                <div>
                  <h4 class="text-xl font-bold">{player.name}</h4>
                  <p class="{player.handleColor}">{player.handle}</p>
                </div>
              </div>
              <div class="text-right">
                <p class="text-2xl font-bold">{player.followers}</p>
                <p class="text-sm {player.handleColor}">followers</p>
              </div>
            </div>
            <div class="flex justify-between text-sm">
              <span>{player.country}</span>
              <span>{player.role}</span>
            </div>
          </div>
        </div>
      {/each}
    </div>
  </div>
</section>
