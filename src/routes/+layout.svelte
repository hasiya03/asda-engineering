<script>
  import '../app.css';
  import { page } from '$app/stores';
  import { onMount } from 'svelte';
  import { siteRevealed } from '../store.js';

  let isNavOpen = false;
  let showBackToTop = false;

  onMount(() => {
    siteRevealed.set(true);

    const observer = new IntersectionObserver((entries) => {
      entries.forEach(entry => {
        if (entry.isIntersecting) {
          entry.target.classList.add('in-view');
          observer.unobserve(entry.target);
        }
      });
    }, { threshold: 0.1, rootMargin: '0px 0px -50px 0px' });

    const targets = document.querySelectorAll('.section-header, .card, .project-card, .team-card, .mv-card, .info-card');
    targets.forEach(target => {
      target.classList.add('reveal-on-scroll');
      observer.observe(target);
    });
  });

  const checkScroll = () => {
    if (typeof window !== 'undefined') {
      showBackToTop = window.scrollY > 300;
    }
  };

  const scrollToTop = () => {
    if (typeof window !== 'undefined') {
      window.scrollTo({ top: 0, behavior: 'smooth' });
    }
  };

  const navItems = [
    { href: '/', label: 'Home' },
    { href: '/about', label: 'About' },
    { href: '/services', label: 'Services' },
    { href: '/projects', label: 'Projects' },
    { href: '/contact', label: 'Contact' }
  ];

  const closeNav = () => {
    isNavOpen = false;
  };
</script>

<svelte:window on:scroll={checkScroll} />

<svelte:head>
  <title>ASDA Engineering | MEP Engineers & Contractors</title>
</svelte:head>

<header class="sticky top-0 z-50 bg-white border-b border-gray-200">

  <nav class="flex items-center justify-between px-6 py-4 max-w-6xl mx-auto" aria-label="Main navigation">
    <a class="flex-shrink-0" href="/" aria-label="ASDA Engineering home" on:click={closeNav}>
      <img class="h-12 w-auto" src="/assets/Company_logo.png" alt="ASDA Engineering logo" />
    </a>

    <button
      class="nav-toggle"
      type="button"
      aria-label="Toggle navigation menu"
      aria-expanded={isNavOpen}
      on:click={() => (isNavOpen = !isNavOpen)}
    >
      <span></span>
      <span></span>
      <span></span>
    </button>

    <div class={`absolute top-full left-0 w-full bg-white border-b border-gray-200 p-6 md:static md:w-auto md:bg-transparent md:border-none md:p-0 transition-all duration-300 ${isNavOpen ? 'block' : 'hidden md:block'}`}>
      <div class="flex flex-col gap-6 md:flex-row md:gap-8">
        {#each navItems as item}
          <a href={item.href} class="group relative font-semibold py-2 uppercase text-sm tracking-wide transition-colors hover:text-gray-500 {$page.url.pathname === item.href ? 'text-brand' : 'text-gray-800'}" on:click={closeNav}>
            {item.label}
            <span class="absolute left-0 bottom-0 w-full h-[3px] bg-brand rounded-full transition-opacity duration-300 {$page.url.pathname === item.href ? 'opacity-100' : 'opacity-0 group-hover:opacity-100'}"></span>
          </a>
        {/each}
      </div>
    </div>
  </nav>
</header>

<main>
  <slot />
</main>

<footer class="bg-gray-50 border-t border-gray-200 px-6 pt-16 pb-8">
  <div class="grid grid-cols-1 md:grid-cols-[2fr_1fr_1fr] gap-12 max-w-6xl mx-auto mb-16 text-sm text-gray-600">
    <div class="flex flex-col gap-4">
      <img class="h-12 w-auto object-contain object-left" src="/assets/Company_logo.png" alt="ASDA Engineering logo" />
      <p class="leading-relaxed">
        Mechanical, electrical, and plumbing engineering services for Sri Lanka's commercial,
        healthcare, hospitality, institutional, and state-sector projects.
      </p>
    </div>

    <div class="flex flex-col gap-3">
      <h2 class="text-brand-dark font-bold uppercase tracking-wide text-xs mb-1">Company</h2>
      <a class="hover:text-brand transition-colors" href="/">Home</a>
      <a class="hover:text-brand transition-colors" href="/about">About</a>
      <a class="hover:text-brand transition-colors" href="/services">Services</a>
      <a class="hover:text-brand transition-colors" href="/projects">Projects</a>
      <a class="hover:text-brand transition-colors" href="/contact">Contact</a>
    </div>

    <div class="flex flex-col gap-3">
      <h2 class="text-brand-dark font-bold uppercase tracking-wide text-xs mb-1">Contact</h2>
      <p>649, Suboothi Mawatha, Battaramulla, Sri Lanka</p>
      <a class="hover:text-brand transition-colors" href="tel:+94112871891">+94 11 2871891</a>
      <a class="hover:text-brand transition-colors" href="tel:+94112074200">+94 11 2074200</a>
      <a class="hover:text-brand transition-colors" href="mailto:asdaengineeringac@gmail.com">asdaengineeringac@gmail.com</a>
    </div>
  </div>
  <div class="flex flex-col md:flex-row items-center justify-between max-w-6xl mx-auto pt-8 border-t border-gray-200 text-xs text-gray-500 gap-4">
    <span>Copyright 2026 ASDA Engineering. All rights reserved.</span>
    <span class="font-semibold">ISO 9001:2015 Certified | ICTAD EM 2 Registered</span>
  </div>
</footer>

{#if showBackToTop && !isNavOpen}
  <button class="fixed bottom-6 right-6 w-12 h-12 rounded-full bg-brand text-white border-none cursor-pointer shadow-lg z-50 flex items-center justify-center hover:bg-[#086330] focus:outline-none focus:ring-2 focus:ring-brand/50 active:scale-95 transition-all" on:click={scrollToTop} aria-label="Back to top">
    <span class="material-symbols-outlined font-semibold text-2xl">arrow_upward</span>
  </button>
{/if}


