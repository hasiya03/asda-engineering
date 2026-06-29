<script>
  import '../app.css';
  import { page } from '$app/stores';
  import { onMount } from 'svelte';
  import { siteRevealed } from '../store.js';

  let isNavOpen = false;
  let isLoading = true;
  let showLoader = true;
  let showBackToTop = false;

  onMount(() => {
    setTimeout(() => {
      isLoading = false;
      setTimeout(() => {
        showLoader = false;
        siteRevealed.set(true);
      }, 500);
    }, 2000);
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

{#if showLoader}
  <div class="site-loader" class:fade-out={!isLoading}>
    <svg viewBox="0 0 100 100" width="150" height="150" class="hvac-loader">
      <!-- Roof -->
      <path d="M 10 45 L 50 15 L 90 45" fill="none" stroke="var(--brand)" stroke-width="6" stroke-linecap="round" stroke-linejoin="round"/>
      <!-- Base & Floor -->
      <path d="M 20 45 L 20 90 M 80 45 L 80 90" fill="none" stroke="var(--brand-dark)" stroke-width="6" stroke-linecap="round"/>
      <path d="M 10 90 L 90 90" fill="none" stroke="var(--brand-dark)" stroke-width="6" stroke-linecap="round"/>
      <!-- Chimney -->
      <path d="M 70 30 L 70 12 L 82 12 L 82 39" fill="none" stroke="var(--brand-dark)" stroke-width="6" stroke-linecap="round" stroke-linejoin="round"/>
      <line x1="66" y1="12" x2="86" y2="12" stroke="var(--brand-dark)" stroke-width="6" stroke-linecap="round"/>
      <!-- Outer fan ring -->
      <circle cx="50" cy="58" r="22" fill="none" stroke="var(--brand-dark)" stroke-width="4"/>
      <!-- Spinning fan -->
      <g class="spinning-fan" style="transform-origin: 50px 58px;">
        <circle cx="50" cy="58" r="6" fill="var(--brand-dark)"/>
        <path d="M 50 58 C 65 58, 60 38, 50 38 C 45 38, 45 50, 50 58" fill="none" stroke="var(--brand-dark)" stroke-width="4"/>
        <path d="M 50 58 C 65 58, 60 38, 50 38 C 45 38, 45 50, 50 58" fill="none" stroke="var(--brand-dark)" stroke-width="4" transform="rotate(90 50 58)"/>
        <path d="M 50 58 C 65 58, 60 38, 50 38 C 45 38, 45 50, 50 58" fill="none" stroke="var(--brand-dark)" stroke-width="4" transform="rotate(180 50 58)"/>
        <path d="M 50 58 C 65 58, 60 38, 50 38 C 45 38, 45 50, 50 58" fill="none" stroke="var(--brand-dark)" stroke-width="4" transform="rotate(270 50 58)"/>
      </g>
    </svg>
    <div class="loader-bar-container">
      <div class="loader-bar"></div>
    </div>
  </div>
{/if}

<div class="site-wrapper" class:revealed={$siteRevealed}>
<header class="site-header">

  <nav class="nav-shell" aria-label="Main navigation">
    <a class="brand" href="/" aria-label="ASDA Engineering home" on:click={closeNav}>
      <img src="/assets/Company_logo.png" alt="ASDA Engineering logo" />
      <span>
        <strong>ASDA Engineering</strong>
        <small>MEP Engineers & Contractors</small>
      </span>
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

      <a class="nav-cta" href="/contact" on:click={closeNav}>Request Consultation</a>
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
      <a href="/about">About us</a>
      <a href="/services">Services</a>
      <a href="/projects">Projects</a>
    </div>

    <div>
      <h2>Contact</h2>
      <p>649, Suboothi Mawatha, Battaramulla, Sri Lanka</p>
      <a href="tel:+94112871891">+94-11-2871891</a>
      <a href="tel:+94112074200">+94-11-2074200</a>
      <a href="mailto:asdaengineeringac@gmail.com">asdaengineeringac@gmail.com</a>
    </div>
  </div>
  <div class="footer-bottom">
    <span>Copyright 2026 ASDA Engineering. All rights reserved.</span>
    <span>ISO 9001:2015 Certified | ICTAD EM 2 Registered</span>
  </div>
</footer>

{#if showBackToTop}
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
  }
  .back-to-top:hover {
    background: var(--brand-dark);
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

  .site-wrapper {
    opacity: 0;
    transform: scale(0.92);
    transition: opacity 1.2s cubic-bezier(0.2, 0.8, 0.2, 1), transform 1.2s cubic-bezier(0.2, 0.8, 0.2, 1);
  }
  .site-wrapper.revealed {
    opacity: 1;
    transform: none;
  }
</style>
</div>
