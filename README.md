<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>NexaGrow Digital — Grow Beyond Limits</title>
  <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,700;0,900;1,400&family=DM+Sans:wght@300;400;500&family=Space+Mono:wght@400;700&display=swap" rel="stylesheet"/>
  <style>
    *, *::before, *::after { margin: 0; padding: 0; box-sizing: border-box; }
    :root {
      --black: #080808; --gold: #C9A84C; --gold-light: #F0D080;
      --gold-dim: #7a6128; --white: #F5F0E8; --grey: #999;
      --card-bg: #111010; --border: rgba(201,168,76,0.2);
    }
    html { scroll-behavior: smooth; }
    body { background: var(--black); color: var(--white); font-family: 'DM Sans', sans-serif; font-weight: 300; overflow-x: hidden; cursor: none; }
    .cursor { width: 10px; height: 10px; border-radius: 50%; background: var(--gold); position: fixed; pointer-events: none; z-index: 9999; transition: transform 0.15s ease; mix-blend-mode: difference; }
    .cursor-ring { width: 36px; height: 36px; border-radius: 50%; border: 1px solid var(--gold); position: fixed; pointer-events: none; z-index: 9998; transition: all 0.25s ease; opacity: 0.6; }
    body::before { content: ''; position: fixed; inset: 0; background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 200 200' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='0.03'/%3E%3C/svg%3E"); pointer-events: none; z-index: 100; opacity: 0.4; }

    /* NAV */
    nav { position: fixed; top: 0; left: 0; right: 0; z-index: 500; display: flex; align-items: center; justify-content: space-between; padding: 1.6rem 5vw; background: linear-gradient(to bottom, rgba(8,8,8,0.96), transparent); backdrop-filter: blur(2px); }
    .logo { font-family: 'Playfair Display', serif; font-size: 1.5rem; font-weight: 900; letter-spacing: -0.02em; }
    .logo span { color: var(--gold); }
    .nav-links { display: flex; gap: 2.5rem; list-style: none; }
    .nav-links a { font-family: 'Space Mono', monospace; font-size: 0.72rem; letter-spacing: 0.12em; text-transform: uppercase; color: var(--grey); text-decoration: none; transition: color 0.3s; }
    .nav-links a:hover { color: var(--gold); }
    .nav-cta { font-family: 'Space Mono', monospace; font-size: 0.72rem; letter-spacing: 0.1em; text-transform: uppercase; color: var(--black); background: var(--gold); padding: 0.65rem 1.4rem; border: none; cursor: none; text-decoration: none; transition: background 0.3s, transform 0.2s; }
    .nav-cta:hover { background: var(--gold-light); transform: translateY(-1px); }

    /* HERO */
    #hero { min-height: 100vh; display: flex; flex-direction: column; justify-content: center; padding: 10rem 5vw 6rem; position: relative; overflow: hidden; }
    .hero-bg-line { position: absolute; top: 0; right: 10vw; bottom: 0; width: 1px; background: linear-gradient(to bottom, transparent, var(--border), transparent); }
    .hero-bg-line:nth-child(2) { right: 35vw; opacity: 0.35; }
    .hero-bg-line:nth-child(3) { right: 65vw; opacity: 0.15; }
    .hero-badge { display: inline-flex; align-items: center; gap: 0.6rem; border: 1px solid var(--border); padding: 0.45rem 1rem; margin-bottom: 2.2rem; width: fit-content; opacity: 0; animation: fadeUp 0.9s 0.2s forwards; }
    .badge-dot { width: 7px; height: 7px; border-radius: 50%; background: var(--gold); animation: pulse 2s infinite; }
    @keyframes pulse { 0%,100%{opacity:1;transform:scale(1)} 50%{opacity:0.5;transform:scale(0.8)} }
    .badge-text { font-family: 'Space Mono', monospace; font-size: 0.68rem; letter-spacing: 0.2em; text-transform: uppercase; color: var(--gold); }
    .hero-title { font-family: 'Playfair Display', serif; font-size: clamp(3.2rem, 8.5vw, 7.5rem); font-weight: 900; line-height: 0.95; letter-spacing: -0.03em; max-width: 860px; opacity: 0; animation: fadeUp 1s 0.4s forwards; }
    .hero-title em { font-style: italic; color: var(--gold); position: relative; }
    .hero-title em::after { content: ''; position: absolute; left: 0; bottom: -4px; right: 0; height: 2px; background: var(--gold); transform: scaleX(0); transform-origin: left; animation: lineGrow 0.8s 1.4s forwards; }
    @keyframes lineGrow { to { transform: scaleX(1); } }
    .hero-sub { margin-top: 2.5rem; max-width: 520px; font-size: 1.05rem; line-height: 1.8; color: var(--grey); opacity: 0; animation: fadeUp 1s 0.6s forwards; }
    .hero-actions { margin-top: 3rem; display: flex; gap: 1.2rem; align-items: center; opacity: 0; animation: fadeUp 1s 0.8s forwards; }
    .btn-primary { font-family: 'Space Mono', monospace; font-size: 0.75rem; letter-spacing: 0.1em; text-transform: uppercase; color: var(--black); background: var(--gold); padding: 1rem 2.2rem; text-decoration: none; border: none; cursor: none; transition: all 0.3s; position: relative; overflow: hidden; }
    .btn-primary::before { content: ''; position: absolute; inset: 0; background: var(--gold-light); transform: translateX(-100%); transition: transform 0.3s ease; }
    .btn-primary:hover::before { transform: translateX(0); }
    .btn-primary span { position: relative; z-index: 1; }
    .btn-outline { font-family: 'Space Mono', monospace; font-size: 0.75rem; letter-spacing: 0.1em; text-transform: uppercase; color: var(--white); padding: 1rem 2.2rem; border: 1px solid var(--border); text-decoration: none; transition: all 0.3s; cursor: none; }
    .btn-outline:hover { border-color: var(--gold); color: var(--gold); }
    .promise-strip { opacity: 0; animation: fadeUp 1s 1s forwards; margin-top: 4rem; display: flex; gap: 2.5rem; flex-wrap: wrap; }
    .promise-item { display: flex; align-items: center; gap: 0.7rem; }
    .promise-icon { color: var(--gold); font-size: 0.9rem; }
    .promise-text { font-family: 'Space Mono', monospace; font-size: 0.65rem; letter-spacing: 0.1em; text-transform: uppercase; color: var(--grey); }
    @keyframes fadeUp { from{opacity:0;transform:translateY(30px)} to{opacity:1;transform:translateY(0)} }

    /* MARQUEE */
    .marquee-section { padding: 1.5rem 0; border-top: 1px solid var(--border); border-bottom: 1px solid var(--border); overflow: hidden; background: rgba(201,168,76,0.03); }
    .marquee-track { display: flex; gap: 4rem; animation: marquee 22s linear infinite; white-space: nowrap; }
    .marquee-item { font-family: 'Space Mono', monospace; font-size: 0.7rem; letter-spacing: 0.2em; text-transform: uppercase; color: var(--gold-dim); display: flex; align-items: center; gap: 1.5rem; flex-shrink: 0; }
    .marquee-dot { width: 4px; height: 4px; background: var(--gold); border-radius: 50%; flex-shrink: 0; }
    @keyframes marquee { from{transform:translateX(0)} to{transform:translateX(-50%)} }

    /* SECTIONS */
    section { padding: 7rem 5vw; }
    .section-label { font-family: 'Space Mono', monospace; font-size: 0.68rem; letter-spacing: 0.25em; text-transform: uppercase; color: var(--gold); margin-bottom: 1.2rem; }
    .section-title { font-family: 'Playfair Display', serif; font-size: clamp(2rem, 4.5vw, 3.6rem); font-weight: 700; line-height: 1.1; letter-spacing: -0.02em; max-width: 640px; }
    .section-title em { font-style: italic; color: var(--gold); }

    /* HONEST INTRO */
    #intro { display: grid; grid-template-columns: 1fr 1fr; gap: 6rem; align-items: center; }
    .intro-text p { font-size: 0.95rem; line-height: 1.85; color: var(--grey); margin-top: 1.8rem; }
    .intro-text p+p { margin-top: 1rem; }
    .intro-text strong { color: var(--white); font-weight: 500; }
    .intro-card { background: var(--card-bg); border: 1px solid var(--border); padding: 3rem; }
    .intro-card-label { font-family: 'Space Mono', monospace; font-size: 0.65rem; letter-spacing: 0.18em; text-transform: uppercase; color: var(--gold); margin-bottom: 1.5rem; }
    .commitment-list { list-style: none; display: flex; flex-direction: column; gap: 1.2rem; }
    .commitment-item { display: flex; align-items: flex-start; gap: 1rem; padding-bottom: 1.2rem; border-bottom: 1px solid var(--border); }
    .commitment-item:last-child { border-bottom: none; padding-bottom: 0; }
    .c-check { width: 20px; height: 20px; flex-shrink: 0; border: 1px solid var(--gold); display: flex; align-items: center; justify-content: center; color: var(--gold); font-size: 0.65rem; margin-top: 2px; }
    .c-text { font-size: 0.9rem; line-height: 1.65; color: var(--grey); }
    .c-text strong { color: var(--white); font-weight: 500; }

    /* SERVICES */
    #services { background: #0c0b0b; }
    .services-grid { margin-top: 4rem; display: grid; grid-template-columns: repeat(auto-fill, minmax(300px, 1fr)); gap: 1px; background: var(--border); border: 1px solid var(--border); }
    .service-card { background: var(--card-bg); padding: 2.8rem 2.5rem; transition: background 0.3s; position: relative; overflow: hidden; }
    .service-card::before { content: ''; position: absolute; top: 0; left: 0; right: 0; height: 2px; background: var(--gold); transform: scaleX(0); transform-origin: left; transition: transform 0.4s ease; }
    .service-card:hover { background: #161414; }
    .service-card:hover::before { transform: scaleX(1); }
    .service-num { font-family: 'Space Mono', monospace; font-size: 0.65rem; letter-spacing: 0.15em; color: var(--gold-dim); margin-bottom: 1.5rem; }
    .service-icon { font-size: 2rem; margin-bottom: 1.2rem; display: block; }
    .service-card h3 { font-family: 'Playfair Display', serif; font-size: 1.4rem; font-weight: 700; margin-bottom: 1rem; }
    .service-card p { font-size: 0.9rem; line-height: 1.75; color: var(--grey); }
    .service-arrow { margin-top: 2rem; font-family: 'Space Mono', monospace; font-size: 0.68rem; letter-spacing: 0.12em; text-transform: uppercase; color: var(--gold); opacity: 0; transform: translateX(-8px); transition: all 0.3s; }
    .service-card:hover .service-arrow { opacity: 1; transform: translateX(0); }

    /* OFFER */
    #offer { }
    .offer-grid { margin-top: 4rem; display: grid; grid-template-columns: repeat(3, 1fr); gap: 1.5rem; }
    .offer-card { border: 1px solid var(--border); padding: 2.5rem 2rem; transition: border-color 0.3s, transform 0.3s; }
    .offer-card:hover { border-color: var(--gold); transform: translateY(-4px); }
    .offer-num { font-family: 'Playfair Display', serif; font-size: 3rem; font-weight: 900; color: rgba(201,168,76,0.12); line-height: 1; margin-bottom: 1.2rem; }
    .offer-card h3 { font-family: 'Playfair Display', serif; font-size: 1.2rem; font-weight: 700; margin-bottom: 0.8rem; }
    .offer-card p { font-size: 0.88rem; line-height: 1.75; color: var(--grey); }

    /* PROCESS */
    #process { background: #0c0b0b; }
    .process-steps { margin-top: 4rem; display: grid; grid-template-columns: repeat(4, 1fr); border: 1px solid var(--border); }
    .process-step { padding: 2.8rem 2rem; border-right: 1px solid var(--border); position: relative; }
    .process-step:last-child { border-right: none; }
    .process-step::after { content: '→'; position: absolute; top: 2.8rem; right: -0.7rem; color: var(--gold); font-size: 1.2rem; z-index: 1; }
    .process-step:last-child::after { display: none; }
    .step-num { font-family: 'Playfair Display', serif; font-size: 3rem; font-weight: 900; color: rgba(201,168,76,0.13); line-height: 1; margin-bottom: 1.2rem; }
    .process-step h3 { font-family: 'Playfair Display', serif; font-size: 1.15rem; font-weight: 700; margin-bottom: 0.8rem; }
    .process-step p { font-size: 0.87rem; color: var(--grey); line-height: 1.7; }

    /* FREE AUDIT CTA */
    #audit { background: var(--gold); padding: 5rem 5vw; display: flex; align-items: center; justify-content: space-between; gap: 3rem; flex-wrap: wrap; }
    .audit-text h2 { font-family: 'Playfair Display', serif; font-size: clamp(1.8rem, 4vw, 3rem); font-weight: 900; color: var(--black); line-height: 1.1; }
    .audit-text p { font-size: 0.95rem; color: rgba(0,0,0,0.6); margin-top: 0.8rem; max-width: 480px; line-height: 1.7; }
    .btn-dark { font-family: 'Space Mono', monospace; font-size: 0.78rem; letter-spacing: 0.1em; text-transform: uppercase; color: var(--white); background: var(--black); padding: 1.1rem 2.5rem; text-decoration: none; border: none; cursor: none; flex-shrink: 0; transition: background 0.3s; }
    .btn-dark:hover { background: #1a1a1a; }

    /* CONTACT */
    #contact { }
    .contact-grid { margin-top: 4rem; display: grid; grid-template-columns: 1fr 1.4fr; gap: 5rem; align-items: start; }
    .contact-info h3 { font-family: 'Playfair Display', serif; font-size: 1.5rem; font-weight: 700; margin-bottom: 1.2rem; line-height: 1.3; }
    .contact-info p { font-size: 0.92rem; line-height: 1.85; color: var(--grey); margin-bottom: 2.5rem; }
    .contact-detail { display: flex; align-items: center; gap: 1rem; margin-bottom: 1.2rem; }
    .contact-detail-icon { width: 38px; height: 38px; flex-shrink: 0; border: 1px solid var(--border); display: flex; align-items: center; justify-content: center; font-size: 1rem; }
    .contact-detail-label { font-family: 'Space Mono', monospace; font-size: 0.62rem; color: var(--gold); letter-spacing: 0.15em; text-transform: uppercase; margin-bottom: 0.2rem; }
    .contact-detail-text { font-family: 'Space Mono', monospace; font-size: 0.75rem; letter-spacing: 0.08em; }
    .contact-form { display: flex; flex-direction: column; gap: 1.2rem; }
    .form-row { display: grid; grid-template-columns: 1fr 1fr; gap: 1.2rem; }
    .form-group { display: flex; flex-direction: column; gap: 0.5rem; }
    .form-group label { font-family: 'Space Mono', monospace; font-size: 0.65rem; letter-spacing: 0.15em; text-transform: uppercase; color: var(--gold); }
    .form-group input, .form-group textarea, .form-group select { background: rgba(255,255,255,0.04); border: 1px solid var(--border); color: var(--white); font-family: 'DM Sans', sans-serif; font-size: 0.9rem; padding: 0.9rem 1.1rem; outline: none; transition: border-color 0.3s; appearance: none; }
    .form-group input:focus, .form-group textarea:focus, .form-group select:focus { border-color: var(--gold); background: rgba(201,168,76,0.05); }
    .form-group textarea { resize: vertical; min-height: 120px; }
    .form-group select option { background: #111; color: var(--white); }
    .form-submit { font-family: 'Space Mono', monospace; font-size: 0.75rem; letter-spacing: 0.1em; text-transform: uppercase; color: var(--black); background: var(--gold); padding: 1.1rem 2.5rem; border: none; cursor: none; transition: all 0.3s; align-self: flex-start; position: relative; overflow: hidden; }
    .form-submit::before { content: ''; position: absolute; inset: 0; background: var(--gold-light); transform: translateX(-100%); transition: transform 0.3s; }
    .form-submit:hover::before { transform: translateX(0); }
    .form-submit span { position: relative; z-index: 1; }
    .success-msg { display: none; font-family: 'Space Mono', monospace; font-size: 0.75rem; letter-spacing: 0.1em; text-transform: uppercase; color: var(--gold); padding: 1rem; border: 1px solid var(--gold); background: rgba(201,168,76,0.06); margin-top: 0.5rem; }

    /* FOOTER */
    footer { padding: 3rem 5vw; border-top: 1px solid var(--border); display: flex; align-items: center; justify-content: space-between; flex-wrap: wrap; gap: 1.5rem; }
    .footer-logo { font-family: 'Playfair Display', serif; font-size: 1.3rem; font-weight: 900; }
    .footer-logo span { color: var(--gold); }
    .footer-copy { font-family: 'Space Mono', monospace; font-size: 0.62rem; letter-spacing: 0.12em; text-transform: uppercase; color: var(--grey); }
    .footer-socials { display: flex; gap: 1rem; }
    .social-link { width: 36px; height: 36px; border: 1px solid var(--border); display: flex; align-items: center; justify-content: center; color: var(--grey); text-decoration: none; font-size: 0.85rem; transition: all 0.3s; cursor: none; }
    .social-link:hover { border-color: var(--gold); color: var(--gold); }

    /* ANIMATIONS */
    .reveal { opacity: 0; transform: translateY(35px); transition: opacity 0.7s ease, transform 0.7s ease; }
    .reveal.visible { opacity: 1; transform: translateY(0); }
    .reveal-delay-1 { transition-delay: 0.1s; }
    .reveal-delay-2 { transition-delay: 0.2s; }
    .reveal-delay-3 { transition-delay: 0.3s; }
    .reveal-delay-4 { transition-delay: 0.4s; }

    /* RESPONSIVE */
    @media (max-width: 900px) {
      #intro { grid-template-columns: 1fr; }
      .offer-grid { grid-template-columns: 1fr 1fr; }
      .process-steps { grid-template-columns: 1fr 1fr; }
      .contact-grid { grid-template-columns: 1fr; gap: 3rem; }
      .form-row { grid-template-columns: 1fr; }
    }
    @media (max-width: 600px) {
      .nav-links { display: none; }
      .process-steps { grid-template-columns: 1fr; }
      .services-grid { grid-template-columns: 1fr; }
      .offer-grid { grid-template-columns: 1fr; }
      .promise-strip { gap: 1.2rem; }
    }
  </style>
</head>
<body>
  <div class="cursor" id="cursor"></div>
  <div class="cursor-ring" id="cursorRing"></div>

  <!-- NAV -->
  <nav>
    <div class="logo">Nexa<span>Grow</span></div>
    <ul class="nav-links">
      <li><a href="#services">Services</a></li>
      <li><a href="#offer">What You Get</a></li>
      <li><a href="#process">Process</a></li>
      <li><a href="#contact">Contact</a></li>
    </ul>
    <a href="#contact" class="nav-cta">Get in Touch</a>
  </nav>

  <!-- HERO -->
  <section id="hero">
    <div class="hero-bg-line"></div>
    <div class="hero-bg-line"></div>
    <div class="hero-bg-line"></div>
    <div class="hero-badge"><span class="badge-dot"></span><span class="badge-text">Now Open — Taking New Clients</span></div>
    <h1 class="hero-title">Your Business,<br/><em>Digitally Grown</em></h1>
    <p class="hero-sub">NexaGrow is a fresh digital marketing studio based in Lucknow. We help small businesses and creators build a genuine online presence — no shortcuts, no inflated promises.</p>
    <div class="hero-actions">
      <a href="#contact" class="btn-primary"><span>Book a Free Call →</span></a>
      <a href="#services" class="btn-outline">See Services</a>
    </div>
    <div class="promise-strip">
      <div class="promise-item"><span class="promise-icon">✦</span><span class="promise-text">No fake metrics</span></div>
      <div class="promise-item"><span class="promise-icon">✦</span><span class="promise-text">No hidden fees</span></div>
      <div class="promise-item"><span class="promise-icon">✦</span><span class="promise-text">Real strategy, real work</span></div>
      <div class="promise-item"><span class="promise-icon">✦</span><span class="promise-text">Free first consultation</span></div>
    </div>
  </section>

  <!-- MARQUEE -->
  <div class="marquee-section">
    <div class="marquee-track">
      <span class="marquee-item"><span class="marquee-dot"></span>Social Media Marketing</span>
      <span class="marquee-item"><span class="marquee-dot"></span>SEO Optimization</span>
      <span class="marquee-item"><span class="marquee-dot"></span>Paid Advertising</span>
      <span class="marquee-item"><span class="marquee-dot"></span>Content Strategy</span>
      <span class="marquee-item"><span class="marquee-dot"></span>Brand Identity</span>
      <span class="marquee-item"><span class="marquee-dot"></span>Email Campaigns</span>
      <span class="marquee-item"><span class="marquee-dot"></span>Reels &amp; Short-Form Video</span>
      <span class="marquee-item"><span class="marquee-dot"></span>Analytics &amp; Reporting</span>
      <span class="marquee-item"><span class="marquee-dot"></span>Social Media Marketing</span>
      <span class="marquee-item"><span class="marquee-dot"></span>SEO Optimization</span>
      <span class="marquee-item"><span class="marquee-dot"></span>Paid Advertising</span>
      <span class="marquee-item"><span class="marquee-dot"></span>Content Strategy</span>
      <span class="marquee-item"><span class="marquee-dot"></span>Brand Identity</span>
      <span class="marquee-item"><span class="marquee-dot"></span>Email Campaigns</span>
      <span class="marquee-item"><span class="marquee-dot"></span>Reels &amp; Short-Form Video</span>
      <span class="marquee-item"><span class="marquee-dot"></span>Analytics &amp; Reporting</span>
    </div>
  </div>

  <!-- HONEST INTRO -->
  <section id="intro">
    <div class="intro-text">
      <p class="section-label reveal">Our Promise</p>
      <h2 class="section-title reveal">Built on <em>Honesty.</em><br/>Proven by Work.</h2>
      <p class="reveal reveal-delay-1">We're a <strong>new studio</strong> — and we're proud of it. We don't have a wall of client logos yet, and we won't invent ones. What we do have is <strong>deep knowledge, real skills, and the hunger to prove ourselves</strong> through exceptional work.</p>
      <p class="reveal reveal-delay-2">Every strategy we build is custom. Every rupee you spend is tracked. Every report you receive will show you <strong>exactly what's working and what isn't</strong> — no fluff, no vanity numbers.</p>
      <p class="reveal reveal-delay-3">Being new also means <strong>you get our full, undivided attention</strong>. You won't be account number 847. You'll be a founding client we work tirelessly to make successful.</p>
    </div>
    <div class="intro-card reveal reveal-delay-2">
      <div class="intro-card-label">✦ Our Commitments to You</div>
      <ul class="commitment-list">
        <li class="commitment-item"><div class="c-check">✓</div><div class="c-text"><strong>Zero inflated promises.</strong> We'll tell you what's realistically achievable in your timeline and budget — not what sounds exciting.</div></li>
        <li class="commitment-item"><div class="c-check">✓</div><div class="c-text"><strong>Monthly transparent reports.</strong> You'll see every metric, every rupee spent, and every result — good or bad.</div></li>
        <li class="commitment-item"><div class="c-check">✓</div><div class="c-text"><strong>No lock-in contracts.</strong> Stay because the work delivers, not because a contract forces you to.</div></li>
        <li class="commitment-item"><div class="c-check">✓</div><div class="c-text"><strong>Founding client rates.</strong> Our first clients get lower pricing — and that rate is locked in for life as we grow.</div></li>
        <li class="commitment-item"><div class="c-check">✓</div><div class="c-text"><strong>Free digital audit.</strong> Before you pay us anything, we'll analyse your current online presence and show you exactly where the gaps are.</div></li>
      </ul>
    </div>
  </section>

  <!-- SERVICES -->
  <section id="services">
    <p class="section-label reveal">What We Do</p>
    <h2 class="section-title reveal">Services Built for<br/><em>Real Growth</em></h2>
    <div class="services-grid">
      <div class="service-card reveal reveal-delay-1">
        <div class="service-num">01</div><span class="service-icon">📱</span>
        <h3>Social Media Marketing</h3>
        <p>Strategy, content calendars, captions, and consistent posting across Instagram, Facebook, and LinkedIn — content that actually connects with your audience.</p>
        <div class="service-arrow">Learn More →</div>
      </div>
      <div class="service-card reveal reveal-delay-2">
        <div class="service-num">02</div><span class="service-icon">🔍</span>
        <h3>SEO &amp; Content</h3>
        <p>Keyword research, on-page optimization, blog writing, and backlink strategies to help your business get found on Google organically over time.</p>
        <div class="service-arrow">Learn More →</div>
      </div>
      <div class="service-card reveal reveal-delay-3">
        <div class="service-num">03</div><span class="service-icon">🎯</span>
        <h3>Paid Advertising</h3>
        <p>Meta and Google Ads set up and managed carefully. We start small, test thoroughly, and scale only what the data confirms is working.</p>
        <div class="service-arrow">Learn More →</div>
      </div>
      <div class="service-card reveal reveal-delay-1">
        <div class="service-num">04</div><span class="service-icon">🎬</span>
        <h3>Reels &amp; Short-Form Video</h3>
        <p>Scripts, hooks, and editing direction for Instagram Reels and YouTube Shorts — currently the highest-reach format for any growing business.</p>
        <div class="service-arrow">Learn More →</div>
      </div>
      <div class="service-card reveal reveal-delay-2">
        <div class="service-num">05</div><span class="service-icon">🎨</span>
        <h3>Brand Identity</h3>
        <p>Logo, color palette, typography, and brand voice guidelines. Look consistent, credible, and memorable everywhere you show up online.</p>
        <div class="service-arrow">Learn More →</div>
      </div>
      <div class="service-card reveal reveal-delay-3">
        <div class="service-num">06</div><span class="service-icon">📊</span>
        <h3>Analytics &amp; Reporting</h3>
        <p>Monthly performance reports that clearly explain what's working and what needs adjustment — in plain language you can actually act on.</p>
        <div class="service-arrow">Learn More →</div>
      </div>
    </div>
  </section>

  <!-- WHAT YOU GET -->
  <section id="offer">
    <p class="section-label reveal">The Offer</p>
    <h2 class="section-title reveal">What Every Client<br/><em>Gets From Day One</em></h2>
    <div class="offer-grid">
      <div class="offer-card reveal reveal-delay-1"><div class="offer-num">01</div><h3>Free Digital Audit</h3><p>Before any payment, we analyse your website, social media, and SEO to identify exactly where you're losing visibility and potential customers.</p></div>
      <div class="offer-card reveal reveal-delay-2"><div class="offer-num">02</div><h3>Custom 90-Day Roadmap</h3><p>A clear, realistic plan tailored to your business — with specific actions, timelines, and measurable goals. No generic templates or copy-paste strategies.</p></div>
      <div class="offer-card reveal reveal-delay-3"><div class="offer-num">03</div><h3>Direct Access to Us</h3><p>You'll work directly with us — not handed off to an intern. Your questions get answered the same day. You always know who's doing the work.</p></div>
      <div class="offer-card reveal reveal-delay-1"><div class="offer-num">04</div><h3>Monthly Performance Reports</h3><p>Every month, a clear report showing growth metrics, ad spend breakdown, and concrete recommendations for the next 30 days.</p></div>
      <div class="offer-card reveal reveal-delay-2"><div class="offer-num">05</div><h3>No Long-Term Lock-In</h3><p>Month-to-month engagement only. You're free to pause or stop at any time. We believe in earning your continued trust every single month.</p></div>
      <div class="offer-card reveal reveal-delay-3"><div class="offer-num">06</div><h3>Founding Client Pricing</h3><p>Our first clients get our lowest-ever rates — locked in permanently as our pricing rises with our growing experience and demand.</p></div>
    </div>
  </section>

  <!-- PROCESS -->
  <section id="process">
    <p class="section-label reveal">How It Works</p>
    <h2 class="section-title reveal">Simple Steps to<br/><em>Getting Started</em></h2>
    <div class="process-steps">
      <div class="process-step reveal reveal-delay-1"><div class="step-num">01</div><h3>Free Discovery Call</h3><p>We learn about your business, your audience, and your goals. No sales pressure — just an honest conversation about what's possible.</p></div>
      <div class="process-step reveal reveal-delay-2"><div class="step-num">02</div><h3>Free Digital Audit</h3><p>We review your current online presence and deliver a clear report of gaps and opportunities — entirely free, with zero obligation to continue.</p></div>
      <div class="process-step reveal reveal-delay-3"><div class="step-num">03</div><h3>Custom Strategy</h3><p>If you choose to work with us, we build a 90-day plan with clear milestones, budgets, and realistic expected outcomes.</p></div>
      <div class="process-step reveal reveal-delay-4"><div class="step-num">04</div><h3>Execute &amp; Report</h3><p>We get to work. You receive weekly updates and a full monthly report. Transparent communication, always.</p></div>
    </div>
  </section>

  <!-- FREE AUDIT CTA -->
  <section id="audit">
    <div class="audit-text reveal">
      <h2>Get Your Free Digital Audit — No Strings Attached</h2>
      <p>We'll review your Instagram, website, and Google presence and send you a personalised report within 48 hours. Zero cost. Zero obligation. Just honest insight.</p>
    </div>
    <a href="#contact" class="btn-dark reveal reveal-delay-2">Claim Free Audit →</a>
  </section>

  <!-- CONTACT -->
  <section id="contact">
    <p class="section-label reveal">Let's Talk</p>
    <h2 class="section-title reveal">Drop Us a Message.<br/>We'll Reply in <em>24 Hours.</em></h2>
    <div class="contact-grid">
      <div class="contact-info reveal">
        <h3>Tell us about your business and we'll give you an honest picture of what digital marketing can do for it.</h3>
        <p>Whether you have a budget of ₹5,000 or ₹50,000, we'll tell you clearly what's achievable and what the smartest first step looks like for you.</p>
        <div class="contact-detail"><div class="contact-detail-icon">📧</div><div><div class="contact-detail-label">Email</div><div class="contact-detail-text">ashutoshupadhyay1233@gmail.com</div></div></div>
        <div class="contact-detail"><div class="contact-detail-icon">📱</div><div><div class="contact-detail-label">WhatsApp</div><div class="contact-detail-text">+91 89579 49173</div></div></div>
        <div class="contact-detail"><div class="contact-detail-icon">📍</div><div><div class="contact-detail-label">Location</div><div class="contact-detail-text">Lucknow, Uttar Pradesh</div></div></div>
        <div class="contact-detail"><div class="contact-detail-icon">🕐</div><div><div class="contact-detail-label">Response Time</div><div class="contact-detail-text">Within 24 hours</div></div></div>
      </div>
      <div class="reveal reveal-delay-2">
        <form class="contact-form" id="contactForm" onsubmit="handleSubmit(event)">
          <div class="form-row">
            <div class="form-group"><label>Your Name</label><input type="text" placeholder="e.g. Rahul Gupta" required /></div>
            <div class="form-group"><label>Email Address</label><input type="email" placeholder="you@example.com" required /></div>
          </div>
          <div class="form-row">
            <div class="form-group"><label>WhatsApp Number</label><input type="tel" placeholder="+91 XXXXX XXXXX" /></div>
            <div class="form-group"><label>Type of Business</label>
              <select><option value="">Select category...</option><option>E-commerce / Online Shop</option><option>Food &amp; Restaurant</option><option>Fashion &amp; Lifestyle</option><option>Health &amp; Wellness</option><option>Education / Coaching</option><option>Content Creator / Influencer</option><option>Local Service Business</option><option>Other</option></select>
            </div>
          </div>
          <div class="form-group"><label>What Are You Looking For?</label>
            <select><option value="">Select a service...</option><option>Free Digital Audit (No cost)</option><option>Social Media Marketing</option><option>SEO &amp; Content</option><option>Paid Advertising</option><option>Reels &amp; Short-Form Video</option><option>Brand Identity</option><option>Full Digital Package</option><option>Not Sure — Need Guidance</option></select>
          </div>
          <div class="form-group"><label>Tell Us About Your Business &amp; Goals</label><textarea placeholder="What does your business do? What are you hoping to achieve digitally? Any budget in mind? The more detail, the better we can help."></textarea></div>
          <button type="submit" class="form-submit"><span>Send Message →</span></button>
          <div class="success-msg" id="successMsg">✦ Message received! We'll be in touch within 24 hours.</div>
        </form>
      </div>
    </div>
  </section>

  <!-- FOOTER -->
  <footer>
    <div class="footer-logo">Nexa<span>Grow</span> Digital</div>
    <div class="footer-copy">© 2025 NexaGrow Digital · Lucknow, India</div>
    <div class="footer-socials">
      <a href="#" class="social-link" title="LinkedIn">in</a>
      <a href="#" class="social-link" title="Instagram">ig</a>
      <a href="#" class="social-link" title="WhatsApp">wa</a>
    </div>
  </footer>

  <script>
    const cursor = document.getElementById('cursor');
    const ring = document.getElementById('cursorRing');
    let mx=0,my=0,rx=0,ry=0;
    document.addEventListener('mousemove',e=>{mx=e.clientX;my=e.clientY;cursor.style.left=mx-5+'px';cursor.style.top=my-5+'px';});
    (function animate(){rx+=(mx-rx-18)*0.12;ry+=(my-ry-18)*0.12;ring.style.left=rx+'px';ring.style.top=ry+'px';requestAnimationFrame(animate);})();
    document.querySelectorAll('a,button,.service-card,.offer-card').forEach(el=>{
      el.addEventListener('mouseenter',()=>{cursor.style.transform='scale(2)';ring.style.transform='scale(1.5)';});
      el.addEventListener('mouseleave',()=>{cursor.style.transform='scale(1)';ring.style.transform='scale(1)';});
    });
    const reveals=document.querySelectorAll('.reveal');
    const obs=new IntersectionObserver(entries=>entries.forEach(e=>{if(e.isIntersecting)e.target.classList.add('visible');}),{threshold:0.1});
    reveals.forEach(el=>obs.observe(el));
    function handleSubmit(e){
      e.preventDefault();
      const btn=e.target.querySelector('.form-submit');
      btn.innerHTML='<span>Sending…</span>';btn.disabled=true;
      setTimeout(()=>{document.getElementById('successMsg').style.display='block';btn.style.display='none';e.target.reset();},1200);
    }
  </script>
</body>
</html>
