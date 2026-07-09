<script>
  const leaders = [
    {
      name: "Nishantha Dissanayake",
      role: "Chairman / Managing Director",
      credential: "PG Dip in Energy Eng. (SL), AMIE (SL), MASHRAE (USA)",
      image:
        "/assets/team%20members/Nishantha_Dissanayake-Chairman-Managing_Director-e1699337723383-qezxl91eo8c7yncu02647w9nc26jo2b5b729y4msro.png",
    },
    {
      name: "Nadeera Herath",
      role: "Director",
      credential: "",
      image:
        "/assets/team%20members/Nadeera_Herath-Director-qdunkjz3qbe8daaj4thfwln9icl6bm4tj4tmi8pulg.png",
    },
    {
      name: "Shantha Balasundaram",
      role: "General Manager - Administration and Operation",
      credential: "",
      image:
        "/assets/team%20members/Shantha-Balasundaram-General-Manager-Administration-and-Operation-qdunuw76wpjs2v9uradpbzpsqxmizr6iyb5wjtdy5g.png",
    },
    {
      name: "Chaminda Pathiraja",
      role: "General Manager - Engineering",
      credential: "",
      image:
        "/assets/team%20members/Chaminda_Pathiraja-General_Manager-Engineering-qduo6o4eizo3j062zvmg2iqonpl2f8xgwldvzlxe78.png",
    },
    {
      name: "Carlton Rodrigo",
      role: "Manager Engineering",
      credential: "",
      image:
        "/assets/team%20members/Carlton-Rodrigo-manager-Engineering-qduoclhrmds6qhk5dxuraiwbi6ddyjgjdxh3xf50ys.png",
    },
    {
      name: "Joy",
      role: "Maintenance Manager",
      credential: "",
      image:
        "/assets/team%20members/Maintenance_Manager-qezxh5gqv8q7bvb6xsdoufia2kdx3l1aewn1loplwk.png",
    },
  ];
  const accreditations = [
    "/assets/our%20accreditions/C1-8.png",
    "/assets/our%20accreditions/C2-5.png",
    "/assets/our%20accreditions/c3-5.png",
    "/assets/our%20accreditions/c4-5.png",
    "/assets/our%20accreditions/c5-4.png",
    "/assets/our%20accreditions/c6-4.png",
    "/assets/our%20accreditions/c7-7.png",
    "/assets/our%20accreditions/c8-2.png",
  ];
</script>

<section class="bg-gray-50/80 border-b border-gray-200 py-24 px-6 text-center">
  <div class="max-w-4xl mx-auto">
    <h1 class="text-4xl md:text-5xl font-bold text-[#041C44] tracking-tight mb-6">Trusted MEP engineering since 2002.</h1>
    <p class="text-lg md:text-xl text-gray-600 leading-relaxed max-w-3xl mx-auto m-0">
      ASDA Engineering is a Sri Lankan mechanical, electrical, and plumbing
      engineering contractor serving state and private-sector construction
      projects with disciplined execution, trained teams, and long-term client
      focus.
    </p>
  </div>
</section>

<section class="py-24 px-6 bg-white max-w-6xl mx-auto border-b border-gray-200">
  <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
    <div class="bg-gray-50 rounded-xl p-8 border border-gray-200 shadow-sm text-center">
      <div class="inline-flex justify-center items-center w-20 h-20 rounded-full bg-white shadow-sm text-brand mb-6 mx-auto">
        <span class="material-symbols-outlined text-5xl">target</span>
      </div>
      <h2 class="text-2xl font-bold text-[#041C44] mb-4">Our Mission</h2>
      <p class="text-lg text-gray-600 leading-relaxed">
        To be the leading mechanical and electrical service provider in
        construction and related fields for both state and private-sector clients.
      </p>
    </div>
    <div class="bg-gray-50 rounded-xl p-8 border border-gray-200 shadow-sm text-center">
      <div class="inline-flex justify-center items-center w-20 h-20 rounded-full bg-white shadow-sm text-brand mb-6 mx-auto">
        <span class="material-symbols-outlined text-5xl">visibility</span>
      </div>
      <h2 class="text-2xl font-bold text-[#041C44] mb-4">Our Vision</h2>
      <p class="text-lg text-gray-600 leading-relaxed">
        To become a premier player in Sri Lanka's growing market as a trusted
        provider of engineering products and services.
      </p>
    </div>
  </div>
</section>

<!-- <section class="soft-band">
  <div class="section">
    <div class="section-header">
      <div>
        <p class="eyebrow">Company scale</p>
        <h2>Built for quality, speed, and accountability.</h2>
      </div>
      <p>
        Our teams receive regular training on current regulations, management techniques,
        safety practices, and engineering standards to maintain quality across delivery.
      </p>
    </div>
    <div class="stats-row">
      <article class="card stat border border-transparent hover:border-cyan-500/45">
        <strong>2002</strong>
        <span>Established</span>
      </article>
      <article class="card stat border border-transparent hover:border-cyan-500/45">
        <strong>150+</strong>
        <span>Employees</span>
      </article>
      <article class="card stat border border-transparent hover:border-cyan-500/45">
        <strong>Rs. 900M+</strong>
        <span>Annual turnover</span>
      </article>
      <article class="card stat border border-transparent hover:border-cyan-500/45">
        <strong>ISO</strong>
        <span>9001:2015 certified</span>
      </article>
      <article class="card stat border border-transparent hover:border-cyan-500/45">
        <strong>EM 2</strong>
        <span>ICTAD registered</span>
      </article>
    </div>
  </div>
</section> -->

<section class="py-24 px-6 max-w-6xl mx-auto border-b border-gray-200 text-center">
  <div class="max-w-3xl mx-auto mb-16">
    <h2 class="text-3xl md:text-4xl font-bold text-[#041C44] tracking-tight mb-4">Industry recognized standards</h2>
    <p class="text-lg text-gray-600 leading-relaxed">
      ASDA Engineering's accreditations reinforce our commitment to professional
      standards, quality management, and dependable project execution.
    </p>
  </div>
  <div class="flex flex-wrap justify-center items-center gap-8 md:gap-12 opacity-80 mix-blend-multiply">
    {#each accreditations as accreditation}
      <div class="w-32 md:w-40 flex justify-center items-center p-4 transition-all duration-300 hover:opacity-100 hover:scale-105 filter grayscale hover:grayscale-0">
        <img src={accreditation} alt="ASDA Engineering accreditation logo" class="max-w-full h-auto object-contain" />
      </div>
    {/each}
  </div>
</section>
<section class="py-24 px-6 max-w-6xl mx-auto">
  <div class="text-center max-w-3xl mx-auto mb-16">
    <h2 class="text-3xl md:text-4xl font-bold text-[#041C44] tracking-tight mb-4">Our Expertise</h2>
  </div>
  <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-8">
    {#each leaders as leader}
      <article class="bg-white rounded-xl overflow-hidden shadow-sm border border-gray-200 transition-all duration-300 hover:-translate-y-1 hover:shadow-xl group hover:border-cyan-500/45">
        <div class="aspect-square bg-gray-50 flex items-end justify-center overflow-hidden">
          <img src={leader.image} alt={leader.name} class="w-full h-full object-cover transition-transform duration-500 group-hover:scale-105" />
        </div>
        <div class="p-6 text-center">
          <h3 class="text-xl font-semibold text-[#041C44] mb-2">{leader.name}</h3>
          <p class="text-brand font-semibold text-sm tracking-wide uppercase m-0">{leader.role}</p>
          {#if leader.credential}
            <p class="text-gray-500 text-xs mt-2 m-0">{leader.credential}</p>
          {/if}
        </div>
      </article>
    {/each}
  </div>
</section>
