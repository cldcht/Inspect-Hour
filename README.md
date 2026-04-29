[index.html](https://github.com/user-attachments/files/27215214/index.html)
<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>INSPECT Hour — Le magazine de la montre</title>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;0,600;0,700;1,300;1,400&family=DM+Sans:wght@300;400;500&display=swap" rel="stylesheet">
  <style>
    /* ── Reset & Variables ──────────────────────────── */
    *, *::before, *::after { margin: 0; padding: 0; box-sizing: border-box; }

    :root {
      --coral:      #E8673A;
      --coral-mid:  rgba(232,103,58,0.18);
      --coral-soft: rgba(232,103,58,0.08);
      --black:      #0D0D0D;
      --dark:       #1A1A1A;
      --mid:        #4A4A4A;
      --light:      #9A9A9A;
      --rule:       #E2E0DB;
      --bg:         #FFFFFF;
      --bg-warm:    #F8F7F5;
      --serif:      'Cormorant Garamond', Georgia, serif;
      --sans:       'DM Sans', Helvetica, sans-serif;
    }

    html { scroll-behavior: smooth; }

    body {
      background: var(--bg);
      color: var(--black);
      font-family: var(--sans);
      font-weight: 300;
      line-height: 1.6;
      overflow-x: hidden;
    }

    a { color: inherit; text-decoration: none; }
    img { display: block; width: 100%; }

    /* ── Coral top accent line ───────────────────────── */
    .accent-line {
      position: fixed;
      top: 0; left: 0; right: 0;
      height: 3px;
      background: var(--coral);
      z-index: 1000;
    }

    /* ── Header / Navigation ─────────────────────────── */
    header {
      position: fixed;
      top: 3px; left: 0; right: 0;
      height: 72px;
      background: rgba(255,255,255,0.97);
      backdrop-filter: blur(12px);
      border-bottom: 1px solid var(--rule);
      z-index: 999;
      display: flex;
      align-items: center;
      justify-content: space-between;
      padding: 0 48px;
    }

    .logo {
      font-family: var(--serif);
      font-size: 22px;
      font-weight: 700;
      letter-spacing: 4px;
      color: var(--black);
      text-transform: uppercase;
    }

    .logo span { color: var(--coral); }

    nav { display: flex; align-items: center; gap: 40px; }

    nav a {
      font-size: 10px;
      font-weight: 500;
      letter-spacing: 2.5px;
      text-transform: uppercase;
      color: var(--mid);
      transition: color 0.2s;
      position: relative;
    }

    nav a::after {
      content: '';
      position: absolute;
      bottom: -3px; left: 0; right: 0;
      height: 1px;
      background: var(--coral);
      transform: scaleX(0);
      transition: transform 0.25s ease;
    }

    nav a:hover { color: var(--black); }
    nav a:hover::after { transform: scaleX(1); }

    .nav-cta {
      font-size: 9px;
      font-weight: 500;
      letter-spacing: 2px;
      text-transform: uppercase;
      color: var(--bg) !important;
      background: var(--black);
      padding: 10px 20px;
      transition: background 0.2s !important;
    }

    .nav-cta::after { display: none !important; }
    .nav-cta:hover { background: var(--coral) !important; color: var(--bg) !important; }

    /* Hamburger */
    .hamburger {
      display: none;
      flex-direction: column;
      gap: 5px;
      cursor: pointer;
      padding: 4px;
    }

    .hamburger span {
      display: block;
      width: 24px;
      height: 1.5px;
      background: var(--black);
      transition: all 0.3s;
    }

    /* Mobile nav */
    .mobile-nav {
      display: none;
      position: fixed;
      top: 75px; left: 0; right: 0;
      background: var(--bg);
      border-bottom: 1px solid var(--rule);
      padding: 24px 48px;
      z-index: 998;
      flex-direction: column;
      gap: 20px;
    }

    .mobile-nav.open { display: flex; }
    .mobile-nav a {
      font-size: 11px;
      font-weight: 500;
      letter-spacing: 2px;
      text-transform: uppercase;
      color: var(--mid);
      padding: 8px 0;
      border-bottom: 1px solid var(--rule);
    }

    /* ── Main content offset ─────────────────────────── */
    main { padding-top: 75px; }

    /* ── Hero Section ─────────────────────────────────── */
    .hero {
      display: grid;
      grid-template-columns: 1fr 1fr;
      min-height: calc(100vh - 75px);
    }

    .hero-left {
      display: flex;
      flex-direction: column;
      justify-content: center;
      padding: 80px 64px 80px 48px;
    }

    .hero-eyebrow {
      font-size: 9px;
      font-weight: 500;
      letter-spacing: 3px;
      text-transform: uppercase;
      color: var(--coral);
      margin-bottom: 24px;
    }

    .hero-title {
      font-family: var(--serif);
      font-size: clamp(52px, 6vw, 88px);
      font-weight: 300;
      line-height: 0.95;
      letter-spacing: -1px;
      color: var(--black);
      margin-bottom: 32px;
    }

    .hero-title em {
      font-style: italic;
      color: var(--coral);
    }

    .hero-rule {
      width: 48px;
      height: 1px;
      background: var(--black);
      margin-bottom: 28px;
    }

    .hero-sub {
      font-size: 14px;
      font-weight: 300;
      line-height: 1.75;
      color: var(--mid);
      max-width: 380px;
      margin-bottom: 48px;
    }

    .hero-cta {
      display: inline-flex;
      align-items: center;
      gap: 12px;
      font-size: 10px;
      font-weight: 500;
      letter-spacing: 2.5px;
      text-transform: uppercase;
      color: var(--black);
      border-bottom: 1px solid var(--black);
      padding-bottom: 6px;
      transition: color 0.2s, border-color 0.2s;
    }

    .hero-cta:hover { color: var(--coral); border-color: var(--coral); }
    .hero-cta-arrow { font-size: 16px; transition: transform 0.2s; }
    .hero-cta:hover .hero-cta-arrow { transform: translateX(4px); }

    .hero-right {
      position: relative;
      overflow: hidden;
      background: var(--bg-warm);
    }

    .hero-image {
      width: 100%;
      height: 100%;
      object-fit: cover;
      filter: grayscale(100%) contrast(1.1);
      transition: transform 6s ease;
    }

    .hero-right:hover .hero-image { transform: scale(1.03); }

    /* Coral overlay block */
    .hero-coral-block {
      position: absolute;
      bottom: 80px;
      left: -32px;
      width: 55%;
      height: 90px;
      background: var(--coral);
      display: flex;
      align-items: center;
      padding: 0 32px;
    }

    .hero-coral-text {
      font-family: var(--serif);
      font-size: 13px;
      font-weight: 400;
      font-style: italic;
      color: var(--bg);
      letter-spacing: 0.5px;
    }

    /* Hero image placeholder */
    .img-placeholder {
      width: 100%;
      height: 100%;
      min-height: 300px;
      background: linear-gradient(135deg, #d0cec9 0%, #b8b5ae 40%, #9a9690 100%);
      display: flex;
      align-items: center;
      justify-content: center;
      position: relative;
      overflow: hidden;
    }

    .img-placeholder::after {
      content: '';
      position: absolute;
      inset: 0;
      background: repeating-linear-gradient(
        45deg,
        transparent,
        transparent 40px,
        rgba(255,255,255,0.03) 40px,
        rgba(255,255,255,0.03) 80px
      );
    }

    .img-placeholder-label {
      font-size: 10px;
      letter-spacing: 2px;
      text-transform: uppercase;
      color: rgba(255,255,255,0.5);
      z-index: 1;
    }

    /* ── Section Header ────────────────────────────────── */
    .section-header {
      display: flex;
      align-items: flex-end;
      justify-content: space-between;
      padding-bottom: 20px;
      border-bottom: 1px solid var(--rule);
      margin-bottom: 48px;
    }

    .section-label {
      font-size: 9px;
      font-weight: 500;
      letter-spacing: 3px;
      text-transform: uppercase;
      color: var(--coral);
      margin-bottom: 8px;
    }

    .section-title {
      font-family: var(--serif);
      font-size: 38px;
      font-weight: 300;
      line-height: 1;
      color: var(--black);
    }

    .section-link {
      font-size: 9px;
      font-weight: 500;
      letter-spacing: 2px;
      text-transform: uppercase;
      color: var(--light);
      border-bottom: 1px solid var(--rule);
      padding-bottom: 4px;
      transition: color 0.2s, border-color 0.2s;
    }

    .section-link:hover { color: var(--black); border-color: var(--black); }

    /* ── Magazine Section ─────────────────────────────── */
    #magazine {
      padding: 96px 48px;
      background: var(--bg);
    }

    .articles-grid {
      display: grid;
      grid-template-columns: 2fr 1fr 1fr;
      gap: 2px;
    }

    .article-card {
      position: relative;
      overflow: hidden;
      cursor: pointer;
    }

    .article-card:hover .article-img { transform: scale(1.04); }

    .article-img-wrap {
      overflow: hidden;
      aspect-ratio: 3/4;
    }

    .article-card:first-child .article-img-wrap { aspect-ratio: 2/3; }

    .article-img {
      width: 100%;
      height: 100%;
      object-fit: cover;
      filter: grayscale(100%) contrast(1.1);
      transition: transform 0.6s cubic-bezier(0.25,0.46,0.45,0.94);
    }

    .article-body {
      padding: 24px 0;
    }

    .article-card:not(:first-child) .article-body { padding: 20px 20px 20px 16px; }

    .article-cat {
      font-size: 8px;
      font-weight: 500;
      letter-spacing: 2.5px;
      text-transform: uppercase;
      color: var(--coral);
      margin-bottom: 10px;
    }

    .article-title {
      font-family: var(--serif);
      font-size: 24px;
      font-weight: 400;
      line-height: 1.2;
      color: var(--black);
      margin-bottom: 12px;
      transition: color 0.2s;
    }

    .article-card:first-child .article-title { font-size: 32px; }
    .article-card:hover .article-title { color: var(--coral); }

    .article-excerpt {
      font-size: 12px;
      font-weight: 300;
      line-height: 1.7;
      color: var(--mid);
    }

    .article-card:not(:first-child) .article-excerpt { display: none; }

    .article-meta {
      display: flex;
      align-items: center;
      gap: 16px;
      margin-top: 16px;
      padding-top: 16px;
      border-top: 1px solid var(--rule);
    }

    .article-author {
      font-size: 9px;
      font-weight: 500;
      letter-spacing: 1.5px;
      text-transform: uppercase;
      color: var(--light);
    }

    .article-dot {
      width: 3px; height: 3px;
      border-radius: 50%;
      background: var(--rule);
    }

    /* Coral accent on featured card */
    .article-card:first-child::after {
      content: '';
      position: absolute;
      top: 0; right: 0;
      width: 4px;
      height: 80px;
      background: var(--coral);
    }

    /* ── Style & Montres Section ──────────────────────── */
    #style {
      padding: 0 48px 96px;
      background: var(--bg);
    }

    .style-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 0;
      min-height: 600px;
    }

    .style-image {
      position: relative;
      overflow: hidden;
      background: var(--bg-warm);
    }

    .style-coral-band {
      position: absolute;
      bottom: 60px;
      left: 0;
      right: 0;
      height: 60px;
      background: var(--coral);
      display: flex;
      align-items: center;
      padding: 0 40px;
      z-index: 2;
    }

    .style-band-text {
      font-family: var(--serif);
      font-size: 11px;
      font-style: italic;
      color: var(--bg);
      letter-spacing: 1px;
    }

    .style-content {
      background: var(--bg-warm);
      padding: 64px 56px;
      display: flex;
      flex-direction: column;
      justify-content: center;
    }

    .archetype-tag {
      display: inline-block;
      font-size: 8px;
      font-weight: 500;
      letter-spacing: 3px;
      text-transform: uppercase;
      color: var(--coral);
      border: 1px solid var(--coral);
      padding: 6px 14px;
      margin-bottom: 32px;
      width: fit-content;
    }

    .style-title {
      font-family: var(--serif);
      font-size: clamp(36px, 4vw, 56px);
      font-weight: 300;
      line-height: 1.05;
      color: var(--black);
      margin-bottom: 24px;
    }

    .style-title em { font-style: italic; color: var(--coral); }

    .style-body {
      font-size: 13px;
      font-weight: 300;
      line-height: 1.85;
      color: var(--mid);
      margin-bottom: 32px;
      max-width: 400px;
    }

    .style-watches {
      display: flex;
      flex-direction: column;
      gap: 12px;
      margin-bottom: 40px;
    }

    .watch-item {
      display: flex;
      align-items: center;
      gap: 16px;
      padding: 12px 0;
      border-bottom: 1px solid var(--rule);
    }

    .watch-dot {
      width: 6px; height: 6px;
      background: var(--coral);
      flex-shrink: 0;
    }

    .watch-name {
      font-family: var(--serif);
      font-size: 15px;
      font-weight: 400;
      color: var(--black);
    }

    .watch-ref {
      font-size: 9px;
      font-weight: 400;
      letter-spacing: 1px;
      color: var(--light);
      margin-left: auto;
    }

    .style-cta {
      display: inline-flex;
      align-items: center;
      gap: 10px;
      font-size: 10px;
      font-weight: 500;
      letter-spacing: 2px;
      text-transform: uppercase;
      color: var(--bg);
      background: var(--black);
      padding: 14px 28px;
      transition: background 0.2s;
      width: fit-content;
    }

    .style-cta:hover { background: var(--coral); }

    /* ── Horlogerie Section ───────────────────────────── */
    #horlogerie {
      padding: 96px 48px;
      background: var(--black);
    }

    #horlogerie .section-label { color: var(--coral); }
    #horlogerie .section-title { color: var(--bg); }
    #horlogerie .section-link { color: var(--light); border-color: rgba(255,255,255,0.12); }
    #horlogerie .section-link:hover { color: var(--bg); border-color: var(--bg); }
    #horlogerie .section-header { border-color: rgba(255,255,255,0.1); }

    .horology-grid {
      display: grid;
      grid-template-columns: 1fr 1fr 1fr;
      gap: 32px;
    }

    .horology-card {
      position: relative;
    }

    .horology-img-wrap {
      aspect-ratio: 4/5;
      overflow: hidden;
      margin-bottom: 24px;
      position: relative;
    }

    .horology-card:nth-child(2) .horology-img-wrap { margin-top: 48px; }

    .coral-tag-abs {
      position: absolute;
      top: 20px; left: 20px;
      background: var(--coral);
      padding: 6px 12px;
      font-size: 8px;
      font-weight: 500;
      letter-spacing: 2px;
      text-transform: uppercase;
      color: var(--bg);
      z-index: 2;
    }

    .horology-title {
      font-family: var(--serif);
      font-size: 22px;
      font-weight: 300;
      line-height: 1.2;
      color: var(--bg);
      margin-bottom: 12px;
    }

    .horology-text {
      font-size: 12px;
      font-weight: 300;
      line-height: 1.75;
      color: rgba(255,255,255,0.45);
    }

    /* ── Archétypes Grid ──────────────────────────────── */
    #archetypes {
      padding: 96px 48px;
      background: var(--bg-warm);
    }

    .archetypes-grid {
      display: grid;
      grid-template-columns: repeat(4, 1fr);
      gap: 2px;
    }

    .archetype-card {
      position: relative;
      overflow: hidden;
      cursor: pointer;
    }

    .archetype-inner {
      aspect-ratio: 2/3;
      position: relative;
      overflow: hidden;
    }

    .archetype-overlay {
      position: absolute;
      inset: 0;
      background: linear-gradient(to top, rgba(13,13,13,0.85) 0%, transparent 55%);
      z-index: 1;
      transition: background 0.4s;
    }

    .archetype-card:hover .archetype-overlay {
      background: linear-gradient(to top, rgba(232,103,58,0.85) 0%, rgba(13,13,13,0.4) 100%);
    }

    .archetype-info {
      position: absolute;
      bottom: 0; left: 0; right: 0;
      padding: 28px 24px;
      z-index: 2;
    }

    .archetype-num {
      font-size: 9px;
      font-weight: 400;
      letter-spacing: 2px;
      color: rgba(255,255,255,0.5);
      margin-bottom: 6px;
    }

    .archetype-name {
      font-family: var(--serif);
      font-size: 20px;
      font-weight: 300;
      color: var(--bg);
      line-height: 1.2;
    }

    .archetype-watches-preview {
      font-size: 9px;
      font-weight: 300;
      color: rgba(255,255,255,0.55);
      margin-top: 8px;
      letter-spacing: 0.5px;
    }

    /* ── Newsletter Strip ─────────────────────────────── */
    #newsletter {
      background: var(--coral);
      padding: 64px 48px;
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 40px;
    }

    .newsletter-text h2 {
      font-family: var(--serif);
      font-size: 36px;
      font-weight: 300;
      color: var(--bg);
      margin-bottom: 8px;
    }

    .newsletter-text p {
      font-size: 12px;
      font-weight: 300;
      color: rgba(255,255,255,0.75);
      letter-spacing: 0.5px;
    }

    .newsletter-form {
      display: flex;
      gap: 0;
      flex-shrink: 0;
    }

    .newsletter-input {
      width: 280px;
      padding: 14px 20px;
      border: 1px solid rgba(255,255,255,0.4);
      background: rgba(255,255,255,0.1);
      color: var(--bg);
      font-family: var(--sans);
      font-size: 12px;
      outline: none;
      transition: border-color 0.2s;
    }

    .newsletter-input::placeholder { color: rgba(255,255,255,0.55); }
    .newsletter-input:focus { border-color: var(--bg); }

    .newsletter-btn {
      padding: 14px 28px;
      background: var(--bg);
      color: var(--black);
      border: 1px solid var(--bg);
      font-family: var(--sans);
      font-size: 10px;
      font-weight: 500;
      letter-spacing: 2px;
      text-transform: uppercase;
      cursor: pointer;
      transition: background 0.2s, color 0.2s;
    }

    .newsletter-btn:hover { background: var(--black); color: var(--bg); border-color: var(--black); }

    /* ── Footer ────────────────────────────────────────── */
    footer {
      background: var(--dark);
      padding: 64px 48px 32px;
    }

    .footer-top {
      display: grid;
      grid-template-columns: 2fr 1fr 1fr 1fr;
      gap: 48px;
      padding-bottom: 48px;
      border-bottom: 1px solid rgba(255,255,255,0.08);
      margin-bottom: 32px;
    }

    .footer-brand .logo { font-size: 18px; margin-bottom: 16px; }

    .footer-tagline {
      font-size: 12px;
      font-weight: 300;
      line-height: 1.7;
      color: rgba(255,255,255,0.4);
      max-width: 240px;
    }

    .footer-col-title {
      font-size: 8px;
      font-weight: 500;
      letter-spacing: 2.5px;
      text-transform: uppercase;
      color: var(--coral);
      margin-bottom: 20px;
    }

    .footer-links {
      display: flex;
      flex-direction: column;
      gap: 10px;
    }

    .footer-links a {
      font-size: 11px;
      font-weight: 300;
      color: rgba(255,255,255,0.45);
      transition: color 0.2s;
    }

    .footer-links a:hover { color: var(--bg); }

    .footer-bottom {
      display: flex;
      align-items: center;
      justify-content: space-between;
    }

    .footer-copy {
      font-size: 10px;
      font-weight: 300;
      letter-spacing: 1px;
      color: rgba(255,255,255,0.25);
    }

    .footer-copy span { color: var(--coral); }

    /* ── Scroll reveal animation ─────────────────────── */
    .reveal {
      opacity: 0;
      transform: translateY(24px);
      transition: opacity 0.7s ease, transform 0.7s ease;
    }
    .reveal.visible { opacity: 1; transform: translateY(0); }
    .reveal-delay-1 { transition-delay: 0.1s; }
    .reveal-delay-2 { transition-delay: 0.2s; }
    .reveal-delay-3 { transition-delay: 0.3s; }
    .reveal-delay-4 { transition-delay: 0.4s; }

    /* ── Responsive ───────────────────────────────────── */
    @media (max-width: 1024px) {
      header { padding: 0 32px; }
      nav { gap: 28px; }
      .hero-left { padding: 60px 40px 60px 32px; }
      .articles-grid { grid-template-columns: 1fr 1fr; }
      .article-card:last-child { display: none; }
      .horology-grid { grid-template-columns: 1fr 1fr; }
      .horology-card:last-child { display: none; }
      .archetypes-grid { grid-template-columns: repeat(2, 1fr); }
      .footer-top { grid-template-columns: 1fr 1fr; gap: 32px; }
    }

    @media (max-width: 768px) {
      header { padding: 0 20px; }
      nav { display: none; }
      .hamburger { display: flex; }
      .mobile-nav { padding: 20px; }

      .hero { grid-template-columns: 1fr; }
      .hero-right { min-height: 50vw; }
      .hero-left { padding: 48px 20px; }
      .hero-title { font-size: 48px; }
      .hero-coral-block { left: 0; width: 80%; }

      #magazine, #style, #horlogerie, #archetypes { padding: 64px 20px; }
      #newsletter { padding: 48px 20px; flex-direction: column; align-items: flex-start; }
      .newsletter-form { width: 100%; }
      .newsletter-input { flex: 1; width: auto; }

      .articles-grid { grid-template-columns: 1fr; }
      .article-card:last-child { display: block; }
      .style-grid { grid-template-columns: 1fr; }
      .style-image { min-height: 340px; }
      .horology-grid { grid-template-columns: 1fr; }
      .horology-card:last-child { display: block; }
      .horology-card:nth-child(2) .horology-img-wrap { margin-top: 0; }
      .archetypes-grid { grid-template-columns: repeat(2, 1fr); }
      .footer-top { grid-template-columns: 1fr; }
      footer { padding: 48px 20px 24px; }
      .footer-bottom { flex-direction: column; gap: 12px; text-align: center; }
    }
  </style>
</head>
<body>

  <!-- Coral accent line -->
  <div class="accent-line"></div>

  <!-- Header -->
  <header>
    <a href="#" class="logo">INSPECT <span>Hour.</span></a>
    <nav>
      <a href="#magazine">Magazine</a>
      <a href="#style">Style & Montres</a>
      <a href="#horlogerie">Horlogerie</a>
      <a href="#archetypes">Archétypes</a>
      <a href="#newsletter" class="nav-cta">Newsletter</a>
    </nav>
    <div class="hamburger" onclick="toggleMenu()" aria-label="Menu">
      <span></span><span></span><span></span>
    </div>
  </header>

  <!-- Mobile nav -->
  <div class="mobile-nav" id="mobileNav">
    <a href="#magazine" onclick="toggleMenu()">Magazine</a>
    <a href="#style" onclick="toggleMenu()">Style & Montres</a>
    <a href="#horlogerie" onclick="toggleMenu()">Horlogerie</a>
    <a href="#archetypes" onclick="toggleMenu()">Archétypes</a>
    <a href="#newsletter" onclick="toggleMenu()">Newsletter</a>
  </div>

  <main>

    <!-- ══ HERO ══════════════════════════════════════════ -->
    <section class="hero">
      <div class="hero-left">
        <p class="hero-eyebrow reveal">Édition Printemps 2026</p>
        <h1 class="hero-title reveal reveal-delay-1">
          Le temps<br>comme <em>art</em><br>de vivre.
        </h1>
        <div class="hero-rule reveal reveal-delay-2"></div>
        <p class="hero-sub reveal reveal-delay-2">
          INSPECT Hour explore l'intersection entre l'horlogerie de précision et les codes du style contemporain. Pour ceux qui portent le temps avec intention.
        </p>
        <a href="#magazine" class="hero-cta reveal reveal-delay-3">
          Découvrir le magazine
          <span class="hero-cta-arrow">→</span>
        </a>
      </div>
      <div class="hero-right">
        <div class="img-placeholder" style="min-height: calc(100vh - 75px);">
          <span class="img-placeholder-label">Photo Hero N&B</span>
        </div>
        <div class="hero-coral-block">
          <p class="hero-coral-text">« La montre est le dernier bijou de l'homme. »</p>
        </div>
      </div>
    </section>

    <!-- ══ MAGAZINE ═══════════════════════════════════════ -->
    <section id="magazine">
      <div class="section-header reveal">
        <div>
          <p class="section-label">Le Magazine</p>
          <h2 class="section-title">À la une</h2>
        </div>
        <a href="#" class="section-link">Tous les articles →</a>
      </div>

      <div class="articles-grid">
        <!-- Featured article -->
        <div class="article-card reveal">
          <div class="article-img-wrap">
            <div class="img-placeholder">
              <span class="img-placeholder-label">Photo Article Principale</span>
            </div>
          </div>
          <div class="article-body">
            <p class="article-cat">Analyse · Stratégie de marque</p>
            <h3 class="article-title">Bauhaus au poignet — Comment l'architecture influence l'horlogerie contemporaine</h3>
            <p class="article-excerpt">De Nomos à Junghans, les manufactures allemandes ont fait du Bauhaus une philosophie horlogère. Rigueur formelle, lisibilité absolue, beauté fonctionnelle.</p>
            <div class="article-meta">
              <span class="article-author">Clément Dumont</span>
              <div class="article-dot"></div>
              <span class="article-author">22 Avril 2026</span>
            </div>
          </div>
        </div>

        <!-- Article 2 -->
        <div class="article-card reveal reveal-delay-1">
          <div class="article-img-wrap">
            <div class="img-placeholder">
              <span class="img-placeholder-label">Photo Article 2</span>
            </div>
          </div>
          <div class="article-body">
            <p class="article-cat">Style · Codes Culturels</p>
            <h3 class="article-title">French Nonchalance — La Tank portée avec désinvolture</h3>
            <div class="article-meta">
              <span class="article-author">22 Avril 2026</span>
            </div>
          </div>
        </div>

        <!-- Article 3 -->
        <div class="article-card reveal reveal-delay-2">
          <div class="article-img-wrap">
            <div class="img-placeholder">
              <span class="img-placeholder-label">Photo Article 3</span>
            </div>
          </div>
          <div class="article-body">
            <p class="article-cat">Horlogerie · Complications</p>
            <h3 class="article-title">Le tourbillon est-il encore pertinent en 2026 ?</h3>
            <div class="article-meta">
              <span class="article-author">18 Avril 2026</span>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- ══ STYLE & MONTRES ════════════════════════════════ -->
    <section id="style">
      <div class="section-header reveal">
        <div>
          <p class="section-label">Style & Montres</p>
          <h2 class="section-title">L'Archétype du mois</h2>
        </div>
        <a href="#" class="section-link">Explorer les archétypes →</a>
      </div>

      <div class="style-grid">
        <div class="style-image">
          <div class="img-placeholder" style="min-height: 600px;">
            <span class="img-placeholder-label">Portrait Lifestyle N&B</span>
          </div>
          <div class="style-coral-band">
            <span class="style-band-text">L'Architecte × Continental European</span>
          </div>
        </div>

        <div class="style-content reveal">
          <div class="archetype-tag">Archétype 01 / 08</div>
          <h2 class="style-title">L'Architecte —<br><em>Proportion & Intention</em></h2>
          <p class="style-body">
            Il porte ses montres comme il conçoit ses projets : avec une intention derrière chaque détail visible. Rigueur formelle, sens de la proportion, beauté fonctionnelle. Le Royal Oak n'est pas un choix ostentatoire — c'est une déclaration de principe.
          </p>
          <div class="style-watches">
            <div class="watch-item">
              <div class="watch-dot"></div>
              <span class="watch-name">Audemars Piguet Royal Oak</span>
              <span class="watch-ref">Réf. 15500ST</span>
            </div>
            <div class="watch-item">
              <div class="watch-dot"></div>
              <span class="watch-name">Bulgari Octo Finissimo</span>
              <span class="watch-ref">Réf. 103431</span>
            </div>
            <div class="watch-item">
              <div class="watch-dot"></div>
              <span class="watch-name">Cartier Santos</span>
              <span class="watch-ref">Réf. WSSA0018</span>
            </div>
          </div>
          <a href="#" class="style-cta">
            Lire l'archétype complet →
          </a>
        </div>
      </div>
    </section>

    <!-- ══ HORLOGERIE ═════════════════════════════════════ -->
    <section id="horlogerie">
      <div class="section-header reveal">
        <div>
          <p class="section-label">Horlogerie</p>
          <h2 class="section-title">Savoir-faire</h2>
        </div>
        <a href="#" class="section-link">Toutes les fiches →</a>
      </div>

      <div class="horology-grid">
        <div class="horology-card reveal">
          <div class="horology-img-wrap">
            <div class="coral-tag-abs">Complications</div>
            <div class="img-placeholder" style="min-height: 320px;">
              <span class="img-placeholder-label">Photo Mouvement</span>
            </div>
          </div>
          <h3 class="horology-title">Le tourbillon — Beauté inutile ou chef-d'œuvre mécanique ?</h3>
          <p class="horology-text">Inventé par Breguet en 1801 pour compenser les effets de la gravité, le tourbillon est aujourd'hui un symbole de maîtrise plus qu'un outil de précision.</p>
        </div>

        <div class="horology-card reveal reveal-delay-1">
          <div class="horology-img-wrap">
            <div class="coral-tag-abs">Finitions</div>
            <div class="img-placeholder" style="min-height: 320px;">
              <span class="img-placeholder-label">Photo Finitions</span>
            </div>
          </div>
          <h3 class="horology-title">Anglage & perlage — L'invisible qui fait la valeur</h3>
          <p class="horology-text">Les finitions à la main définissent la haute horlogerie. Un anglage parfait sur un composant jamais visible — c'est l'éthique du métier.</p>
        </div>

        <div class="horology-card reveal reveal-delay-2">
          <div class="horology-img-wrap">
            <div class="coral-tag-abs">Matériaux</div>
            <div class="img-placeholder" style="min-height: 320px;">
              <span class="img-placeholder-label">Photo Matériaux</span>
            </div>
          </div>
          <h3 class="horology-title">Acier 904L vs 316L — Pourquoi Rolex est seul dans sa catégorie</h3>
          <p class="horology-text">La résistance à la corrosion, le poli exceptionnel — l'acier 904L utilisé par Rolex depuis 1985 change fondamentalement le toucher du bracelet.</p>
        </div>
      </div>
    </section>

    <!-- ══ ARCHÉTYPES ═════════════════════════════════════ -->
    <section id="archetypes">
      <div class="section-header reveal">
        <div>
          <p class="section-label" style="color: var(--coral);">Les 8 Archétypes</p>
          <h2 class="section-title">Trouver votre profil</h2>
        </div>
        <a href="#" class="section-link">Voir la matrice complète →</a>
      </div>

      <div class="archetypes-grid">
        <div class="archetype-card reveal">
          <div class="archetype-inner">
            <div class="img-placeholder" style="min-height: 400px; background: linear-gradient(135deg,#2a2a2a,#1a1a1a);">
              <span class="img-placeholder-label" style="color:rgba(255,255,255,0.3);">Photo Archétype</span>
            </div>
            <div class="archetype-overlay"></div>
            <div class="archetype-info">
              <p class="archetype-num">01</p>
              <h3 class="archetype-name">L'Architecte</h3>
              <p class="archetype-watches-preview">Royal Oak · Octo Finissimo · Santos</p>
            </div>
          </div>
        </div>

        <div class="archetype-card reveal reveal-delay-1">
          <div class="archetype-inner">
            <div class="img-placeholder" style="min-height: 400px; background: linear-gradient(135deg,#2d2a26,#1a1710);">
              <span class="img-placeholder-label" style="color:rgba(255,255,255,0.3);">Photo Archétype</span>
            </div>
            <div class="archetype-overlay"></div>
            <div class="archetype-info">
              <p class="archetype-num">02</p>
              <h3 class="archetype-name">L'Aventurier Littéraire</h3>
              <p class="archetype-watches-preview">Explorer · Fifty Fathoms · Black Bay</p>
            </div>
          </div>
        </div>

        <div class="archetype-card reveal reveal-delay-2">
          <div class="archetype-inner">
            <div class="img-placeholder" style="min-height: 400px; background: linear-gradient(135deg,#1a1a22,#12121a);">
              <span class="img-placeholder-label" style="color:rgba(255,255,255,0.3);">Photo Archétype</span>
            </div>
            <div class="archetype-overlay"></div>
            <div class="archetype-info">
              <p class="archetype-num">03</p>
              <h3 class="archetype-name">Le Dandy Discret</h3>
              <p class="archetype-watches-preview">Calatrava · Patrimony · Tank</p>
            </div>
          </div>
        </div>

        <div class="archetype-card reveal reveal-delay-3">
          <div class="archetype-inner">
            <div class="img-placeholder" style="min-height: 400px; background: linear-gradient(135deg,#1a2222,#101a1a);">
              <span class="img-placeholder-label" style="color:rgba(255,255,255,0.3);">Photo Archétype</span>
            </div>
            <div class="archetype-overlay"></div>
            <div class="archetype-info">
              <p class="archetype-num">04</p>
              <h3 class="archetype-name">Le Minimaliste Radical</h3>
              <p class="archetype-watches-preview">Nomos Orion · Junghans · Ressence</p>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- ══ NEWSLETTER ═════════════════════════════════════ -->
    <section id="newsletter">
      <div class="newsletter-text">
        <h2>La revue de presse horlogère.</h2>
        <p>Chaque lundi — les meilleures lectures de la semaine, sélectionnées et commentées.</p>
      </div>
      <form class="newsletter-form" onsubmit="return false;">
        <input type="email" class="newsletter-input" placeholder="votre@email.com">
        <button type="submit" class="newsletter-btn">S'abonner</button>
      </form>
    </section>

  </main>

  <!-- Footer -->
  <footer>
    <div class="footer-top">
      <div class="footer-brand">
        <div class="logo">INSPECT <span>Hour.</span></div>
        <p class="footer-tagline">Le magazine qui explore l'intersection entre l'horlogerie de précision et les codes du style contemporain.</p>
      </div>
      <div>
        <p class="footer-col-title">Rubriques</p>
        <div class="footer-links">
          <a href="#magazine">Magazine</a>
          <a href="#style">Style & Montres</a>
          <a href="#horlogerie">Horlogerie</a>
          <a href="#archetypes">Archétypes</a>
        </div>
      </div>
      <div>
        <p class="footer-col-title">Ressources</p>
        <div class="footer-links">
          <a href="#">Guides d'achat</a>
          <a href="#">Base de données</a>
          <a href="#">Comparateur</a>
          <a href="#">Glossaire</a>
        </div>
      </div>
      <div>
        <p class="footer-col-title">À propos</p>
        <div class="footer-links">
          <a href="#">La vision éditoriale</a>
          <a href="#">L'auteur</a>
          <a href="#">Collaborations</a>
          <a href="#">Contact</a>
        </div>
      </div>
    </div>
    <div class="footer-bottom">
      <p class="footer-copy">© 2026 <span>INSPECT Hour.</span> — Tous droits réservés</p>
      <p class="footer-copy">Fait avec intention — Design & Code</p>
    </div>
  </footer>

  <script>
    // ── Mobile menu ──────────────────────────────────────
    function toggleMenu() {
      const nav = document.getElementById('mobileNav');
      nav.classList.toggle('open');
    }

    // ── Scroll reveal ─────────────────────────────────────
    const reveals = document.querySelectorAll('.reveal');
    const observer = new IntersectionObserver((entries) => {
      entries.forEach(entry => {
        if (entry.isIntersecting) {
          entry.target.classList.add('visible');
          observer.unobserve(entry.target);
        }
      });
    }, { threshold: 0.1, rootMargin: '0px 0px -40px 0px' });

    reveals.forEach(el => observer.observe(el));

    // ── Header scroll state ───────────────────────────────
    const header = document.querySelector('header');
    window.addEventListener('scroll', () => {
      if (window.scrollY > 40) {
        header.style.boxShadow = '0 1px 24px rgba(0,0,0,0.06)';
      } else {
        header.style.boxShadow = 'none';
      }
    });
  </script>

</body>
</html>
