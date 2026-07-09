<script>
  const services = [
    [
      'MVAC Systems', 
      'Air conditioning, ventilation, chilled water systems, fan coil units, and mechanical plant installation.',
      '<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M9.59 4.59A2 2 0 1 1 11 8H2m10.59 11.41A2 2 0 1 0 14 16H2m15.73-8.27A2.5 2.5 0 1 1 19.5 12H2"/></svg>'
    ],
    [
      'Plumbing & Sanitary Drainage', 
      'Water supply, drainage, sanitary systems, and project-specific plumbing solutions.',
      '<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M12 22a7 7 0 0 0 7-7c0-2-1-3.9-3-5.5s-3.5-4-4-6.5c-.5 2.5-2 4.9-4 6.5C6 11.1 5 13 5 15a7 7 0 0 0 7 7z"/></svg>'
    ],
    [
      'Electrical & Lighting Installations', 
      'Electrical infrastructure, high lighting systems, and building services installations.',
      '<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><polygon points="13 2 3 14 12 14 11 22 21 10 12 10 13 2"/></svg>'
    ],
    [
      'Fire Detection & Protection', 
      'Integrated fire detection and protection systems for safer built environments.',
      '<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M8.5 14.5A2.5 2.5 0 0 0 11 12c0-1.38-.5-2-1-3-1.072-2.143-.224-4.054 2-6 .5 2.5 2 4.9 4 6.5 2 1.6 3 3.5 3 5.5a7 7 0 1 1-14 0c0-1.153.433-2.294 1-3a2.5 2.5 0 0 0 2.5 2.5z"/></svg>'
    ],
    [
      'Steel Fabrication', 
      'Workshop-supported fabrication for mechanical, construction, and site-specific requirements.',
      '<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="m15 12-8.5 8.5c-.83.83-2.17.83-3 0 0 0 0 0 0 0a2.12 2.12 0 0 1 0-3L12 9"/><path d="M17.64 15 22 10.64"/><path d="m20.91 11.7-1.25-1.25c-.6-.6-.93-1.4-.93-2.25v-.86L16.01 4.6a5.56 5.56 0 0 0-3.94-1.64H11.2C10.4 2.96 9 2.96 9 2.96c0 0 0 1.4.96 2.2h.86c.85 0 1.65.33 2.25.93l1.25 1.25"/><path d="m11.23 8.78.47.47"/></svg>'
    ],
    [
      'Testing, Balancing & Commissioning', 
      'Air testing, hydro testing, balancing, performance checks, and final commissioning.',
      '<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M16 4h2a2 2 0 0 1 2 2v14a2 2 0 0 1-2 2H6a2 2 0 0 1-2-2V6a2 2 0 0 1 2-2h2"/><rect x="8" y="2" width="8" height="4" rx="1" ry="1"/><path d="m9 14 2 2 4-4"/></svg>'
    ]
  ];
</script>

<section class="page-hero">
  <div class="section" style="grid-template-columns: 1fr;">
    <div>
      
      <h1>MEP services from design to commissioning.</h1>
      <p class="lead">
        ASDA Engineering supports complete MEP delivery for commercial, healthcare,
        hospitality, government, institutional, and industrial environments.
      </p>
    </div>
  </div>
</section>

<section class="section">
  <div class="grid three">
    {#each services as service}
      <article class="card">
        <span class="icon-box">{@html service[2]}</span>
        <h3>{service[0]}</h3>
        <p>{service[1]}</p>
      </article>
    {/each}
  </div>
</section>

<section class="soft-band">
  <div class="section split">
    <img src="/assets/History1.jpg.jpeg" alt="ASDA Engineering workshop facility" />
    <div>
   
      <h2>Structured to support demanding building-services projects.</h2>
      <p>
        With owned plant equipment, a fully equipped workshop, trained technical staff, and a
        trusted subcontractor network, ASDA Engineering can support projects from early
        coordination to final system handover.
      </p>
      <ul class="check-list">
        <li>Consultancy and design coordination</li>
        <li>Building, installation, and site execution</li>
        <li>Testing, balancing, and commissioning</li>
        <li>Maintenance and operational support</li>
      </ul>
    </div>
  </div>
</section>

