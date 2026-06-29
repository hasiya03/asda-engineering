<script>
  import { onMount } from 'svelte';
  import { tweened } from 'svelte/motion';
  import { cubicOut } from 'svelte/easing';
  import { siteRevealed } from '../store.js';

  const services = [
    ['01', 'MVAC Systems', 'Air conditioning, ventilation, chilled water systems, FCUs, and related mechanical services.'],
    ['02', 'Plumbing & Sanitary Drainage', 'Water supply, sanitary drainage, and plumbing systems for demanding building environments.'],
    ['03', 'Electrical & Lighting', 'High-quality lighting systems, electrical infrastructure, and building-services installations.'],
    ['04', 'Fire Protection', 'Fire detection and protection systems designed for safer, more compliant built environments.'],
    ['05', 'Steel Fabrication', 'Workshop-supported steel fabrication for project-specific mechanical and site requirements.'],
    ['06', 'Testing & Commissioning', 'Air testing, hydro testing, balancing, performance validation, and final commissioning.']
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
      Mechanical, Electrical <br/>
      Plumbing Engineers
    </h1>
    <p class="modern-lead">
      ASDA Engineering delivers consultancy, design, building, installation, testing,
      balancing, and commissioning services for mechanical, electrical, and plumbing systems
      across Sri Lanka.
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
    <img class="float-img img-1" src="/assets/project%20location%20image/Kingsbury-Hotel.jpg.jpeg" alt="" />
    <img class="float-img img-2" src="/assets/project%20location%20image/Army-Hospital-Narahenpita.jpg.jpeg" alt="" />
    <img class="float-img img-3" src="/assets/project%20location%20image/srilanka-insuarance.jpg.jpeg" alt="" />
    <img class="float-img img-4" src="/assets/project location image/15 NOS.jpg" alt="" />
    <img class="float-img img-5" src="/assets/project location image/Tangerine-kalutara.jpg.jpeg" alt="" />
    <img class="float-img img-6" src="/assets/project location image/Japanese Embassy House Project.jpg" alt="" />
    <img class="float-img img-7" src="/assets/project location image/Examination Department Pallawatte.jpg" alt="" />
    <img class="float-img img-8" src="/assets/project location image/Taru Villa Hotel Bentota.jpg" alt="" />
    <img class="float-img img-9" src="/assets/project location image/Mr. Dinesh Rodrigo Office Complex.jpg" alt="" />
    <img class="float-img img-10" src="/assets/project location image/AMBEWELLA PATTIPOLA FARM.jpg" alt="" />
    <img class="float-img img-11" src="/assets/project location image/World Trade Centre, Colombo.webp" alt="" />
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
  <div class="section split">
    <div>
    
      <h2>Practical delivery models for demanding projects.</h2>
      <p>
        ASDA Engineering provides viable solutions across traditional construction,
        engineering procurement construction, partnering, and joint venture contracts. Our
        strength lies in combining technical engineering knowledge with disciplined site
        execution.
      </p>
      <ul class="check-list">
        <li>Consultancy, design, build, installation, and commissioning capability</li>
        <li>Owned plant equipment and a fully equipped workshop facility</li>
        <li>ISO-certified quality management and ICTAD EM 2 contractor status</li>
        <li>Cost-conscious and responsive support across project stages</li>
      </ul>
    </div>
    <img src="/assets/History2.jpg.jpeg" alt="ASDA Engineering workshop and fabrication capability" />
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

<section class="soft-band">
  <div class="section split">
    <img src="/assets/who_are_we1.jpg.jpeg" alt="ASDA Engineering team and project environment" />
    <div>
    
      <h2>Reliable engineering. Responsive service. Long-term partnerships.</h2>
      <p>
        Since 2002, ASDA Engineering has built a strong reputation as a trusted MEP
        engineering contractor. We approach every project with a focus on long-term
        relationships, rapid response, attentive service, and affordable project delivery.
      </p>
      <p>
        Our repeat contracts with local contractors, councils, and state departments reflect
        the confidence clients place in our technical capability, site discipline, and
        commitment to completing work responsibly.
      </p>
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
        <span class="icon-box">{service[0]}</span>
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
