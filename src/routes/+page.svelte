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

<section class="relative flex flex-col items-center justify-center text-center min-h-[calc(100vh-116px)] px-5 py-24 overflow-hidden before:content-[''] before:absolute before:inset-0 before:bg-white/75 before:z-10 before:pointer-events-none">
  <div class="relative z-20 max-w-6xl mx-auto">
    <h1 class="text-[clamp(2rem,4.5vw,4rem)] leading-[1.1] font-bold text-[#041C44] mb-6">
      Engineered to Run Flawlessly.<br/>
      Built to Last.
    </h1>
    <p class="text-[clamp(1.1rem,2vw,1.25rem)] text-gray-600 leading-relaxed max-w-2xl mx-auto mb-12">
      Don't let poorly designed systems derail your operations. We provide expert consultancy, installation, and balancing for MEP systems across Sri Lanka, ensuring your building runs at peak efficiency from day one.
    </p>

    <div class="flex flex-wrap justify-center gap-8 md:gap-16 mb-12">
      <div class="flex flex-col items-center">
        <strong class="text-4xl md:text-5xl font-bold text-brand mb-1">{Math.floor($numProjects)}+</strong>
        <span class="text-sm font-semibold uppercase tracking-wider text-gray-500">Projects</span>
      </div>
      <div class="flex flex-col items-center">
        <strong class="text-4xl md:text-5xl font-bold text-brand mb-1">{Math.floor($numEmployees)}+</strong>
        <span class="text-sm font-semibold uppercase tracking-wider text-gray-500">Employees</span>
      </div>
      <div class="flex flex-col items-center">
        <strong class="text-4xl md:text-5xl font-bold text-brand mb-1">{Math.floor($numTurnover)}M+</strong>
        <span class="text-sm font-semibold uppercase tracking-wider text-gray-500">Annual Turnover</span>
      </div>
    </div>

    <div class="flex flex-col sm:flex-row justify-center items-center gap-4">
      <a class="inline-flex justify-center items-center px-8 py-4 bg-brand text-white font-semibold rounded-lg transition-all duration-300 shadow-md hover:bg-[#086330] hover:-translate-y-0.5 hover:shadow-xl w-full sm:w-auto" href="/contact">Request a Consultation</a>
      <a class="inline-flex justify-center items-center px-8 py-4 bg-transparent text-brand font-semibold rounded-lg border-2 border-brand transition-all duration-300 hover:bg-brand hover:text-white hover:-translate-y-0.5 hover:shadow-xl w-full sm:w-auto" href="/projects">View Projects</a>
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

<section class="bg-gray-50/80 border-t border-b border-gray-200 py-20 px-6">
  <div class="max-w-6xl mx-auto">
    <div class="text-center max-w-3xl mx-auto mb-16">
      <h2 class="text-3xl md:text-4xl font-bold text-[#041C44] mb-6 tracking-tight">Our Approach & Capabilities</h2>
      <p class="text-lg text-gray-600 leading-relaxed">
        ASDA Engineering delivers comprehensive solutions across traditional construction, Engineering, Procurement, and Construction (EPC), partnering, and joint venture contracts. Our core strength lies in bridging the gap between advanced technical engineering and strictly disciplined on-site execution.
      </p>
    </div>
    
    <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-8">
      <article class="bg-white rounded-xl p-8 border border-gray-200 shadow-sm transition-all duration-300 hover:-translate-y-1 hover:shadow-xl hover:border-cyan-500/45">
        <span class="material-symbols-outlined block text-brand text-4xl mb-4">layers</span>
        <h4 class="text-xl font-semibold text-[#041C44] mb-3">End-to-End Execution</h4>
        <p class="text-gray-600 text-sm leading-relaxed">Complete consultancy, design, build, installation, and commissioning capabilities.</p>
      </article>
      <article class="bg-white rounded-xl p-8 border border-gray-200 shadow-sm transition-all duration-300 hover:-translate-y-1 hover:shadow-xl hover:border-cyan-500/45">
        <span class="material-symbols-outlined block text-brand text-4xl mb-4">domain</span>
        <h4 class="text-xl font-semibold text-[#041C44] mb-3">In-House Infrastructure</h4>
        <p class="text-gray-600 text-sm leading-relaxed">We maintain our own plant equipment and a fully equipped workshop facility, ensuring zero delays.</p>
      </article>
      <article class="bg-white rounded-xl p-8 border border-gray-200 shadow-sm transition-all duration-300 hover:-translate-y-1 hover:shadow-xl hover:border-cyan-500/45">
        <span class="material-symbols-outlined block text-brand text-4xl mb-4">verified</span>
        <h4 class="text-xl font-semibold text-[#041C44] mb-3">Certified Excellence</h4>
        <p class="text-gray-600 text-sm leading-relaxed">Operating with ISO-certified quality management and proud ICTAD EM 2 contractor status.</p>
      </article>
      <article class="bg-white rounded-xl p-8 border border-gray-200 shadow-sm transition-all duration-300 hover:-translate-y-1 hover:shadow-xl hover:border-cyan-500/45">
        <span class="material-symbols-outlined block text-brand text-4xl mb-4">security</span>
        <h4 class="text-xl font-semibold text-[#041C44] mb-3">Reliable Support</h4>
        <p class="text-gray-600 text-sm leading-relaxed">Cost-conscious planning and highly responsive support across every single project stage.</p>
      </article>
    </div>
  </div>
</section>

<section class="py-24 px-6 max-w-6xl mx-auto">
  <div class="mb-16 text-center max-w-3xl mx-auto">
    <h2 class="text-3xl md:text-4xl font-bold text-[#041C44] tracking-tight">Proven experience across Sri Lanka's critical built environments.</h2>
  </div>

  <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-8">
    {#each projects as project}
      <article class="bg-white rounded-xl overflow-hidden shadow-md transition-all duration-300 hover:-translate-y-1 hover:shadow-xl group border border-transparent hover:border-cyan-500/45">
        <div class="h-56 overflow-hidden">
          <img src={project.image} alt={project.title} class="w-full h-full object-cover transition-transform duration-500 group-hover:scale-110" />
        </div>
        <div class="p-6">
          <span class="inline-block px-3 py-1 bg-green-50 text-brand text-xs font-semibold uppercase tracking-wider rounded-full mb-4">{project.category}</span>
          <h3 class="text-xl font-semibold text-[#041C44] mb-3">{project.title}</h3>
          <p class="text-sm text-gray-600 leading-relaxed m-0">{project.detail}</p>
        </div>
      </article>
    {/each}
  </div>
  <div class="mt-16 flex justify-center">
    <a class="inline-flex justify-center items-center px-8 py-4 bg-brand text-white font-semibold rounded-lg transition-all duration-300 shadow-md hover:bg-brand-dark hover:-translate-y-0.5 hover:shadow-xl" href="/projects">Explore Portfolio</a>
  </div>
</section>

<section class="relative py-24 px-6 overflow-hidden min-h-[90vh] flex items-center justify-center">
  <div class="absolute inset-0 bg-cover bg-center bg-no-repeat" style="background-image: url('/assets/who_are_we1.jpg.jpeg');"></div>
  <div class="absolute inset-0 bg-[#041C44]/90 z-10"></div>
  <div class="relative z-20 max-w-6xl mx-auto w-full">
    <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
      <article class="bg-white/10 backdrop-blur-md rounded-xl p-8 border border-white/20 text-white transition-transform duration-300 hover:-translate-y-1 hover:border-cyan-500/45">
        <span class="material-symbols-outlined block text-3xl text-brand mb-4">history</span>
        <h3 class="text-xl font-semibold text-white mb-3">Over Two Decades of Experience</h3>
        <p class="text-sm text-white/80 leading-relaxed">Established in 2002, we bring a long-standing, strong reputation as a trusted MEP engineering contractor to every project.</p>
      </article>
      <article class="bg-white/10 backdrop-blur-md rounded-xl p-8 border border-white/20 text-white transition-transform duration-300 hover:-translate-y-1 hover:border-cyan-500/45">
        <span class="material-symbols-outlined block text-3xl text-brand mb-4">flash_on</span>
        <h3 class="text-xl font-semibold text-white mb-3">Rapid & Responsive Service</h3>
        <p class="text-sm text-white/80 leading-relaxed">We prioritize rapid response times and attentive service, ensuring your project keeps moving without unnecessary delays.</p>
      </article>
      <article class="bg-white/10 backdrop-blur-md rounded-xl p-8 border border-white/20 text-white transition-transform duration-300 hover:-translate-y-1 hover:border-cyan-500/45">
        <span class="material-symbols-outlined block text-3xl text-brand mb-4">handshake</span>
        <h3 class="text-xl font-semibold text-white mb-3">Focus on Long-Term Partnerships</h3>
        <p class="text-sm text-white/80 leading-relaxed">We aren't just looking for a single contract; we approach every project with the goal of building lasting, collaborative relationships.</p>
      </article>
      <article class="bg-white/10 backdrop-blur-md rounded-xl p-8 border border-white/20 text-white transition-transform duration-300 hover:-translate-y-1 hover:border-cyan-500/45">
        <span class="material-symbols-outlined block text-3xl text-brand mb-4">price_check</span>
        <h3 class="text-xl font-semibold text-white mb-3">Cost-Effective Project Delivery</h3>
        <p class="text-sm text-white/80 leading-relaxed">High-quality engineering shouldn't break the budget. We are committed to delivering exceptional results at an affordable price point.</p>
      </article>
      <article class="bg-white/10 backdrop-blur-md rounded-xl p-8 border border-white/20 text-white transition-transform duration-300 hover:-translate-y-1 hover:border-cyan-500/45">
        <span class="material-symbols-outlined block text-3xl text-brand mb-4">rule</span>
        <h3 class="text-xl font-semibold text-white mb-3">Strict Site Discipline & Responsibility</h3>
        <p class="text-sm text-white/80 leading-relaxed">We operate with high technical capability and strict on-site discipline, guaranteeing that all work is completed safely and responsibly.</p>
      </article>
      <article class="bg-white/10 backdrop-blur-md rounded-xl p-8 border border-white/20 text-white transition-transform duration-300 hover:-translate-y-1 hover:border-cyan-500/45">
        <span class="material-symbols-outlined block text-3xl text-brand mb-4">verified_user</span>
        <h3 class="text-xl font-semibold text-white mb-3">Trusted by the Public & Private Sectors</h3>
        <p class="text-sm text-white/80 leading-relaxed">Our high rate of repeat contracts with local contractors, councils, and state departments proves the confidence clients place in our work.</p>
      </article>
    </div>
  </div>
</section>

<section class="py-24 px-6 max-w-6xl mx-auto border-t border-gray-200">
  <div class="mb-16 text-center">
    <h2 class="text-3xl md:text-4xl font-bold text-[#041C44] tracking-tight">Complete MEP capability under one engineering partner.</h2>
  </div>

  <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
    {#each services as service}
      <article class="bg-white rounded-xl p-8 border border-gray-200 shadow-sm transition-all duration-300 hover:-translate-y-1 hover:shadow-xl text-center hover:border-cyan-500/45">
        <span class="inline-flex justify-center items-center w-16 h-16 rounded-full bg-green-50 text-brand mb-6 mx-auto">{@html service[0]}</span>
        <h3 class="text-xl font-semibold text-[#041C44] mb-3">{service[1]}</h3>
        <p class="text-sm text-gray-600 leading-relaxed m-0">{service[2]}</p>
      </article>
    {/each}
  </div>
</section>

<section class="bg-gray-50/80 border-t border-gray-200 py-24 px-6">
  <div class="max-w-4xl mx-auto">
    <div class="text-center mb-16">
      <h2 class="text-3xl md:text-4xl font-bold text-[#041C44] tracking-tight mb-4">Frequently Asked Questions</h2>
      <p class="text-lg text-gray-600">Common questions about our MEP engineering capability and project delivery.</p>
    </div>

    <div class="flex flex-col gap-4">
      {#each faqs as faq, index}
        <div class="bg-white border border-gray-200 rounded-xl overflow-hidden shadow-sm">
          <button class="w-full flex items-center justify-between p-6 text-left bg-transparent border-none cursor-pointer text-lg font-semibold text-[#041C44] hover:bg-gray-50 transition-colors" on:click={() => toggleFaq(index)} aria-expanded={activeFaq === index}>
            {faq.question}
            <span class="relative w-6 h-6 flex-shrink-0 ml-4">
              <span class="absolute top-1/2 left-0 w-full h-0.5 bg-brand -translate-y-1/2 transition-transform duration-300" class:rotate-180={activeFaq === index}></span>
              <span class="absolute top-0 left-1/2 w-0.5 h-full bg-brand -translate-x-1/2 transition-transform duration-300" class:rotate-90={activeFaq === index}></span>
            </span>
          </button>
          <div class="grid transition-all duration-300 ease-in-out" style={activeFaq === index ? 'grid-template-rows: 1fr;' : 'grid-template-rows: 0fr;'}>
            <div class="overflow-hidden">
              <p class="p-6 pt-0 m-0 text-gray-600 leading-relaxed">
                {faq.answer}
              </p>
            </div>
          </div>
        </div>
      {/each}
    </div>
  </div>
</section>
