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

<header class="site-header">

  <nav class="nav-shell" aria-label="Main navigation">
    <a class="brand" href="/" aria-label="ASDA Engineering home" on:click={closeNav}>
      <img src="/assets/Company_logo.png" alt="ASDA Engineering logo" />
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

    <div class={`nav-menu ${isNavOpen ? 'open' : ''}`}>
      <div class="nav-links">
        {#each navItems as item}
          <a href={item.href} class:active={$page.url.pathname === item.href} on:click={closeNav}>{item.label}</a>
        {/each}
      </div>
    </div>
  </nav>
</header>

<main>
  <slot />
</main>

<footer class="site-footer">
  <div class="footer-grid">
    <div>
      <img class="footer-logo" src="/assets/Company_logo.png" alt="ASDA Engineering logo" />
      <p>
        Mechanical, electrical, and plumbing engineering services for Sri Lanka's commercial,
        healthcare, hospitality, institutional, and state-sector projects.
      </p>
    </div>

    <div>
      <h2>Company</h2>
      <a href="/">Home</a>
      <a href="/about">About us</a>
      <a href="/services">Services</a>
      <a href="/projects">Projects</a>
      <a href="/contact">Contact</a>
    </div>

    <div>
      <h2>Contact</h2>
      <p>649, Suboothi Mawatha, Battaramulla, Sri Lanka</p>
      <a href="tel:+94112871891">+94 11 2871891</a>
      <a href="tel:+94112074200">+94 11 2074200</a>
      <a href="mailto:asdaengineeringac@gmail.com">asdaengineeringac@gmail.com</a>
    </div>
  </div>
  <div class="footer-bottom">
    <span>Copyright 2026 ASDA Engineering. All rights reserved.</span>
    <span>ISO 9001:2015 Certified | ICTAD EM 2 Registered</span>
  </div>
</footer>

{#if showBackToTop && !isNavOpen}
  <button class="back-to-top" on:click={scrollToTop} aria-label="Back to top">
    <svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round">
      <path d="M18 15l-6-6-6 6"/>
    </svg>
  </button>
{/if}

<style>
  .back-to-top {
    position: fixed;
    bottom: 24px;
    right: 24px;
    width: 48px;
    height: 48px;
    border-radius: 50%;
    background: var(--brand);
    color: var(--white);
    border: none;
    cursor: pointer;
    box-shadow: 0 4px 12px rgba(0,0,0,0.15);
    z-index: 90;
    display: flex;
    align-items: center;
    justify-content: center;
    transition: background 0.2s, transform 0.2s;
    -webkit-tap-highlight-color: transparent;
    outline: none;
  }
  .back-to-top:hover, .back-to-top:active, .back-to-top:focus {
    background: var(--brand);
  }
  .back-to-top:hover {
    transform: translateY(-3px);
  }
  @media (max-width: 640px) {
    .back-to-top {
      bottom: 16px;
      right: 16px;
      width: 44px;
      height: 44px;
    }
  }
</style>
