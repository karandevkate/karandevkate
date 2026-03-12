<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Karan Devkate — GitHub README</title>
<link href="https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@300;400;600;700&family=Syne:wght@400;600;800&display=swap" rel="stylesheet"/>
<style>
  :root {
    --bg:       #0a0c0f;
    --surface:  #0f1318;
    --panel:    #141920;
    --border:   #1e2730;
    --amber:    #f5a623;
    --green:    #3ddc84;
    --cyan:     #47d4e8;
    --red:      #ff5f56;
    --muted:    #4a5568;
    --text:     #cdd6e0;
    --bright:   #eaf2fb;
  }

  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'JetBrains Mono', monospace;
    font-size: 14px;
    line-height: 1.7;
    min-height: 100vh;
    overflow-x: hidden;
  }

  /* ── GRID BACKGROUND ── */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background-image:
      linear-gradient(rgba(245,166,35,.04) 1px, transparent 1px),
      linear-gradient(90deg, rgba(245,166,35,.04) 1px, transparent 1px);
    background-size: 40px 40px;
    pointer-events: none;
    z-index: 0;
  }

  .wrapper {
    position: relative;
    z-index: 1;
    max-width: 860px;
    margin: 0 auto;
    padding: 60px 24px 100px;
  }

  /* ── TERMINAL HEADER ── */
  .terminal-bar {
    display: flex;
    align-items: center;
    gap: 8px;
    background: var(--panel);
    border: 1px solid var(--border);
    border-bottom: none;
    border-radius: 10px 10px 0 0;
    padding: 12px 18px;
  }
  .dot { width: 12px; height: 12px; border-radius: 50%; }
  .dot-r { background: var(--red); }
  .dot-y { background: var(--amber); }
  .dot-g { background: var(--green); }
  .terminal-title {
    margin-left: 12px;
    font-size: 12px;
    color: var(--muted);
    letter-spacing: .08em;
  }

  .card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 0 0 10px 10px;
    padding: 48px 44px;
    animation: fadeUp .6s ease both;
  }

  /* ── HERO ── */
  .hero { margin-bottom: 56px; }

  .prompt {
    display: inline-block;
    color: var(--amber);
    font-size: 12px;
    letter-spacing: .12em;
    margin-bottom: 14px;
    opacity: 0;
    animation: fadeUp .5s ease .1s both;
  }
  .prompt::before { content: '> '; color: var(--green); }

  .name {
    font-family: 'Syne', sans-serif;
    font-size: clamp(2rem, 5vw, 3.6rem);
    font-weight: 800;
    color: var(--bright);
    line-height: 1.1;
    letter-spacing: -.02em;
    opacity: 0;
    animation: fadeUp .5s ease .2s both;
  }

  .name span {
    color: var(--amber);
    position: relative;
  }
  .name span::after {
    content: '';
    position: absolute;
    left: 0; bottom: 2px;
    width: 100%; height: 3px;
    background: var(--amber);
    transform: scaleX(0);
    transform-origin: left;
    animation: underlineIn .5s ease .8s both;
  }

  .tagline {
    margin-top: 16px;
    font-size: 13px;
    color: var(--cyan);
    letter-spacing: .06em;
    opacity: 0;
    animation: fadeUp .5s ease .35s both;
  }
  .tagline::before { content: '// '; color: var(--muted); }

  .badges {
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
    margin-top: 24px;
    opacity: 0;
    animation: fadeUp .5s ease .5s both;
  }
  .badge {
    display: inline-flex;
    align-items: center;
    gap: 6px;
    padding: 5px 12px;
    border-radius: 4px;
    font-size: 11px;
    font-weight: 600;
    letter-spacing: .06em;
    border: 1px solid;
    transition: transform .2s, box-shadow .2s;
  }
  .badge:hover { transform: translateY(-2px); box-shadow: 0 4px 16px rgba(0,0,0,.4); }
  .badge-amber  { border-color: var(--amber); color: var(--amber); background: rgba(245,166,35,.08); }
  .badge-green  { border-color: var(--green); color: var(--green); background: rgba(61,220,132,.08); }
  .badge-cyan   { border-color: var(--cyan);  color: var(--cyan);  background: rgba(71,212,232,.08); }
  .badge-muted  { border-color: var(--border); color: var(--muted); background: rgba(255,255,255,.03); }

  /* ── SECTION ── */
  .section { margin-bottom: 52px; opacity: 0; animation: fadeUp .5s ease both; }
  .section:nth-child(2) { animation-delay: .15s }
  .section:nth-child(3) { animation-delay: .25s }
  .section:nth-child(4) { animation-delay: .35s }
  .section:nth-child(5) { animation-delay: .45s }
  .section:nth-child(6) { animation-delay: .55s }

  .section-label {
    display: flex;
    align-items: center;
    gap: 12px;
    font-family: 'Syne', sans-serif;
    font-size: 11px;
    font-weight: 600;
    letter-spacing: .16em;
    text-transform: uppercase;
    color: var(--amber);
    margin-bottom: 20px;
  }
  .section-label::after {
    content: '';
    flex: 1;
    height: 1px;
    background: linear-gradient(90deg, var(--border), transparent);
  }

  /* ── ABOUT GRID ── */
  .about-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 16px;
  }
  @media (max-width: 580px) { .about-grid { grid-template-columns: 1fr; } }

  .about-panel {
    background: var(--panel);
    border: 1px solid var(--border);
    border-radius: 8px;
    padding: 20px;
    transition: border-color .25s;
  }
  .about-panel:hover { border-color: var(--amber); }

  .about-panel h4 {
    font-family: 'Syne', sans-serif;
    font-size: 13px;
    font-weight: 600;
    color: var(--bright);
    margin-bottom: 12px;
    letter-spacing: .04em;
  }

  .about-panel li {
    list-style: none;
    padding: 3px 0;
    font-size: 12.5px;
    color: var(--text);
    display: flex;
    gap: 8px;
  }
  .about-panel li::before { content: '▸'; color: var(--green); flex-shrink: 0; }

  /* ── TECH TABLE ── */
  .tech-table { width: 100%; border-collapse: collapse; }
  .tech-table th, .tech-table td {
    padding: 10px 14px;
    text-align: left;
    font-size: 12.5px;
    border-bottom: 1px solid var(--border);
  }
  .tech-table th {
    color: var(--amber);
    font-weight: 600;
    letter-spacing: .06em;
    font-size: 11px;
    text-transform: uppercase;
    background: var(--panel);
  }
  .tech-table tr:hover td { background: rgba(245,166,35,.04); }
  .tech-table td:first-child {
    color: var(--cyan);
    white-space: nowrap;
    font-weight: 600;
    width: 170px;
  }
  .tech-table td:last-child { color: var(--text); line-height: 1.9; }

  /* ── PROJECT CARDS ── */
  .projects { display: flex; flex-direction: column; gap: 16px; }

  .proj-card {
    background: var(--panel);
    border: 1px solid var(--border);
    border-radius: 8px;
    padding: 24px;
    position: relative;
    overflow: hidden;
    transition: border-color .25s, transform .25s, box-shadow .25s;
    cursor: default;
  }
  .proj-card::before {
    content: '';
    position: absolute;
    top: 0; left: 0;
    width: 3px; height: 100%;
    background: var(--accent-color, var(--amber));
    border-radius: 3px 0 0 3px;
    transform: scaleY(0);
    transition: transform .3s ease;
  }
  .proj-card:hover { transform: translateX(4px); box-shadow: -4px 0 24px rgba(0,0,0,.3); }
  .proj-card:hover::before { transform: scaleY(1); }
  .proj-card:hover { border-color: var(--accent-color, var(--amber)); }

  .proj-card.c1 { --accent-color: var(--amber); }
  .proj-card.c2 { --accent-color: var(--cyan); }
  .proj-card.c3 { --accent-color: #c084fc; }

  .proj-top { display: flex; justify-content: space-between; align-items: flex-start; gap: 16px; flex-wrap: wrap; }

  .proj-title {
    font-family: 'Syne', sans-serif;
    font-size: 16px;
    font-weight: 700;
    color: var(--bright);
    margin-bottom: 4px;
  }

  .proj-sub {
    font-size: 11px;
    color: var(--muted);
    letter-spacing: .06em;
  }

  .proj-tags { display: flex; flex-wrap: wrap; gap: 6px; margin-top: 14px; }
  .tag {
    font-size: 11px;
    padding: 3px 10px;
    border-radius: 3px;
    border: 1px solid var(--border);
    color: var(--muted);
    font-weight: 600;
    letter-spacing: .04em;
    transition: border-color .2s, color .2s;
  }
  .proj-card:hover .tag { border-color: var(--accent-color, var(--amber)); color: var(--accent-color, var(--amber)); }

  .proj-desc {
    margin-top: 12px;
    font-size: 12.5px;
    color: var(--text);
    line-height: 1.7;
  }

  .proj-feats {
    margin-top: 12px;
    display: flex;
    flex-wrap: wrap;
    gap: 8px 20px;
  }
  .proj-feats span {
    font-size: 12px;
    color: var(--muted);
  }
  .proj-feats span::before { content: '✓ '; color: var(--green); }

  /* ── LEARNING TABLE ── */
  .learn-table { width: 100%; border-collapse: collapse; }
  .learn-table th, .learn-table td {
    padding: 10px 14px;
    font-size: 12.5px;
    border-bottom: 1px solid var(--border);
    text-align: left;
  }
  .learn-table th { background: var(--panel); color: var(--amber); font-size: 11px; letter-spacing: .1em; text-transform: uppercase; }
  .learn-table td:first-child { color: var(--text); }
  .learn-table td:last-child { color: var(--green); font-weight: 600; letter-spacing: .06em; }

  /* ── CONNECT ── */
  .connect-row {
    display: flex;
    gap: 12px;
    flex-wrap: wrap;
  }
  .connect-btn {
    display: inline-flex;
    align-items: center;
    gap: 8px;
    padding: 10px 20px;
    border-radius: 6px;
    font-size: 12px;
    font-weight: 700;
    letter-spacing: .07em;
    text-decoration: none;
    border: 1px solid;
    transition: background .2s, color .2s, transform .2s;
  }
  .connect-btn:hover { transform: translateY(-2px); }
  .btn-linkedin { border-color: #0a66c2; color: #0a66c2; background: rgba(10,102,194,.08); }
  .btn-linkedin:hover { background: rgba(10,102,194,.2); }
  .btn-gmail { border-color: #ea4335; color: #ea4335; background: rgba(234,67,53,.08); }
  .btn-gmail:hover { background: rgba(234,67,53,.2); }
  .btn-github { border-color: var(--muted); color: var(--text); background: rgba(255,255,255,.04); }
  .btn-github:hover { border-color: var(--bright); color: var(--bright); }

  /* ── FOOTER ── */
  .footer {
    margin-top: 48px;
    padding-top: 24px;
    border-top: 1px solid var(--border);
    display: flex;
    justify-content: space-between;
    align-items: center;
    flex-wrap: gap;
    font-size: 11px;
    color: var(--muted);
    letter-spacing: .06em;
  }
  .cursor {
    display: inline-block;
    width: 8px; height: 14px;
    background: var(--amber);
    border-radius: 1px;
    animation: blink 1s step-end infinite;
    vertical-align: middle;
    margin-left: 2px;
  }

  /* ── KEYFRAMES ── */
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(18px); }
    to   { opacity: 1; transform: translateY(0); }
  }
  @keyframes underlineIn {
    to { transform: scaleX(1); }
  }
  @keyframes blink {
    0%, 100% { opacity: 1; }
    50%       { opacity: 0; }
  }
</style>
</head>
<body>
<div class="wrapper">

  <!-- Terminal chrome -->
  <div class="terminal-bar">
    <div class="dot dot-r"></div>
    <div class="dot dot-y"></div>
    <div class="dot dot-g"></div>
    <span class="terminal-title">~/github/karandevkate/README.md</span>
  </div>

  <div class="card">

    <!-- ── HERO ── -->
    <div class="hero">
      <div class="prompt">software engineer · pune, india</div>
      <h1 class="name">Karan <span>Devkate</span></h1>
      <p class="tagline">Java Backend &amp; Full-Stack Developer · Microservices · Cloud-Native</p>
      <div class="badges">
        <span class="badge badge-amber">Java 17+</span>
        <span class="badge badge-green">Spring Boot 3.x</span>
        <span class="badge badge-cyan">Microservices</span>
        <span class="badge badge-amber">AWS</span>
        <span class="badge badge-green">React</span>
        <span class="badge badge-cyan">Docker</span>
        <span class="badge badge-muted">Apache Kafka</span>
        <span class="badge badge-muted">PostgreSQL</span>
      </div>
    </div>

    <!-- ── ABOUT ── -->
    <div class="section">
      <div class="section-label">About</div>
      <div class="about-grid">
        <div class="about-panel">
          <h4>💼 What I Do</h4>
          <ul>
            <li>Software Engineer at <strong>First Quad Tech Solutions</strong></li>
            <li>Enterprise-grade microservices &amp; APIs</li>
            <li>Scalable distributed systems</li>
            <li>Cloud-native architecture on AWS</li>
            <li>Full-stack with modern UI frameworks</li>
          </ul>
        </div>
        <div class="about-panel">
          <h4>🎯 My Focus</h4>
          <ul>
            <li>Security: RBAC, JWT, Resilience4j</li>
            <li>Unit &amp; integration testing (JUnit, Mockito)</li>
            <li>Swagger / OpenAPI documentation</li>
            <li>Agile / Scrum &amp; clean code principles</li>
            <li>Performance optimization at scale</li>
          </ul>
        </div>
      </div>
    </div>

    <!-- ── TECH STACK ── -->
    <div class="section">
      <div class="section-label">Tech Stack</div>
      <table class="tech-table">
        <thead>
          <tr><th>Category</th><th>Technologies</th></tr>
        </thead>
        <tbody>
          <tr><td>Backend &amp; Core</td><td>Java 8/17 · Spring Boot · Spring WebFlux · RESTful APIs · Microservices · Apache Kafka · Eureka · Resilience4j</td></tr>
          <tr><td>Frontend &amp; UI</td><td>React.js · Next.js · JavaScript / TypeScript · Bootstrap · HTML5 / CSS3 · jQuery · Ajax</td></tr>
          <tr><td>Databases</td><td>PostgreSQL · MySQL · MongoDB · Redis</td></tr>
          <tr><td>Cloud &amp; DevOps</td><td>AWS EC2 · AWS RDS · Docker · Kubernetes basics · Git · CI/CD</td></tr>
          <tr><td>Tools &amp; Practices</td><td>Postman · Swagger/OpenAPI · PlantUML · Agile/Scrum · JUnit · Mockito</td></tr>
        </tbody>
      </table>
    </div>

    <!-- ── PROJECTS ── -->
    <div class="section">
      <div class="section-label">Featured Projects</div>
      <div class="projects">

        <div class="proj-card c1">
          <div class="proj-top">
            <div>
              <div class="proj-title">🏢 Society Maintenance System</div>
              <div class="proj-sub">Full-Stack · Java · Spring Boot · PostgreSQL · Next.js</div>
            </div>
          </div>
          <p class="proj-desc">Complete housing society management platform with advanced features and a seamless user experience across all roles.</p>
          <div class="proj-tags">
            <span class="tag">Java</span><span class="tag">Spring Boot</span><span class="tag">PostgreSQL</span><span class="tag">Next.js</span>
          </div>
          <div class="proj-feats">
            <span>Role-based access control (RBAC)</span>
            <span>Interactive dashboards &amp; real-time notifications</span>
            <span>Modular, clean architecture</span>
          </div>
        </div>

        <div class="proj-card c2">
          <div class="proj-top">
            <div>
              <div class="proj-title">⭐ Company Rating &amp; Review Platform</div>
              <div class="proj-sub">Microservices · Spring Boot · React · Eureka · WebClient</div>
            </div>
          </div>
          <p class="proj-desc">Scalable review system featuring service discovery, resilient inter-service communication, and circuit-breaker patterns.</p>
          <div class="proj-tags">
            <span class="tag">Microservices</span><span class="tag">Spring Boot</span><span class="tag">React</span><span class="tag">Eureka</span>
          </div>
          <div class="proj-feats">
            <span>Service discovery &amp; inter-service communication</span>
            <span>Circuit breakers &amp; resilient APIs</span>
            <span>Swagger docs &amp; modern frontend</span>
          </div>
        </div>

        <div class="proj-card c3">
          <div class="proj-top">
            <div>
              <div class="proj-title">🎓 Online Examination Portal</div>
              <div class="proj-sub">Java · Spring Boot · Bootstrap · Ajax</div>
            </div>
          </div>
          <p class="proj-desc">Secure exam platform with a dynamic question bank, timed exams, and real-time result calculation.</p>
          <div class="proj-tags">
            <span class="tag">Java</span><span class="tag">Spring Boot</span><span class="tag">Bootstrap</span><span class="tag">Ajax</span>
          </div>
          <div class="proj-feats">
            <span>Dynamic question bank &amp; timed exams</span>
            <span>Real-time result calculation</span>
            <span>Clean CRUD APIs + intuitive UI</span>
          </div>
        </div>

      </div>
    </div>

    <!-- ── LEARNING ── -->
  <!--  <div class="section">
      <div class="section-label">Currently Exploring</div>
      <table class="learn-table">
        <thead><tr><th>Topic</th><th>Status</th></tr></thead>
        <tbody>
          <tr><td>Kubernetes &amp; container orchestration</td><td>LEARNING</td></tr>
          <tr><td>Advanced Kafka patterns &amp; event-driven architecture</td><td>LEARNING</td></tr>
          <tr><td>Reactive programming with Project Reactor</td><td>LEARNING</td></tr>
          <tr><td>OpenTelemetry &amp; observability stack</td><td>EXPLORING</td></tr>
          <tr><td>System design &amp; low-level design interviews</td><td>PREPARING</td></tr>
        </tbody>
      </table>
    </div>── -->

    <!-- ── CONNECT ── -->
    <div class="section">
      <div class="section-label">Let's Connect</div>
      <div class="connect-row">
        <a class="connect-btn btn-linkedin" href="https://www.linkedin.com/in/karandevkate/" target="_blank">
          <svg width="14" height="14" viewBox="0 0 24 24" fill="currentColor"><path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433c-1.144 0-2.063-.926-2.063-2.065 0-1.138.92-2.063 2.063-2.063 1.14 0 2.064.925 2.064 2.063 0 1.139-.925 2.065-2.064 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/></svg>
          LinkedIn
        </a>
        <a class="connect-btn btn-gmail" href="mailto:karandevkate225@gmail.com">
          <svg width="14" height="14" viewBox="0 0 24 24" fill="currentColor"><path d="M24 5.457v13.909c0 .904-.732 1.636-1.636 1.636h-3.819V11.73L12 16.64l-6.545-4.91v9.273H1.636A1.636 1.636 0 0 1 0 19.366V5.457c0-2.023 2.309-3.178 3.927-1.964L5.455 4.64 12 9.548l6.545-4.907 1.528-1.148C21.69 2.28 24 3.434 24 5.457z"/></svg>
          Gmail
        </a>
        <a class="connect-btn btn-github" href="https://github.com/karandevkate" target="_blank">
          <svg width="14" height="14" viewBox="0 0 24 24" fill="currentColor"><path d="M12 .297c-6.63 0-12 5.373-12 12 0 5.303 3.438 9.8 8.205 11.385.6.113.82-.258.82-.577 0-.285-.01-1.04-.015-2.04-3.338.724-4.042-1.61-4.042-1.61C4.422 18.07 3.633 17.7 3.633 17.7c-1.087-.744.084-.729.084-.729 1.205.084 1.838 1.236 1.838 1.236 1.07 1.835 2.809 1.305 3.495.998.108-.776.417-1.305.76-1.605-2.665-.3-5.466-1.332-5.466-5.93 0-1.31.465-2.38 1.235-3.22-.135-.303-.54-1.523.105-3.176 0 0 1.005-.322 3.3 1.23.96-.267 1.98-.399 3-.405 1.02.006 2.04.138 3 .405 2.28-1.552 3.285-1.23 3.285-1.23.645 1.653.24 2.873.12 3.176.765.84 1.23 1.91 1.23 3.22 0 4.61-2.805 5.625-5.475 5.92.42.36.81 1.096.81 2.22 0 1.606-.015 2.896-.015 3.286 0 .315.21.69.825.57C20.565 22.092 24 17.592 24 12.297c0-6.627-5.373-12-12-12"/></svg>
          GitHub
        </a>
      </div>
    </div>

    <!-- ── FOOTER ── -->
    <div class="footer">
      <span>⭐ Drop a star on repos you find useful!</span>
      <span>@mrkarandevkate<span class="cursor"></span></span>
    </div>

  </div><!-- /card -->
</div><!-- /wrapper -->
</body>
</html>
