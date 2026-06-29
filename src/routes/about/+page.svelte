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

<section class="page-hero">
  <div class="section">
    <div>
      
      <h1 style="font-size: clamp(2.5rem, 5vw, 4rem); line-height: 1.1; margin-bottom: 1rem;">Trusted MEP engineering since 2002.</h1>
      <p class="lead" style="font-size: clamp(1.15rem, 2vw, 1.5rem); line-height: 1.6;">
        ASDA Engineering is a Sri Lankan mechanical, electrical, and plumbing
        engineering contractor serving state and private-sector construction
        projects with disciplined execution, trained teams, and long-term client
        focus.
      </p>
    </div>
    <img
      src="/assets/who_are_we2-qdbeiqswhdnaux9mqu7h291hy9w7jtpohpyaaaxsog.jpg.jpeg"
      alt="ASDA Engineering project team"
    />
  </div>
</section>

<section class="section mission-vision-section">
  <div class="statement left">
    <h2>Mission</h2>
    <p>
      To be the leading mechanical and electrical service provider in
      construction and related fields for both state and private-sector clients.
    </p>
  </div>
  <div class="statement right">
    <h2>Vision</h2>
    <p>
      To become a premier player in Sri Lanka's growing market as a trusted
      provider of engineering products and services.
    </p>
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
      <article class="card stat">
        <strong>2002</strong>
        <span>Established</span>
      </article>
      <article class="card stat">
        <strong>150+</strong>
        <span>Employees</span>
      </article>
      <article class="card stat">
        <strong>Rs. 900M+</strong>
        <span>Annual turnover</span>
      </article>
      <article class="card stat">
        <strong>ISO</strong>
        <span>9001:2015 certified</span>
      </article>
      <article class="card stat">
        <strong>EM 2</strong>
        <span>ICTAD registered</span>
      </article>
    </div>
  </div>
</section> -->

<section class="section">
  <div class="section-header center">
    <h1>
      Experienced direction across administration, engineering, and
      maintenance.
    </h1>
    <!-- <p>
      ASDA Engineering is led by a multidisciplinary management team supporting
      project delivery, technical coordination, operations, administration, and
      maintenance.
    </p> -->
  </div>
  <div class="team-grid">
    {#each leaders as leader}
      <article class="team-card">
        <img src={leader.image} alt={leader.name} />
        <div>
          <h3>{leader.name}</h3>
          <p>{leader.role}</p>
          {#if leader.credential}
            <p>{leader.credential}</p>
          {/if}
        </div>
      </article>
    {/each}
  </div>
</section>
<section class="section">
  <div class="section-header center">
    <div>
    
      <h1>Recognized credentials that support trusted engineering delivery.</h1>
    </div>
    <p style="font-size: clamp(1.15rem, 2vw, 1.5rem); line-height: 1.6;">
      ASDA Engineering's accreditations reinforce our commitment to professional
      standards, quality management, and dependable project execution.
    </p>
  </div>
  <div class="logo-strip accreditation-strip">
    {#each accreditations as accreditation}
      <div class="logo-tile accreditation-tile">
        <img src={accreditation} alt="ASDA Engineering accreditation logo" />
      </div>
    {/each}
  </div>
</section>
