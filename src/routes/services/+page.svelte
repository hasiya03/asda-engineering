<script>
  const services = [
    [
      'MVAC Systems', 
      'Air conditioning, ventilation, chilled water systems, fan coil units, and mechanical plant installation.',
      '<span class="material-symbols-outlined" style="font-size: 32px;">hvac</span>'
    ],
    [
      'Plumbing & Sanitary Drainage', 
      'Water supply, drainage, sanitary systems, and project-specific plumbing solutions.',
      '<span class="material-symbols-outlined" style="font-size: 32px;">plumbing</span>'
    ],
    [
      'Electrical & Lighting Installations', 
      'Electrical infrastructure, high lighting systems, and building services installations.',
      '<span class="material-symbols-outlined" style="font-size: 32px;">electrical_services</span>'
    ],
    [
      'Fire Detection & Protection', 
      'Integrated fire detection and protection systems for safer built environments.',
      '<span class="material-symbols-outlined" style="font-size: 32px;">fire_extinguisher</span>'
    ],
    [
      'Steel Fabrication', 
      'Workshop-supported fabrication for mechanical, construction, and site-specific requirements.',
      '<span class="material-symbols-outlined" style="font-size: 32px;">construction</span>'
    ],
    [
      'Testing, Balancing & Commissioning', 
      'Air testing, hydro testing, balancing, performance checks, and final commissioning.',
      '<span class="material-symbols-outlined" style="font-size: 32px;">fact_check</span>'
    ]
  ];
</script>

<section class="bg-gray-50/80 border-b border-gray-200 py-24 px-6 text-center">
  <div class="max-w-4xl mx-auto">
    <h1 class="text-4xl md:text-5xl font-bold text-[#041C44] tracking-tight mb-6">MEP services from design to commissioning.</h1>
    <p class="text-lg md:text-xl text-gray-600 leading-relaxed max-w-3xl mx-auto m-0">
      ASDA Engineering supports complete MEP delivery for commercial, healthcare,
      hospitality, government, institutional, and industrial environments.
    </p>
  </div>
</section>

<section class="py-24 px-6 max-w-6xl mx-auto">
  <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
    {#each services as service}
      <article class="bg-white rounded-xl p-8 border border-gray-200 shadow-sm transition-all duration-300 hover:-translate-y-1 hover:shadow-xl text-center hover:border-brand-dark">
        <span class="inline-flex justify-center items-center w-16 h-16 rounded-full bg-green-50 text-brand mb-6 mx-auto">{@html service[2]}</span>
        <h3 class="text-xl font-semibold text-[#041C44] mb-3">{service[0]}</h3>
        <p class="text-sm text-gray-600 leading-relaxed m-0">{service[1]}</p>
      </article>
    {/each}
  </div>
</section>

<section class="bg-gray-50/80 border-t border-gray-200 py-24 px-6">
  <div class="max-w-6xl mx-auto grid grid-cols-1 lg:grid-cols-2 gap-12 items-center">
    <div class="rounded-2xl overflow-hidden shadow-lg">
      <img src="/assets/history_1.jpeg" alt="ASDA Engineering workshop facility" class="w-full h-auto object-cover" />
    </div>
    <div class="flex flex-col gap-6 lg:pr-16 xl:pr-24">
      <h2 class="text-3xl md:text-4xl font-bold text-[#041C44] tracking-tight m-0">Structured to support demanding building-services projects.</h2>
      <p class="text-lg text-gray-600 leading-relaxed m-0">
        With owned plant equipment, a fully equipped workshop, trained technical staff, and a
        trusted subcontractor network, ASDA Engineering can support projects from early
        coordination to final system handover.
      </p>
      <ul class="flex flex-col gap-3 p-0 m-0 list-none mt-4">
        <li class="relative pl-8 text-gray-700 before:content-['✓'] before:absolute before:left-0 before:top-0 before:text-brand before:font-semibold before:text-lg">Consultancy and design coordination</li>
        <li class="relative pl-8 text-gray-700 before:content-['✓'] before:absolute before:left-0 before:top-0 before:text-brand before:font-semibold before:text-lg">Building, installation, and site execution</li>
        <li class="relative pl-8 text-gray-700 before:content-['✓'] before:absolute before:left-0 before:top-0 before:text-brand before:font-semibold before:text-lg">Testing, balancing, and commissioning</li>
        <li class="relative pl-8 text-gray-700 before:content-['✓'] before:absolute before:left-0 before:top-0 before:text-brand before:font-semibold before:text-lg">Maintenance and operational support</li>
      </ul>
    </div>
  </div>
</section>

