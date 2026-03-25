<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Sadaf Khan — Java Backend Developer</title>
<link href="https://fonts.googleapis.com/css2?family=DM+Serif+Display:ital@0;1&family=DM+Mono:wght@300;400;500&family=Outfit:wght@300;400;500;600&display=swap" rel="stylesheet"/>
<style>
  :root {
    --bg: #0a0a0f;
    --surface: #111118;
    --card: #16161f;
    --border: #222230;
    --accent: #7c6af7;
    --accent2: #e8745a;
    --accent3: #4ecdc4;
    --text: #e8e8f0;
    --muted: #6b6b80;
    --highlight: #f0eeff;
  }

  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  html { scroll-behavior: smooth; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'Outfit', sans-serif;
    font-weight: 300;
    line-height: 1.7;
    overflow-x: hidden;
  }

  /* Grain texture overlay */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)' opacity='0.04'/%3E%3C/svg%3E");
    pointer-events: none;
    z-index: 999;
    opacity: 0.4;
  }

  /* ─── NAV ─── */
  nav {
    position: fixed;
    top: 0; left: 0; right: 0;
    z-index: 100;
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 1.2rem 3rem;
    backdrop-filter: blur(20px);
    background: rgba(10,10,15,0.7);
    border-bottom: 1px solid var(--border);
  }

  .nav-logo {
    font-family: 'DM Mono', monospace;
    font-size: 0.85rem;
    color: var(--accent);
    letter-spacing: 0.15em;
    text-transform: uppercase;
  }

  .nav-links {
    display: flex;
    gap: 2rem;
    list-style: none;
  }

  .nav-links a {
    color: var(--muted);
    text-decoration: none;
    font-size: 0.82rem;
    letter-spacing: 0.08em;
    text-transform: uppercase;
    font-family: 'DM Mono', monospace;
    transition: color 0.2s;
  }
  .nav-links a:hover { color: var(--text); }

  /* ─── HERO ─── */
  .hero {
    min-height: 100vh;
    display: grid;
    grid-template-columns: 1fr 1fr;
    position: relative;
    overflow: hidden;
  }

  .hero-left {
    display: flex;
    flex-direction: column;
    justify-content: center;
    padding: 8rem 4rem 4rem 5rem;
    position: relative;
    z-index: 2;
  }

  .hero-tag {
    font-family: 'DM Mono', monospace;
    font-size: 0.75rem;
    color: var(--accent);
    letter-spacing: 0.2em;
    text-transform: uppercase;
    margin-bottom: 1.5rem;
    display: flex;
    align-items: center;
    gap: 0.75rem;
  }
  .hero-tag::before {
    content: '';
    display: block;
    width: 32px; height: 1px;
    background: var(--accent);
  }

  .hero-name {
    font-family: 'DM Serif Display', serif;
    font-size: clamp(3.5rem, 6vw, 5.5rem);
    line-height: 1.05;
    color: var(--highlight);
    margin-bottom: 0.3rem;
  }

  .hero-name .italic {
    font-style: italic;
    color: var(--accent);
  }

  .hero-title {
    font-family: 'DM Mono', monospace;
    font-size: 0.9rem;
    color: var(--accent2);
    letter-spacing: 0.12em;
    margin-bottom: 2rem;
    margin-top: 0.5rem;
  }

  .hero-desc {
    font-size: 1rem;
    color: var(--muted);
    max-width: 420px;
    margin-bottom: 2.5rem;
    line-height: 1.8;
  }

  .hero-cta {
    display: flex;
    gap: 1rem;
    flex-wrap: wrap;
  }

  .btn-primary {
    background: var(--accent);
    color: white;
    padding: 0.75rem 2rem;
    border-radius: 4px;
    text-decoration: none;
    font-size: 0.85rem;
    font-weight: 500;
    letter-spacing: 0.05em;
    transition: all 0.2s;
    border: 1px solid var(--accent);
  }
  .btn-primary:hover {
    background: transparent;
    color: var(--accent);
  }

  .btn-secondary {
    background: transparent;
    color: var(--text);
    padding: 0.75rem 2rem;
    border-radius: 4px;
    text-decoration: none;
    font-size: 0.85rem;
    font-weight: 400;
    letter-spacing: 0.05em;
    border: 1px solid var(--border);
    transition: all 0.2s;
  }
  .btn-secondary:hover {
    border-color: var(--accent);
    color: var(--accent);
  }

  .hero-right {
    position: relative;
    display: flex;
    align-items: center;
    justify-content: center;
    overflow: hidden;
  }

  .hero-orb {
    position: absolute;
    width: 600px; height: 600px;
    border-radius: 50%;
    background: radial-gradient(circle at 40% 40%, rgba(124,106,247,0.25), rgba(232,116,90,0.1), transparent 70%);
    animation: float 8s ease-in-out infinite;
    filter: blur(1px);
  }

  @keyframes float {
    0%,100% { transform: translateY(0) rotate(0deg); }
    33% { transform: translateY(-20px) rotate(5deg); }
    66% { transform: translateY(10px) rotate(-3deg); }
  }

  .hero-stats {
    position: relative;
    z-index: 2;
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 1rem;
    padding: 2rem;
  }

  .stat-card {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 1.5rem;
    transition: border-color 0.2s, transform 0.2s;
  }
  .stat-card:hover {
    border-color: var(--accent);
    transform: translateY(-2px);
  }

  .stat-num {
    font-family: 'DM Serif Display', serif;
    font-size: 2.2rem;
    color: var(--highlight);
    line-height: 1;
    margin-bottom: 0.25rem;
  }

  .stat-num span { color: var(--accent); }

  .stat-label {
    font-family: 'DM Mono', monospace;
    font-size: 0.7rem;
    color: var(--muted);
    letter-spacing: 0.1em;
    text-transform: uppercase;
  }

  /* ─── SECTIONS ─── */
  section {
    padding: 6rem 5rem;
    max-width: 1200px;
    margin: 0 auto;
  }

  .section-header {
    display: flex;
    align-items: center;
    gap: 1rem;
    margin-bottom: 3rem;
  }

  .section-num {
    font-family: 'DM Mono', monospace;
    font-size: 0.75rem;
    color: var(--accent);
    opacity: 0.6;
  }

  .section-title {
    font-family: 'DM Serif Display', serif;
    font-size: 2.2rem;
    color: var(--highlight);
  }

  .section-line {
    flex: 1;
    height: 1px;
    background: var(--border);
  }

  /* ─── SKILLS ─── */
  .skills-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
    gap: 1.25rem;
  }

  .skill-group {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 1.5rem;
    transition: border-color 0.25s;
  }
  .skill-group:hover { border-color: var(--accent); }

  .skill-group-label {
    font-family: 'DM Mono', monospace;
    font-size: 0.7rem;
    color: var(--accent);
    letter-spacing: 0.15em;
    text-transform: uppercase;
    margin-bottom: 1rem;
  }

  .skill-tags {
    display: flex;
    flex-wrap: wrap;
    gap: 0.5rem;
  }

  .tag {
    background: rgba(124,106,247,0.1);
    border: 1px solid rgba(124,106,247,0.25);
    color: var(--text);
    font-size: 0.78rem;
    padding: 0.3rem 0.75rem;
    border-radius: 100px;
    font-family: 'DM Mono', monospace;
    transition: all 0.2s;
  }
  .tag:hover {
    background: rgba(124,106,247,0.2);
    border-color: var(--accent);
    color: var(--accent);
  }

  /* ─── EXPERIENCE ─── */
  .timeline {
    position: relative;
    padding-left: 2rem;
  }

  .timeline::before {
    content: '';
    position: absolute;
    left: 0; top: 0.5rem; bottom: 0.5rem;
    width: 1px;
    background: linear-gradient(to bottom, var(--accent), transparent);
  }

  .timeline-item {
    position: relative;
    padding-bottom: 3rem;
  }
  .timeline-item:last-child { padding-bottom: 0; }

  .timeline-item::before {
    content: '';
    position: absolute;
    left: -2.4rem;
    top: 0.4rem;
    width: 8px; height: 8px;
    border-radius: 50%;
    background: var(--accent);
    box-shadow: 0 0 12px var(--accent);
  }

  .timeline-meta {
    font-family: 'DM Mono', monospace;
    font-size: 0.72rem;
    color: var(--accent2);
    letter-spacing: 0.1em;
    margin-bottom: 0.35rem;
  }

  .timeline-role {
    font-family: 'DM Serif Display', serif;
    font-size: 1.4rem;
    color: var(--highlight);
    margin-bottom: 0.25rem;
  }

  .timeline-org {
    font-size: 0.85rem;
    color: var(--muted);
    margin-bottom: 1rem;
    font-family: 'DM Mono', monospace;
  }

  .timeline-bullets {
    list-style: none;
    display: flex;
    flex-direction: column;
    gap: 0.5rem;
  }

  .timeline-bullets li {
    font-size: 0.88rem;
    color: var(--muted);
    padding-left: 1.25rem;
    position: relative;
  }

  .timeline-bullets li::before {
    content: '→';
    position: absolute;
    left: 0;
    color: var(--accent3);
  }

  /* ─── PROJECT ─── */
  .project-card {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 16px;
    overflow: hidden;
    transition: border-color 0.25s, transform 0.25s;
    position: relative;
  }
  .project-card:hover {
    border-color: var(--accent2);
    transform: translateY(-4px);
  }

  .project-card::before {
    content: '';
    position: absolute;
    top: 0; left: 0; right: 0;
    height: 3px;
    background: linear-gradient(90deg, var(--accent), var(--accent2), var(--accent3));
  }

  .project-body { padding: 2rem; }

  .project-shield {
    font-size: 2rem;
    margin-bottom: 1rem;
    display: block;
  }

  .project-name {
    font-family: 'DM Serif Display', serif;
    font-size: 1.6rem;
    color: var(--highlight);
    margin-bottom: 0.5rem;
  }

  .project-stack {
    display: flex;
    flex-wrap: wrap;
    gap: 0.4rem;
    margin-bottom: 1rem;
  }

  .stack-tag {
    background: rgba(78,205,196,0.1);
    border: 1px solid rgba(78,205,196,0.2);
    color: var(--accent3);
    font-size: 0.72rem;
    padding: 0.2rem 0.6rem;
    border-radius: 4px;
    font-family: 'DM Mono', monospace;
  }

  .project-desc {
    font-size: 0.88rem;
    color: var(--muted);
    line-height: 1.8;
    margin-bottom: 1.25rem;
  }

  .project-features {
    list-style: none;
    display: flex;
    flex-direction: column;
    gap: 0.5rem;
    margin-bottom: 1.5rem;
  }

  .project-features li {
    font-size: 0.84rem;
    color: var(--muted);
    padding-left: 1.25rem;
    position: relative;
  }

  .project-features li::before {
    content: '◆';
    position: absolute;
    left: 0;
    color: var(--accent2);
    font-size: 0.5rem;
    top: 0.35em;
  }

  .project-link {
    display: inline-flex;
    align-items: center;
    gap: 0.5rem;
    color: var(--accent2);
    text-decoration: none;
    font-family: 'DM Mono', monospace;
    font-size: 0.78rem;
    letter-spacing: 0.08em;
    transition: gap 0.2s;
  }
  .project-link:hover { gap: 0.75rem; }

  /* ─── EDUCATION / CERTS ─── */
  .edu-card {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 2rem;
    display: grid;
    grid-template-columns: 1fr auto;
    align-items: start;
    gap: 1rem;
    transition: border-color 0.2s;
  }
  .edu-card:hover { border-color: var(--accent3); }

  .edu-degree {
    font-family: 'DM Serif Display', serif;
    font-size: 1.3rem;
    color: var(--highlight);
    margin-bottom: 0.3rem;
  }

  .edu-school {
    font-family: 'DM Mono', monospace;
    font-size: 0.8rem;
    color: var(--muted);
    margin-bottom: 0.5rem;
  }

  .edu-period {
    font-family: 'DM Mono', monospace;
    font-size: 0.72rem;
    color: var(--accent);
  }

  .edu-cgpa {
    background: linear-gradient(135deg, var(--accent), var(--accent2));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    font-family: 'DM Serif Display', serif;
    font-size: 2rem;
    text-align: right;
    line-height: 1;
  }

  .cgpa-label {
    font-family: 'DM Mono', monospace;
    font-size: 0.65rem;
    color: var(--muted);
    text-align: right;
    margin-top: 0.25rem;
  }

  /* ─── CERTIFICATIONS ─── */
  .certs-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(260px, 1fr));
    gap: 1rem;
  }

  .cert-card {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 10px;
    padding: 1.25rem 1.5rem;
    display: flex;
    align-items: center;
    gap: 1rem;
    transition: border-color 0.2s, transform 0.2s;
  }
  .cert-card:hover {
    border-color: var(--accent2);
    transform: translateX(4px);
  }

  .cert-icon {
    font-size: 1.5rem;
    flex-shrink: 0;
  }

  .cert-name {
    font-size: 0.87rem;
    color: var(--text);
    font-weight: 400;
  }

  .cert-issuer {
    font-family: 'DM Mono', monospace;
    font-size: 0.7rem;
    color: var(--muted);
    margin-top: 0.2rem;
  }

  /* ─── ACHIEVEMENTS ─── */
  .achieve-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 1rem;
  }

  .achieve-card {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 1.5rem;
    text-align: center;
    transition: border-color 0.2s, transform 0.2s;
  }
  .achieve-card:hover {
    border-color: var(--accent);
    transform: translateY(-3px);
  }

  .achieve-icon { font-size: 2rem; margin-bottom: 0.75rem; }

  .achieve-title {
    font-size: 0.87rem;
    color: var(--text);
    font-weight: 400;
  }

  /* ─── GITHUB ─── */
  .github-section {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 16px;
    padding: 2.5rem;
    display: flex;
    flex-wrap: wrap;
    gap: 1.5rem;
    justify-content: center;
    align-items: center;
  }

  .github-section img {
    border-radius: 8px;
    max-width: 100%;
    height: auto;
    filter: contrast(1.05);
  }

  /* ─── FOOTER ─── */
  footer {
    border-top: 1px solid var(--border);
    padding: 2rem 5rem;
    display: flex;
    justify-content: space-between;
    align-items: center;
    max-width: 1200px;
    margin: 0 auto;
  }

  .footer-left {
    font-family: 'DM Mono', monospace;
    font-size: 0.78rem;
    color: var(--muted);
  }

  .footer-right {
    font-family: 'DM Mono', monospace;
    font-size: 0.72rem;
    color: var(--muted);
    letter-spacing: 0.1em;
  }

  /* ─── ANIMATIONS ─── */
  .fade-up {
    opacity: 0;
    transform: translateY(24px);
    animation: fadeUp 0.7s ease forwards;
  }

  @keyframes fadeUp {
    to { opacity: 1; transform: translateY(0); }
  }

  .delay-1 { animation-delay: 0.1s; }
  .delay-2 { animation-delay: 0.2s; }
  .delay-3 { animation-delay: 0.3s; }
  .delay-4 { animation-delay: 0.4s; }
  .delay-5 { animation-delay: 0.5s; }

  /* Divider */
  .divider {
    border: none;
    border-top: 1px solid var(--border);
    margin: 0;
  }

  /* ─── RESPONSIVE ─── */
  @media (max-width: 900px) {
    nav { padding: 1rem 1.5rem; }
    .nav-links { display: none; }
    .hero { grid-template-columns: 1fr; }
    .hero-left { padding: 6rem 1.5rem 2rem; }
    .hero-right { padding: 2rem; }
    .hero-stats { grid-template-columns: 1fr 1fr; }
    section { padding: 4rem 1.5rem; }
    .achieve-grid { grid-template-columns: 1fr 1fr; }
    footer { padding: 1.5rem; flex-direction: column; gap: 0.5rem; text-align: center; }
  }
</style>
</head>
<body>

<!-- NAV -->
<nav>
  <span class="nav-logo">SK — Portfolio</span>
  <ul class="nav-links">
    <li><a href="#skills">Skills</a></li>
    <li><a href="#experience">Experience</a></li>
    <li><a href="#projects">Projects</a></li>
    <li><a href="#education">Education</a></li>
  </ul>
</nav>

<!-- HERO -->
<div class="hero">
  <div class="hero-left">
    <div class="hero-tag fade-up">Java Backend Developer</div>
    <h1 class="hero-name fade-up delay-1">Sadaf<br/><span class="italic">Khan</span></h1>
    <p class="hero-title fade-up delay-2">B.Tech CSE '27 · Galgotias University</p>
    <p class="hero-desc fade-up delay-3">
      Passionate about building secure, scalable, and high-performance web applications.
      Specializing in Java, Spring Boot, and enterprise backend architecture.
    </p>
    <div class="hero-cta fade-up delay-4">
      <a href="https://safeher-a-women-saftey-app.onrender.com" class="btn-primary" target="_blank">View Live Project</a>
      <a href="https://github.com/Sadaf-khan61" class="btn-secondary" target="_blank">GitHub ↗</a>
    </div>
  </div>

  <div class="hero-right">
    <div class="hero-orb"></div>
    <div class="hero-stats fade-up delay-3">
      <div class="stat-card">
        <div class="stat-num">9.38<span>/10</span></div>
        <div class="stat-label">CGPA</div>
      </div>
      <div class="stat-card">
        <div class="stat-num">900<span>+</span></div>
        <div class="stat-label">DSA Problems</div>
      </div>
      <div class="stat-card">
        <div class="stat-num">2</div>
        <div class="stat-label">Internships</div>
      </div>
      <div class="stat-card">
        <div class="stat-num">3</div>
        <div class="stat-label">Certifications</div>
      </div>
    </div>
  </div>
</div>

<hr class="divider"/>

<!-- SKILLS -->
<section id="skills">
  <div class="section-header">
    <span class="section-num">01</span>
    <h2 class="section-title">Technical Skills</h2>
    <div class="section-line"></div>
  </div>

  <div class="skills-grid">
    <div class="skill-group">
      <div class="skill-group-label">Languages</div>
      <div class="skill-tags">
        <span class="tag">Java</span>
        <span class="tag">SQL</span>
        <span class="tag">HTML/CSS</span>
        <span class="tag">JavaScript</span>
      </div>
    </div>

    <div class="skill-group">
      <div class="skill-group-label">Frameworks & Tools</div>
      <div class="skill-tags">
        <span class="tag">Spring Boot</span>
        <span class="tag">Spring</span>
        <span class="tag">JSP</span>
        <span class="tag">Servlets</span>
        <span class="tag">Maven</span>
        <span class="tag">JDBC</span>
      </div>
    </div>

    <div class="skill-group">
      <div class="skill-group-label">Databases</div>
      <div class="skill-tags">
        <span class="tag">MySQL</span>
        <span class="tag">Aiven Cloud DB</span>
      </div>
    </div>

    <div class="skill-group">
      <div class="skill-group-label">Core Concepts</div>
      <div class="skill-tags">
        <span class="tag">OOP</span>
        <span class="tag">DSA</span>
        <span class="tag">MVC</span>
        <span class="tag">REST APIs</span>
        <span class="tag">DAO Pattern</span>
      </div>
    </div>

    <div class="skill-group">
      <div class="skill-group-label">Developer Tools</div>
      <div class="skill-tags">
        <span class="tag">Git</span>
        <span class="tag">GitHub</span>
        <span class="tag">IntelliJ IDEA</span>
        <span class="tag">Eclipse</span>
        <span class="tag">Render.com</span>
      </div>
    </div>

    <div class="skill-group">
      <div class="skill-group-label">Soft Skills</div>
      <div class="skill-tags">
        <span class="tag">Problem Solving</span>
        <span class="tag">Communication</span>
        <span class="tag">Team Collaboration</span>
      </div>
    </div>
  </div>
</section>

<hr class="divider"/>

<!-- EXPERIENCE -->
<section id="experience">
  <div class="section-header">
    <span class="section-num">02</span>
    <h2 class="section-title">Experience</h2>
    <div class="section-line"></div>
  </div>

  <div class="timeline">
    <div class="timeline-item">
      <div class="timeline-meta">Apr 2025 – Jun 2025</div>
      <div class="timeline-role">Java Full Stack Developer Intern</div>
      <div class="timeline-org">AICTE (EduSkills)</div>
      <ul class="timeline-bullets">
        <li>Built Java-based web applications using JSP, Servlets, and Spring Boot</li>
        <li>Implemented backend modules and business logic across multiple features</li>
        <li>Gained hands-on experience with MVC, REST APIs, DAO layers, and deployment</li>
      </ul>
    </div>

    <div class="timeline-item">
      <div class="timeline-meta">Jul 2025 – Sep 2025</div>
      <div class="timeline-role">Cloud Virtual Intern</div>
      <div class="timeline-org">AWS (Amazon Web Services)</div>
      <ul class="timeline-bullets">
        <li>Completed cloud computing fundamentals with hands-on cloud-based tasks</li>
        <li>Worked with virtual machines, storage, and cloud deployment concepts</li>
        <li>Applied core principles of cloud architecture, scalability, and security</li>
      </ul>
    </div>
  </div>
</section>

<hr class="divider"/>

<!-- PROJECTS -->
<section id="projects">
  <div class="section-header">
    <span class="section-num">03</span>
    <h2 class="section-title">Projects</h2>
    <div class="section-line"></div>
  </div>

  <div class="project-card">
    <div class="project-body">
      <span class="project-shield">🛡️</span>
      <h3 class="project-name">SafeHer — AI-Powered Women Safety App</h3>
      <div class="project-stack">
        <span class="stack-tag">Java</span>
        <span class="stack-tag">Spring Boot</span>
        <span class="stack-tag">MySQL</span>
        <span class="stack-tag">HTML/CSS/JS</span>
        <span class="stack-tag">Render.com</span>
        <span class="stack-tag">Aiven</span>
      </div>
      <p class="project-desc">
        A full-stack women safety web application featuring a Spring Boot REST API backend
        and a mobile-first frontend, deployed live on Render.com with cloud MySQL on Aiven.
      </p>
      <ul class="project-features">
        <li>One-tap SOS alert system with real-time GPS location capture and automatic event logging</li>
        <li>AI FIR Generator that converts user descriptions into formal legal police complaints</li>
        <li>Evidence Vault with encrypted audio/video recording for secure evidence preservation</li>
        <li>Community Safety module with Guardian Angel mode and fake call simulator</li>
      </ul>
      <a href="https://safeher-a-women-saftey-app.onrender.com" class="project-link" target="_blank">
        View Live App →
      </a>
    </div>
  </div>
</section>

<hr class="divider"/>

<!-- EDUCATION -->
<section id="education">
  <div class="section-header">
    <span class="section-num">04</span>
    <h2 class="section-title">Education</h2>
    <div class="section-line"></div>
  </div>

  <div class="edu-card">
    <div>
      <div class="edu-degree">B.Tech in Computer Science & Engineering</div>
      <div class="edu-school">Galgotias University, Greater Noida</div>
      <div class="edu-period">2023 – 2027</div>
    </div>
    <div>
      <div class="edu-cgpa">9.38</div>
      <div class="cgpa-label">CGPA / 10</div>
    </div>
  </div>
</section>

<hr class="divider"/>

<!-- CERTIFICATIONS -->
<section id="certifications">
  <div class="section-header">
    <span class="section-num">05</span>
    <h2 class="section-title">Certifications</h2>
    <div class="section-line"></div>
  </div>

  <div class="certs-grid">
    <div class="cert-card">
      <div class="cert-icon">🎓</div>
      <div>
        <div class="cert-name">Design Thinking</div>
        <div class="cert-issuer">NPTEL</div>
      </div>
    </div>
    <div class="cert-card">
      <div class="cert-icon">☕</div>
      <div>
        <div class="cert-name">Full Stack Java Internship</div>
        <div class="cert-issuer">AICTE</div>
      </div>
    </div>
    <div class="cert-card">
      <div class="cert-icon">☁️</div>
      <div>
        <div class="cert-name">Cloud Virtual Internship</div>
        <div class="cert-issuer">AWS</div>
      </div>
    </div>
  </div>
</section>

<hr class="divider"/>

<!-- ACHIEVEMENTS -->
<section id="achievements">
  <div class="section-header">
    <span class="section-num">06</span>
    <h2 class="section-title">Achievements</h2>
    <div class="section-line"></div>
  </div>

  <div class="achieve-grid">
    <div class="achieve-card">
      <div class="achieve-icon">🏆</div>
      <div class="achieve-title">Strong academic performance with 9.38 CGPA</div>
    </div>
    <div class="achieve-card">
      <div class="achieve-icon">⚙️</div>
      <div class="achieve-title">Built multiple Java applications independently</div>
    </div>
    <div class="achieve-card">
      <div class="achieve-icon">🧠</div>
      <div class="achieve-title">Solved 900+ DSA problems across platforms</div>
    </div>
  </div>
</section>

<hr class="divider"/>

<!-- GITHUB STATS -->
<section>
  <div class="section-header">
    <span class="section-num">07</span>
    <h2 class="section-title">GitHub Activity</h2>
    <div class="section-line"></div>
  </div>

  <div class="github-section">
    <img src="https://github-readme-stats.vercel.app/api?username=Sadaf-khan61&show_icons=true&theme=dark&bg_color=16161f&border_color=222230&title_color=7c6af7&icon_color=e8745a&text_color=e8e8f0&hide_border=false" alt="Sadaf's GitHub Stats" />
    <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=Sadaf-khan61&layout=compact&theme=dark&bg_color=16161f&border_color=222230&title_color=7c6af7&text_color=e8e8f0&hide_border=false" alt="Top Languages" />
  </div>
</section>

<hr class="divider"/>

<!-- FOOTER -->
<footer>
  <div class="footer-left">
    Sadaf Khan &mdash; Java Backend Developer &mdash; B.Tech CSE '27
  </div>
  <div class="footer-right">Galgotias University · Greater Noida</div>
</footer>

</body>
</html>
