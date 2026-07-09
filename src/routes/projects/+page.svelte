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

<section class="page-hero">
  <div class="section" style="grid-template-columns: 1fr;">
    <div>
 
      <h1>Portfolio of major MEP work across Sri Lanka.</h1>
      <p class="lead">
        Explore completed and ongoing projects across hospitality, commercial, healthcare,
        institutional, and specialist building environments.
      </p>
    </div>
    
  </div>
</section>

{#each projectGroups as group}
  <section class="section">
    <div class="section-header">
      <div>
       
        <h2>{group.title}</h2>
      </div>
      
    </div>
    <div class="grid three">
      {#each group.projects as project}
        <article class="project-card">
          {#if project[3]}
            <div style="width: 100%; aspect-ratio: 16 / 10; background: linear-gradient(rgba(0,0,0,0.5), rgba(0,0,0,0.7)), url('/assets/project location image/moh.jpg') center/cover no-repeat; display: flex; align-items: center; justify-content: center; flex-direction: column; gap: 16px; padding: 20px; text-align: center;">
              <a href={project[2]} target="_blank" rel="noopener noreferrer" class="button" style="padding: 0 16px; min-height: 40px; font-size: 0.9rem;">View 3D Tour (Full Screen)</a>
            </div>
          {:else}
            <img src={project[2]} alt={project[0]} />
          {/if}
          <div>
            <span>{group.title}</span>
            <h3>{project[0]}</h3>
            <p>{project[1]}</p>
          </div>
        </article>
      {/each}
    </div>
  </section>


{/each}

<section class="soft-band faq-section">
  <div class="section">
    <div class="section-header center">
      <h2>Complete Client Roster</h2>
      <p>Explore our extensive history of over 100 successful MEP deliveries across key sectors in Sri Lanka.</p>
    </div>

    <div class="faq-accordion">
      {#each clientCategories as category, index}
        <div class="faq-item" class:active={activeCategory === index}>
          <button class="faq-question" on:click={() => toggleCategory(index)} aria-expanded={activeCategory === index}>
            {category.title} ({category.clients.length} Projects)
            <span class="faq-icon"></span>
          </button>
          <div class="faq-answer">
            <ul class="client-list">
              {#each category.clients as client}
                <li>{client}</li>
              {/each}
            </ul>
          </div>
        </div>
      {/each}
    </div>
  </div>
</section>

<style>
  .client-list {
    margin: 0;
    padding: 0 0 0 20px;
    color: var(--muted);
    font-size: 0.95rem;
    line-height: 1.8;
    column-count: 2;
    column-gap: 40px;
  }
  .client-list li {
    margin-bottom: 8px;
    break-inside: avoid-column;
  }
  @media (max-width: 768px) {
    .client-list {
      column-count: 1;
    }
  }
</style>
