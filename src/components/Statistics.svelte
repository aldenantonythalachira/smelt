<script>
  const battingRecords = [
    {
      title: "Highest Individual Score (Test)",
      player: "Brian Lara",
      value: "400*",
      description: "vs England, 2004"
    },
    {
      title: "Highest Individual Score (ODI)",
      player: "Rohit Sharma",
      value: "264",
      description: "vs Sri Lanka, 2014"
    },
    {
      title: "Most Runs (Test)",
      player: "Sachin Tendulkar",
      value: "15,921",
      description: "200 matches"
    },
    {
      title: "Highest T20I Score",
      player: "Aaron Finch",
      value: "172",
      description: "vs Zimbabwe, 2018"
    }
  ];

  const bowlingRecords = [
    {
      title: "Best Bowling (Test)",
      player: "Jim Laker",
      value: "10/53",
      description: "vs Australia, 1956"
    },
    {
      title: "Best Bowling (ODI)",
      player: "Chaminda Vaas",
      value: "8/19",
      description: "vs Zimbabwe, 2001"
    },
    {
      title: "Most Wickets (Test)",
      player: "Muttiah Muralitharan",
      value: "800",
      description: "133 matches"
    },
    {
      title: "Best T20I Bowling",
      player: "Deepak Chahar",
      value: "6/7",
      description: "vs Bangladesh, 2019"
    }
  ];
</script>

<section id="stats" class="py-16 bg-white">
  <div class="container mx-auto px-4">
    <h3 class="text-3xl md:text-4xl font-bold text-center mb-12 text-gray-800">Cricket Statistics Dashboard</h3>
    
    <!-- Record Holders Section -->
    <div class="grid grid-cols-1 lg:grid-cols-2 gap-8 mb-12">
      <!-- Batting Records -->
      <div class="bg-white rounded-xl p-6 md:p-8 shadow-lg">
        <h4 class="text-xl md:text-2xl font-bold mb-6 text-gray-800">
          Batting Records
        </h4>
        <div class="space-y-4">
          {#each battingRecords as record}
            <div class="flex flex-col sm:flex-row sm:justify-between sm:items-center p-4 bg-white rounded-lg shadow-sm hover:shadow-md transition duration-300">
              <div class="mb-2 sm:mb-0">
                <p class="font-semibold text-gray-800 text-sm md:text-base">{record.title}</p>
                <p class="text-xs md:text-sm text-gray-600">{record.player}</p>
              </div>
              <div class="text-left sm:text-right">
                <p class="text-xl md:text-2xl font-bold text-green-600">{record.value}</p>
                <p class="text-xs text-gray-500">{record.description}</p>
              </div>
            </div>
          {/each}
        </div>
      </div>
      
      <!-- Bowling Records -->
      <div class="bg-white rounded-xl p-6 md:p-8 shadow-lg">
        <h4 class="text-xl md:text-2xl font-bold mb-6 text-gray-800">
          Bowling Records
        </h4>
        <div class="space-y-4">
          {#each bowlingRecords as record}
            <div class="flex flex-col sm:flex-row sm:justify-between sm:items-center p-4 bg-white rounded-lg shadow-sm hover:shadow-md transition duration-300">
              <div class="mb-2 sm:mb-0">
                <p class="font-semibold text-gray-800 text-sm md:text-base">{record.title}</p>
                <p class="text-xs md:text-sm text-gray-600">{record.player}</p>
              </div>
              <div class="text-left sm:text-right">
                <p class="text-xl md:text-2xl font-bold text-green-600">{record.value}</p>
                <p class="text-xs text-gray-500">{record.description}</p>
              </div>
            </div>
          {/each}
        </div>
      </div>
    </div>
  </div>
</section>
