<script>
  import { onMount } from 'svelte';
  import { tweened } from 'svelte/motion';
  import { cubicOut } from 'svelte/easing';
  import { siteRevealed } from '../store.js';

  const services = [
    ['<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M9.59 4.59A2 2 0 1 1 11 8H2m10.59 11.41A2 2 0 1 0 14 16H2m15.73-8.27A2.5 2.5 0 1 1 19.5 12H2"/></svg>', 'MVAC Systems', 'Air conditioning, ventilation, chilled water systems, FCUs, and related mechanical services.'],
    ['<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M12 22a7 7 0 0 0 7-7c0-2-1-3.9-3-5.5s-3.5-4-4-6.5c-.5 2.5-2 4.9-4 6.5C6 11.1 5 13 5 15a7 7 0 0 0 7 7z"/></svg>', 'Plumbing & Sanitary Drainage', 'Water supply, sanitary drainage, and plumbing systems for demanding building environments.'],
    ['<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><polygon points="13 2 3 14 12 14 11 22 21 10 12 10 13 2"/></svg>', 'Electrical & Lighting', 'High-quality lighting systems, electrical infrastructure, and building-services installations.'],
    ['<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M8.5 14.5A2.5 2.5 0 0 0 11 12c0-1.38-.5-2-1-3-1.072-2.143-.224-4.054 2-6 .5 2.5 2 4.9 4 6.5 2 1.6 3 3.5 3 5.5a7 7 0 1 1-14 0c0-1.153.433-2.294 1-3a2.5 2.5 0 0 0 2.5 2.5z"/></svg>', 'Fire Protection', 'Fire detection and protection systems designed for safer, more compliant built environments.'],
    ['<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="m15 12-8.5 8.5c-.83.83-2.17.83-3 0 0 0 0 0 0 0a2.12 2.12 0 0 1 0-3L12 9"/><path d="M17.64 15 22 10.64"/><path d="m20.91 11.7-1.25-1.25c-.6-.6-.93-1.4-.93-2.25v-.86L16.01 4.6a5.56 5.56 0 0 0-3.94-1.64H11.2C10.4 2.96 9 2.96 9 2.96c0 0 0 1.4.96 2.2h.86c.85 0 1.65.33 2.25.93l1.25 1.25"/><path d="m11.23 8.78.47.47"/></svg>', 'Steel Fabrication', 'Workshop-supported steel fabrication for project-specific mechanical and site requirements.'],
    ['<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M16 4h2a2 2 0 0 1 2 2v14a2 2 0 0 1-2 2H6a2 2 0 0 1-2-2V6a2 2 0 0 1 2-2h2"/><rect x="8" y="2" width="8" height="4" rx="1" ry="1"/><path d="m9 14 2 2 4-4"/></svg>', 'Testing & Commissioning', 'Air testing, hydro testing, balancing, performance validation, and final commissioning.']
  ];

  const projects = [
    {
      category: 'Hospitality & Commercial',
      title: 'Kingsbury Hotel, Colombo',
      image: '/assets/project%20location%20image/Kingsbury-Hotel.jpg.jpeg',
      detail: '412 TR chiller capacity with 255 fan coil units.'
    },
    {
      category: 'Healthcare',
      title: 'Army Hospital, Narahenpita',
      image: '/assets/project%20location%20image/Army-Hospital-Narahenpita.jpg.jpeg',
      detail: '660 TR capacity and 400 fan coil units.'
    },
    {
      category: 'Commercial',
      title: 'Sri Lanka Insurance Co., Colombo',
      image: '/assets/project%20location%20image/srilanka-insuarance.jpg.jpeg',
      detail: '750 TR capacity for a major commercial facility.'
    }
  ];

  const clientLogos = [
    '/assets/Clients_logo/kingsbury-logo.png',
    '/assets/Clients_logo/SLIC-logo.png',
    '/assets/Clients_logo/hemas-hosptal.png',
    '/assets/Clients_logo/MAS_Holdings.png',
    '/assets/Clients_logo/brandix-logo.png',
    '/assets/Clients_logo/cinnamon-grande-logo.png',
    '/assets/Clients_logo/McDonalds_logo.png',
    '/assets/Clients_logo/Lb_finance-logo.png',
    '/assets/Clients_logo/CBL-logo.png',
    '/assets/Clients_logo/ansell_logo.png'
  ];

  const carouselLogos = [...clientLogos, ...clientLogos];

  const heroRow1 = [
    { class: 'img-1', src: '/assets/project%20location%20image/Kingsbury-Hotel.jpg.jpeg' },
    { class: 'img-2', src: '/assets/project%20location%20image/Army-Hospital-Narahenpita.jpg.jpeg' },
    { class: 'img-3', src: '/assets/project%20location%20image/srilanka-insuarance.jpg.jpeg' },
    { class: 'img-4', src: '/assets/project location image/15 NOS.jpg' },
  ];
  const heroRow2 = [
    { class: 'img-5', src: '/assets/project location image/Tangerine-kalutara.jpg.jpeg' },
    { class: 'img-6', src: '/assets/project location image/Japanese Embassy House Project.jpg' },
    { class: 'img-7', src: '/assets/project location image/Examination Department Pallawatte.jpg' },
    { class: 'img-8', src: '/assets/project location image/Taru Villa Hotel Bentota.jpg' },
  ];
  const heroRow3 = [
    { class: 'img-9', src: '/assets/project location image/Mr. Dinesh Rodrigo Office Complex.jpg' },
    { class: 'img-10', src: '/assets/project location image/AMBEWELLA PATTIPOLA FARM.jpg' },
    { class: 'img-11', src: '/assets/project location image/World Trade Centre, Colombo.webp' },
  ];

  const faqs = [
    {
      question: "What areas of Sri Lanka do you operate in?",
      answer: "We provide MEP engineering services for commercial, healthcare, and state-sector projects across all major districts in Sri Lanka."
    },
    {
      question: "Do you handle both design and installation?",
      answer: "Yes, we offer comprehensive end-to-end services, from initial consultancy and system design to complete installation, testing, and commissioning."
    },
    {
      question: "Are your engineering practices certified?",
      answer: "Absolutely. ASDA Engineering is ISO 9001:2015 certified and registered as an ICTAD EM 2 contractor, ensuring all work meets rigorous quality and safety standards."
    },
    {
      question: "Do you provide post-installation maintenance?",
      answer: "We offer dedicated maintenance and support services to ensure your mechanical, electrical, and plumbing systems run efficiently long after final commissioning."
    }
  ];

  let activeFaq = null;
  const toggleFaq = (index) => {
    activeFaq = activeFaq === index ? null : index;
  };

  const numProjects = tweened(0, { duration: 2500, easing: cubicOut });
  const numEmployees = tweened(0, { duration: 2500, easing: cubicOut });
  const numTurnover = tweened(0, { duration: 2500, easing: cubicOut });

  $: if ($siteRevealed) {
    numProjects.set(100);
    numEmployees.set(150);
    numTurnover.set(900);
  }
</script>

<section class="modern-hero">
  <div class="modern-hero-content">
    <h1 class="modern-title">
      Engineered to Run Flawlessly.<br/>
      Built to Last.
    </h1>
    <p class="modern-lead">
      Don't let poorly designed systems derail your operations. We provide expert consultancy, installation, and balancing for MEP systems across Sri Lanka, ensuring your building runs at peak efficiency from day one.
    </p>

    <div class="modern-stats">
      <div class="modern-stat">
        <strong>{Math.floor($numProjects)}+</strong>
        <span>Projects</span>
      </div>
      <div class="modern-stat">
        <strong>{Math.floor($numEmployees)}+</strong>
        <span>Employees</span>
      </div>
      <div class="modern-stat">
        <strong>{Math.floor($numTurnover)}M+</strong>
        <span>Annual Turnover</span>
      </div>
    </div>

    <div class="modern-actions">
      <a class="button" href="/contact">Request a Consultation</a>
      <a class="button secondary" href="/projects">View Projects</a>
    </div>
  </div>

  <div class="floating-images">
    <div class="hero-row">
      <div class="hero-track">
        {#each heroRow1 as img}
          <img class="float-img {img.class}" src={img.src} alt="" />
        {/each}
        {#each heroRow1 as img}
          <img class="float-img {img.class} duplicate" src={img.src} alt="" aria-hidden="true" />
        {/each}
      </div>
    </div>
    <div class="hero-row">
      <div class="hero-track reverse">
        {#each heroRow2 as img}
          <img class="float-img {img.class}" src={img.src} alt="" />
        {/each}
        {#each heroRow2 as img}
          <img class="float-img {img.class} duplicate" src={img.src} alt="" aria-hidden="true" />
        {/each}
      </div>
    </div>
    <div class="hero-row">
      <div class="hero-track">
        {#each heroRow3 as img}
          <img class="float-img {img.class}" src={img.src} alt="" />
        {/each}
        {#each heroRow3 as img}
          <img class="float-img {img.class} duplicate" src={img.src} alt="" aria-hidden="true" />
        {/each}
      </div>
    </div>
  </div>
</section>


<section class="trusted-carousel-section" aria-label="Trusted clients and project partners">
  <div class="trusted-heading">
    
    <h2>Clients and project partners.</h2>
  </div>
  <div class="logo-carousel" aria-hidden="true">
    <div class="logo-track">
      {#each carouselLogos as logo}
        <div class="logo-tile carousel-tile">
          <img src={logo} alt="" />
        </div>
      {/each}
    </div>
  </div>
</section>

<section class="soft-band">
  <div class="section" style="max-width: 1200px; margin: 0 auto;">
    <div style="text-align: center; max-width: 800px; margin: 0 auto 3rem auto;">
      <h2>Our Approach & Capabilities</h2>
      <p style="font-size: 1.15rem; color: var(--muted); margin-bottom: 0;">
        ASDA Engineering delivers comprehensive solutions across traditional construction, Engineering, Procurement, and Construction (EPC), partnering, and joint venture contracts. Our core strength lies in bridging the gap between advanced technical engineering and strictly disciplined on-site execution.
      </p>
    </div>
    
    <div class="advantages-grid">
      <article class="card">
        <h4 style="font-size: 1.2rem; margin-bottom: 12px;">End-to-End Execution</h4>
        <p style="font-size: 0.95rem; color: var(--muted); margin-bottom: 0;">Complete consultancy, design, build, installation, and commissioning capabilities.</p>
      </article>
      <article class="card">
        <h4 style="font-size: 1.2rem; margin-bottom: 12px;">In-House Infrastructure</h4>
        <p style="font-size: 0.95rem; color: var(--muted); margin-bottom: 0;">We maintain our own plant equipment and a fully equipped workshop facility, ensuring zero delays.</p>
      </article>
      <article class="card">
        <h4 style="font-size: 1.2rem; margin-bottom: 12px;">Certified Excellence</h4>
        <p style="font-size: 0.95rem; color: var(--muted); margin-bottom: 0;">Operating with ISO-certified quality management and proud ICTAD EM 2 contractor status.</p>
      </article>
      <article class="card">
        <h4 style="font-size: 1.2rem; margin-bottom: 12px;">Reliable Support</h4>
        <p style="font-size: 0.95rem; color: var(--muted); margin-bottom: 0;">Cost-conscious planning and highly responsive support across every single project stage.</p>
      </article>
    </div>
  </div>
</section>

<section class="section">
  <div class="section-header">
    <div>
   
      <h2>Proven experience across Sri Lanka's critical built environments.</h2>
    </div>
    <p>
      ASDA Engineering has delivered major hospitality, commercial, healthcare, government,
      and institutional MEP works with significant plant capacity and technical scope.
    </p>
  </div>

  <div class="grid three">
    {#each projects as project}
      <article class="project-card">
        <img src={project.image} alt={project.title} />
        <div>
          <span>{project.category}</span>
          <h3>{project.title}</h3>
          <p>{project.detail}</p>
        </div>
      </article>
    {/each}
  </div>
  <div class="cta-row">
    <a class="button" href="/projects">Explore Portfolio</a>
  </div>
</section>

<section class="points-section">
  <div class="points-bg" style="background-image: url('/assets/who_are_we1.jpg.jpeg');"></div>
  <div class="points-overlay"></div>
  <div class="section" style="position: relative; z-index: 2;">
    <div class="grid three points-grid">
      <article class="card point-card">
        <span class="point-icon"><svg xmlns="http://www.w3.org/2000/svg" width="40" height="40" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="8" r="6"/><path d="M15.477 12.89 17 22l-5-3-5 3 1.523-9.11"/></svg></span>
        <h3>Over Two Decades of Experience</h3>
        <p>Established in 2002, we bring a long-standing, strong reputation as a trusted MEP engineering contractor to every project.</p>
      </article>
      <article class="card point-card">
        <span class="point-icon"><svg xmlns="http://www.w3.org/2000/svg" width="40" height="40" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><polygon points="13 2 3 14 12 14 11 22 21 10 12 10 13 2"/></svg></span>
        <h3>Rapid & Responsive Service</h3>
        <p>We prioritize rapid response times and attentive service, ensuring your project keeps moving without unnecessary delays.</p>
      </article>
      <article class="card point-card">
        <span class="point-icon"><svg xmlns="http://www.w3.org/2000/svg" width="40" height="40" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M16 21v-2a4 4 0 0 0-4-4H6a4 4 0 0 0-4 4v2"/><circle cx="9" cy="7" r="4"/><path d="M22 21v-2a4 4 0 0 0-3-3.87"/><path d="M16 3.13a4 4 0 0 1 0 7.75"/></svg></span>
        <h3>Focus on Long-Term Partnerships</h3>
        <p>We aren't just looking for a single contract; we approach every project with the goal of building lasting, collaborative relationships.</p>
      </article>
      <article class="card point-card">
        <span class="point-icon"><svg xmlns="http://www.w3.org/2000/svg" width="40" height="40" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><line x1="12" y1="2" x2="12" y2="22"/><path d="M17 5H9.5a3.5 3.5 0 0 0 0 7h5a3.5 3.5 0 0 1 0 7H6"/></svg></span>
        <h3>Cost-Effective Project Delivery</h3>
        <p>High-quality engineering shouldn't break the budget. We are committed to delivering exceptional results at an affordable price point.</p>
      </article>
      <article class="card point-card">
        <span class="point-icon"><svg xmlns="http://www.w3.org/2000/svg" width="40" height="40" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M12 22s8-4 8-10V5l-8-3-8 3v7c0 6 8 10 8 10z"/><path d="m9 12 2 2 4-4"/></svg></span>
        <h3>Strict Site Discipline & Responsibility</h3>
        <p>We operate with high technical capability and strict on-site discipline, guaranteeing that all work is completed safely and responsibly.</p>
      </article>
      <article class="card point-card">
        <span class="point-icon"><svg xmlns="http://www.w3.org/2000/svg" width="40" height="40" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect width="20" height="14" x="2" y="7" rx="2" ry="2"/><path d="M16 21V5a2 2 0 0 0-2-2h-4a2 2 0 0 0-2 2v16"/></svg></span>
        <h3>Trusted by the Public & Private Sectors</h3>
        <p>Our high rate of repeat contracts with local contractors, councils, and state departments proves the confidence clients place in our work.</p>
      </article>
    </div>
  </div>
</section>

<section class="section">
  <div class="section-header">
    <div>
   
      <h2>Complete MEP capability under one engineering partner.</h2>
    </div>
    
  </div>

  <div class="grid three">
    {#each services as service}
      <article class="card">
        <span class="icon-box">{@html service[0]}</span>
        <h3>{service[1]}</h3>
        <p>{service[2]}</p>
      </article>
    {/each}
  </div>
</section>

<section class="soft-band faq-section">
  <div class="section">
    <div class="section-header center">
      <h2>Frequently Asked Questions</h2>
      <p>Common questions about our MEP engineering capability and project delivery.</p>
    </div>

    <div class="faq-accordion">
      {#each faqs as faq, index}
        <div class="faq-item" class:active={activeFaq === index}>
          <button class="faq-question" on:click={() => toggleFaq(index)} aria-expanded={activeFaq === index}>
            {faq.question}
            <span class="faq-icon"></span>
          </button>
          <div class="faq-answer">
            <p>{faq.answer}</p>
          </div>
        </div>
      {/each}
    </div>
  </div>
</section>
