<script>
  const projectGroups = [
    {
      title: 'Ongoing Projects',
      projects: [
        ['Ministry of Health Sri Lanka', 'Immersive 3D Chiller Room VR', 'https://view.berl.dev/viewer?scene=chillerroom_asda', true],
        ['International Conference Hall Nikanda', 'MEP - Rs. 550 million', '/assets/project location image/International Conference Hall Nikanda.png'],
        ['Examination Department Pallawatte', 'AC System - Rs. 40 million', '/assets/project location image/Examination Department Pallawatte.jpg'],
        ['Abewella & Pattipola Farm Project', 'Plumbing - Rs. 226 million', '/assets/project location image/AMBEWELLA PATTIPOLA FARM.jpg'],
        ['Mr. Dinesh Rodrigo Office Complex', 'MEP - Rs. 148 million', '/assets/project location image/Mr. Dinesh Rodrigo Office Complex.jpg'],
        ['Taru Villa Hotel Bentota', 'MEP - Rs. 83 million & 30KW Solar', '/assets/project location image/Taru Villa Hotel Bentota.jpg'],
        ['15 Nos House Units', '5KW each Solar System', '/assets/project location image/15 NOS.jpg']
      ]
    },
    {
      title: 'Hospitality & Commercial',
      projects: [
        ['Kingsbury Hotel, Colombo', '412 TR Chiller, 255 FCUs', '/assets/project%20location%20image/Kingsbury-Hotel.jpg.jpeg'],
        ['Royal Palms & Tangerine, Kalutara', 'Major hospitality MEP works', '/assets/project%20location%20image/Royal-Palms-kalutara.png'],
        ['Tangerine, Kalutara', '214 TR capacity', '/assets/project location image/Tangerine-kalutara.jpg.jpeg'],
        ['Sri Lanka Insurance Co., Colombo', '750 TR capacity', '/assets/project%20location%20image/srilanka-insuarance.jpg.jpeg'],
        ['World Trade Centre, Colombo', 'M&E works, 37th floor', '/assets/project location image/World Trade Centre, Colombo.webp'],
        ['Japanese Embassy House Project', 'AC, electrical, and fire systems', '/assets/project location image/Japanese Embassy House Project.jpg']
      ]
    },
    {
      title: 'Healthcare',
      projects: [
        ['Army Hospital, Narahenpita', '660 TR capacity, 400 FCUs', '/assets/project%20location%20image/Army-Hospital-Narahenpita.jpg.jpeg'],
        ['NHSL Neurotrauma Unit', '316 TR capacity', '/assets/project%20location%20image/Neurotrauma-unit-NHSL.jpg.jpeg'],
        ['NHSL Epilepsy Unit', '400 TR capacity', '/assets/project%20location%20image/Epilepsy-Unit-at-NHSL.jpg.jpeg'],
        ['General Hospital, Hambantota', 'Healthcare MEP works', '/assets/project%20location%20image/generl-hospital-hambantota.jpg.jpeg'],
        ['Cancer Hospital, Maharagama', 'Healthcare engineering works', '/assets/project%20location%20image/Cancer-Hospital-maharagma.jpg.jpeg'],
        ['Hemas Hospital, Wattala', '456 TR capacity', '/assets/project%20location%20image/Hemas-Hospital-wattala.jpg.jpeg']
      ]
    }
  ];

  const clientCategories = [
    {
      title: "Healthcare & Hospitals",
      clients: [
        "National Blood Transfusion Services Improvement Project", "Hambantota Hospital", "Vavuniya Hospital", "Fewer Hospital", "Operation Theater, Kegalla Genaral Hospital", "Galgamuwa Hospital", "Matara Labeema Hospital", "Government Hospital, Marawila", "General Hospital, Matara", "General Hospital, Kalutara", "Hemas Private Hospital, Wattala", "Duch Hospital Gall", "Hemas Hospital, Thalawatugoda", "Lanka Hospitals, Colombo", "Cooperative Hospital Galle", "Army Hospitals, Colombo", "Kandy Hospital Eye Theater", "Navy Hospital Trinco", "Army Hospital, Colombo", "Mr Zarook Dental Clinic Dhiwala", "Epilepsy Units at Colombo Hospital", "Cancer Hospital Maharagama", "Hambantota New Hospital"
      ]
    },
    {
      title: "Hospitality & Hotels",
      clients: [
        "Browns Beach Hotel, Negombo", "Cinnamon Grand Hotel, Colombo", "Trans Asia Hotel, Colombo", "Sidhalepa Hotel and spa", "Solis Hotel Kotte", "Silver Ray Hotel", "Hotel School, Kandy", "Fortress Hotel, Koggala", "Royal Palm Hotel, Kalutara", "Avani Hotel, Kalutara", "Tangerine Beach Hotel", "Galadari Hotel", "Premier Hotel, Pasikudha", "Peace Haven Hotel Tangalla", "MGM Club – Bambalapitiya", "Colombo Hilton – Multi Event Venue"
      ]
    },
    {
      title: "Commercial & Corporate",
      clients: [
        "World Trade Centre, 37th floor renovation", "Setmil Development, Colombo", "Lanka Bell Office Project", "MTV Head Office, Colombo", "Sri Lanka Insurance Corporation", "Lake house Publishers, Colombo", "Hutchison Telecom Plant Room", "Regal Cinema Hall, Colombo", "Exetel Communications", "Peoples Bank 1st City Branch", "SLT Data Centre", "EAL Mortors Head office", "Alfred House Garden", "Pership Building at Colombo-03", "Majestic City", "DFCC Bank Kurunagala", "Crest Cat Boulevard Renovation work", "National Savings Bank, Chilaw", "LB Finance Head office", "Mcdonalds, Reid Avenue", "McDonald’s, Rajagiriya", "DG-5 Group, Head office", "Havelock city apartment", "Havelock City Club House", "DNK Shopping Mall, Rajagiriya", "Enclaves Apartments", "Sriyani Dress Point, Kurunagala"
      ]
    },
    {
      title: "State & Institutional",
      clients: [
        "Japanese Embassy House Project", "Intake Improvement of Nittambuwa–Veyangoda Water Supply", "Sierra Housing Project", "National Film Corporation", "Dockyard Office Complex", "Hambantota Administrative Complex", "Pallekale Cricket Stadium", "International Buddhist Centre, Kandy", "Army Camp, Ambepussa", "Temple Trees Colombo-03", "Western Province center", "Korean Embassy Residence", "Labour Department", "Matara University College", "Kelaniya University", "Harbor Master Building, Colombo", "Sri Lanka Ports Authority", "IOM Organization", "Colombo Harbor Development Project", "National Archives, Colombo", "Ave-Maria Convent, Negombo", "Kotalawala Defense University", "British High Commission"
      ]
    },
    {
      title: "Industrial & Manufacturing",
      clients: [
        "Lanka Milk Foods, Welisara", "Intermart Printers, Kelaniya", "Dial Textile Industries", "Mas Methliya, Warakapola", "Ceylon Cold Stores", "Ansell Lanka Factory Biyagama", "CBL factory Ranala", "SC Printing Rathmalana", "Causeway paints", "Ceylon Oxygen Kerawalapitiya", "Causway Paints Panadura", "Basiler Tea Factory", "Trans Asia Electronics", "Brandix Garments, Ratmalana", "Liner Clothing, Kandy", "Phoenix Factory, Pannala", "Khalifa Port & Industrial Zone Project, Abhudabi", "MAS Holdings, Thuruliya Garments", "Brandix Garments, Mirigama", "Aitken Spence Factory", "Vario System Factory", "Durbar Lanka Factory", "Inovac Factory, Horana", "Brandix Garments, Avissawella", "Mas Holding Matrix Garments Factory", "Brandix Grament, Welisara", "Ceylon Beverages Horana", "Metrix Garment Stage-11"
      ]
    },
    {
      title: "Special & Solar Projects",
      clients: [
        "Dr Wasantha Dissanayake – 5KW Solar System", "Mr M Rajapakeshe – 10KW Solar System", "Head office – 15KW Solar System"
      ]
    }
  ];

  let activeCategory = null;
  const toggleCategory = (index) => {
    activeCategory = activeCategory === index ? null : index;
  };
</script>

<section class="bg-gray-50/80 border-b border-gray-200 py-24 px-6 text-center">
  <div class="max-w-4xl mx-auto">
    <h1 class="text-4xl md:text-5xl font-bold text-[#041C44] tracking-tight mb-6">Portfolio of major MEP work across Sri Lanka.</h1>
    <p class="text-lg md:text-xl text-gray-600 leading-relaxed max-w-3xl mx-auto m-0">
      Explore completed and ongoing projects across hospitality, commercial, healthcare,
      institutional, and specialist building environments.
    </p>
  </div>
</section>

{#each projectGroups as group}
  <section class="py-24 px-6 max-w-6xl mx-auto">
    <div class="mb-12">
      <h2 class="text-3xl font-bold text-[#041C44] tracking-tight">{group.title}</h2>
    </div>
    <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-8">
      {#each group.projects as project}
        <article class="bg-white rounded-xl overflow-hidden shadow-md transition-all duration-300 hover:-translate-y-1 hover:shadow-xl group flex flex-col border border-transparent hover:border-cyan-500/45">
          <div class="h-56 overflow-hidden flex-shrink-0">
            {#if project[3]}
              <img src="/assets/project location image/moh.jpg" alt={project[0]} class="w-full h-full object-cover scale-[1.2] transition-transform duration-500 group-hover:scale-[1.3]" />
            {:else}
              <img src={project[2]} alt={project[0]} class="w-full h-full object-cover transition-transform duration-500 group-hover:scale-110" />
            {/if}
          </div>
          <div class="p-6 flex flex-col flex-grow">
            <h3 class="text-xl font-semibold text-[#041C44] mb-3">{project[0]}</h3>
            <p class="text-sm text-gray-600 leading-relaxed m-0 mb-4">{project[1]}</p>
            {#if project[3]}
              <div class="mt-auto pt-2">
                <a href={project[2]} target="_blank" rel="noopener noreferrer" class="inline-flex justify-center items-center px-4 py-2 bg-brand text-white font-semibold rounded-lg transition-colors hover:bg-brand-dark text-sm shadow-md">View 3D Tour</a>
              </div>
            {/if}
          </div>
        </article>
      {/each}
    </div>
  </section>


{/each}

<section class="bg-gray-50/80 border-t border-gray-200 py-24 px-6">
  <div class="max-w-4xl mx-auto">
    <div class="text-center mb-16">
      <h2 class="text-3xl md:text-4xl font-bold text-[#041C44] tracking-tight mb-4">Complete Client Roster</h2>
      <p class="text-lg text-gray-600">Explore our extensive history of over 100 successful MEP deliveries across key sectors in Sri Lanka.</p>
    </div>

    <div class="flex flex-col gap-4">
      {#each clientCategories as category, index}
        <div class="bg-white border border-gray-200 rounded-xl overflow-hidden shadow-sm">
          <button class="w-full flex items-center justify-between p-6 text-left bg-transparent border-none cursor-pointer text-lg font-semibold text-[#041C44] hover:bg-gray-50 transition-colors" on:click={() => toggleCategory(index)} aria-expanded={activeCategory === index}>
            {category.title} ({category.clients.length} Projects)
            <span class="relative w-6 h-6 flex-shrink-0 ml-4">
              <span class="absolute top-1/2 left-0 w-full h-0.5 bg-brand -translate-y-1/2 transition-transform duration-300" class:rotate-180={activeCategory === index}></span>
              <span class="absolute top-0 left-1/2 w-0.5 h-full bg-brand -translate-x-1/2 transition-transform duration-300" class:rotate-90={activeCategory === index}></span>
            </span>
          </button>
          <div class="grid transition-all duration-300 ease-in-out" style={activeCategory === index ? 'grid-template-rows: 1fr;' : 'grid-template-rows: 0fr;'}>
            <div class="overflow-hidden">
              <ul class="columns-1 md:columns-2 gap-10 p-0 m-0 pb-6 px-6 list-none text-gray-600 text-sm leading-relaxed">
                {#each category.clients as client}
                  <li class="mb-2 break-inside-avoid relative pl-5 before:content-['•'] before:absolute before:left-0 before:text-brand">{client}</li>
                {/each}
              </ul>
            </div>
          </div>
        </div>
      {/each}
    </div>
  </div>
</section>
