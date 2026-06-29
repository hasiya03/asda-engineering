<script>
  const services = [
    ['MVAC Systems', 'Air conditioning, ventilation, chilled water systems, fan coil units, and mechanical plant installation.'],
    ['Plumbing & Sanitary Drainage', 'Water supply, drainage, sanitary systems, and project-specific plumbing solutions.'],
    ['Electrical & Lighting Installations', 'Electrical infrastructure, high lighting systems, and building services installations.'],
    ['Fire Detection & Protection', 'Integrated fire detection and protection systems for safer built environments.'],
    ['Steel Fabrication', 'Workshop-supported fabrication for mechanical, construction, and site-specific requirements.'],
    ['Testing, Balancing & Commissioning', 'Air testing, hydro testing, balancing, performance checks, and final commissioning.']
  ];
</script>

<section class="page-hero">
  <div class="section">
    <div>
      
      <h1 style="font-size: clamp(2.5rem, 5vw, 4rem); line-height: 1.1; margin-bottom: 1rem;">Mechanical, electrical, and plumbing services from design to commissioning.</h1>
      <p class="lead" style="font-size: clamp(1.15rem, 2vw, 1.5rem); line-height: 1.6;">
        ASDA Engineering supports complete MEP delivery for commercial, healthcare,
        hospitality, government, institutional, and industrial environments.
      </p>
    </div>
    <img src="/assets/slider6.jpg.jpeg" alt="Mechanical and electrical installation site" />
  </div>
</section>

<section class="section">
  <div class="grid three">
    {#each services as service, index}
      <article class="card">
        <span class="icon-box">0{index + 1}</span>
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
      <p class="eyebrow">Delivery capability</p>
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

