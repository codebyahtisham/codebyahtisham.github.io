<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Ahtisham Saleem — AI Research Engineer & Electrical Engineer</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link href="https://fonts.googleapis.com/css2?family=Outfit:wght@300;400;500;600;700;800&family=JetBrains+Mono:wght@400;500&display=swap" rel="stylesheet">
    <style>
        *, *::before, *::after { margin: 0; padding: 0; box-sizing: border-box; }

        :root {
            --bg-primary: #0a0a0f;
            --bg-secondary: #12121a;
            --bg-card: #181824;
            --bg-card-hover: #1e1e2e;
            --accent: #00d4aa;
            --accent-dim: rgba(0, 212, 170, 0.15);
            --accent-glow: rgba(0, 212, 170, 0.3);
            --text-primary: #e8e8ef;
            --text-secondary: #8888a0;
            --text-muted: #55556a;
            --border: #2a2a3a;
            --font-body: 'Outfit', sans-serif;
            --font-mono: 'JetBrains Mono', monospace;
        }

        html { scroll-behavior: smooth; }

        body {
            font-family: var(--font-body);
            background: var(--bg-primary);
            color: var(--text-primary);
            line-height: 1.7;
            overflow-x: hidden;
        }

        /* ─── NAV ─── */
        nav {
            position: fixed; top: 0; left: 0; right: 0; z-index: 1000;
            background: rgba(10, 10, 15, 0.85);
            backdrop-filter: blur(20px);
            border-bottom: 1px solid var(--border);
            transition: all 0.3s ease;
        }
        nav.scrolled { background: rgba(10, 10, 15, 0.95); }
        .nav-inner {
            max-width: 1200px; margin: 0 auto;
            display: flex; justify-content: space-between; align-items: center;
            padding: 1rem 2rem;
        }
        .nav-logo {
            font-weight: 700; font-size: 1.2rem;
            color: var(--accent); text-decoration: none;
            font-family: var(--font-mono);
        }
        .nav-links { display: flex; gap: 2rem; list-style: none; }
        .nav-links a {
            color: var(--text-secondary); text-decoration: none;
            font-size: 0.9rem; font-weight: 500;
            transition: color 0.3s; position: relative;
        }
        .nav-links a:hover, .nav-links a.active { color: var(--accent); }
        .nav-links a.active::after {
            content: ''; position: absolute; bottom: -6px; left: 0; right: 0;
            height: 2px; background: var(--accent); border-radius: 1px;
        }
        .hamburger { display: none; cursor: pointer; flex-direction: column; gap: 5px; }
        .hamburger span { width: 24px; height: 2px; background: var(--text-primary); transition: 0.3s; }

        /* ─── PAGE SECTIONS ─── */
        .page { display: none; min-height: 100vh; padding-top: 80px; }
        .page.active { display: block; }

        .container { max-width: 1100px; margin: 0 auto; padding: 0 2rem; }

        /* ─── HERO ─── */
        .hero {
            min-height: calc(100vh - 80px);
            display: flex; align-items: center;
            position: relative;
        }
        .hero-bg {
            position: absolute; top: 0; left: 0; right: 0; bottom: 0;
            background:
                radial-gradient(ellipse 600px 400px at 20% 50%, rgba(0, 212, 170, 0.06), transparent),
                radial-gradient(ellipse 500px 300px at 80% 30%, rgba(100, 100, 255, 0.04), transparent);
            pointer-events: none;
        }
        .hero-content { position: relative; z-index: 1; }
        .hero-label {
            font-family: var(--font-mono); font-size: 0.85rem;
            color: var(--accent); margin-bottom: 1.5rem;
            display: flex; align-items: center; gap: 0.75rem;
        }
        .hero-label::before {
            content: ''; width: 40px; height: 1px; background: var(--accent);
        }
        .hero h1 {
            font-size: clamp(2.5rem, 6vw, 4.5rem);
            font-weight: 800; line-height: 1.1;
            margin-bottom: 1.5rem;
        }
        .hero h1 .highlight { color: var(--accent); }
        .hero-desc {
            font-size: 1.15rem; color: var(--text-secondary);
            max-width: 600px; margin-bottom: 2.5rem; line-height: 1.8;
        }
        .hero-links { display: flex; gap: 1rem; flex-wrap: wrap; }
        .btn {
            display: inline-flex; align-items: center; gap: 0.5rem;
            padding: 0.75rem 1.75rem; border-radius: 6px;
            font-family: var(--font-body); font-size: 0.9rem; font-weight: 600;
            text-decoration: none; transition: all 0.3s; cursor: pointer; border: none;
        }
        .btn-primary {
            background: var(--accent); color: var(--bg-primary);
        }
        .btn-primary:hover { box-shadow: 0 0 30px var(--accent-glow); transform: translateY(-2px); }
        .btn-outline {
            background: transparent; color: var(--text-primary);
            border: 1px solid var(--border);
        }
        .btn-outline:hover { border-color: var(--accent); color: var(--accent); }

        .scroll-indicator {
            position: absolute; bottom: 2rem; left: 50%;
            transform: translateX(-50%); color: var(--text-muted);
            font-size: 0.8rem; text-align: center;
            animation: float 2s ease-in-out infinite;
        }
        @keyframes float { 0%, 100% { transform: translateX(-50%) translateY(0); } 50% { transform: translateX(-50%) translateY(8px); } }

        /* ─── SECTION HEADERS ─── */
        .section { padding: 5rem 0; }
        .section-label {
            font-family: var(--font-mono); font-size: 0.8rem;
            color: var(--accent); text-transform: uppercase;
            letter-spacing: 2px; margin-bottom: 0.75rem;
        }
        .section-title {
            font-size: 2.2rem; font-weight: 700; margin-bottom: 1rem;
        }
        .section-desc {
            color: var(--text-secondary); font-size: 1rem;
            max-width: 600px; margin-bottom: 3rem;
        }

        /* ─── ABOUT PAGE ─── */
        .about-grid {
            display: grid; grid-template-columns: 1fr 1fr;
            gap: 4rem; align-items: start;
        }
        .about-text p {
            color: var(--text-secondary); margin-bottom: 1.5rem;
            font-size: 1rem;
        }
        .about-text strong { color: var(--text-primary); }
        .about-stats {
            display: grid; grid-template-columns: 1fr 1fr;
            gap: 1.5rem;
        }
        .stat-card {
            background: var(--bg-card); border: 1px solid var(--border);
            border-radius: 12px; padding: 1.5rem;
            transition: all 0.3s;
        }
        .stat-card:hover { border-color: var(--accent); transform: translateY(-3px); }
        .stat-number {
            font-size: 2rem; font-weight: 800; color: var(--accent);
            font-family: var(--font-mono);
        }
        .stat-label { color: var(--text-secondary); font-size: 0.85rem; margin-top: 0.25rem; }

        /* ─── SKILLS ─── */
        .skills-grid {
            display: grid; grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
            gap: 1.5rem;
        }
        .skill-category {
            background: var(--bg-card); border: 1px solid var(--border);
            border-radius: 12px; padding: 2rem;
            transition: all 0.3s;
        }
        .skill-category:hover { border-color: var(--accent); }
        .skill-category h3 {
            font-size: 1rem; font-weight: 600;
            margin-bottom: 1rem; color: var(--accent);
        }
        .skill-tags { display: flex; flex-wrap: wrap; gap: 0.5rem; }
        .skill-tag {
            background: var(--accent-dim); color: var(--accent);
            padding: 0.35rem 0.85rem; border-radius: 20px;
            font-size: 0.78rem; font-family: var(--font-mono);
        }

        /* ─── PROJECTS PAGE ─── */
        .project-filters {
            display: flex; gap: 0.75rem; flex-wrap: wrap;
            margin-bottom: 2.5rem;
        }
        .filter-btn {
            background: var(--bg-card); border: 1px solid var(--border);
            color: var(--text-secondary); padding: 0.5rem 1.25rem;
            border-radius: 20px; cursor: pointer;
            font-family: var(--font-body); font-size: 0.85rem;
            transition: all 0.3s;
        }
        .filter-btn:hover, .filter-btn.active {
            background: var(--accent-dim); border-color: var(--accent);
            color: var(--accent);
        }

        .projects-grid {
            display: grid; grid-template-columns: repeat(auto-fill, minmax(340px, 1fr));
            gap: 1.5rem;
        }
        .project-card {
            background: var(--bg-card); border: 1px solid var(--border);
            border-radius: 12px; padding: 2rem;
            transition: all 0.4s; position: relative; overflow: hidden;
        }
        .project-card:hover {
            border-color: var(--accent); transform: translateY(-4px);
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.3);
        }
        .project-card.pinned { border-color: rgba(0, 212, 170, 0.3); }
        .project-card.pinned::before {
            content: '★ PINNED'; position: absolute; top: 1rem; right: 1rem;
            font-family: var(--font-mono); font-size: 0.65rem;
            color: var(--accent); background: var(--accent-dim);
            padding: 0.2rem 0.6rem; border-radius: 4px;
        }
        .project-number {
            font-family: var(--font-mono); font-size: 0.75rem;
            color: var(--text-muted); margin-bottom: 0.75rem;
        }
        .project-card h3 {
            font-size: 1.1rem; font-weight: 600;
            margin-bottom: 0.75rem; line-height: 1.4;
        }
        .project-card p {
            color: var(--text-secondary); font-size: 0.88rem;
            margin-bottom: 1.25rem; line-height: 1.7;
        }
        .project-meta {
            display: flex; justify-content: space-between;
            align-items: center; flex-wrap: wrap; gap: 0.75rem;
        }
        .project-tags { display: flex; flex-wrap: wrap; gap: 0.4rem; }
        .project-tag {
            font-family: var(--font-mono); font-size: 0.7rem;
            color: var(--text-muted); background: rgba(255,255,255,0.04);
            padding: 0.2rem 0.6rem; border-radius: 4px;
        }
        .project-link {
            color: var(--accent); font-size: 0.85rem;
            text-decoration: none; font-weight: 500;
            display: flex; align-items: center; gap: 0.3rem;
        }
        .project-link:hover { text-decoration: underline; }

        /* ─── CONTACT PAGE ─── */
        .contact-grid {
            display: grid; grid-template-columns: 1fr 1fr;
            gap: 4rem; align-items: start;
        }
        .contact-text h2 { font-size: 2.5rem; font-weight: 800; margin-bottom: 1.5rem; }
        .contact-text p { color: var(--text-secondary); margin-bottom: 2rem; font-size: 1.05rem; }
        .contact-links { display: flex; flex-direction: column; gap: 1rem; }
        .contact-item {
            display: flex; align-items: center; gap: 1rem;
            padding: 1.25rem 1.5rem;
            background: var(--bg-card); border: 1px solid var(--border);
            border-radius: 12px; text-decoration: none;
            color: var(--text-primary); transition: all 0.3s;
        }
        .contact-item:hover { border-color: var(--accent); transform: translateX(8px); }
        .contact-icon {
            width: 44px; height: 44px; border-radius: 10px;
            background: var(--accent-dim); display: flex;
            align-items: center; justify-content: center;
            font-size: 1.2rem; flex-shrink: 0;
        }
        .contact-item-label { font-size: 0.8rem; color: var(--text-muted); }
        .contact-item-value { font-weight: 500; font-size: 0.95rem; }

        .contact-quote {
            background: var(--bg-card); border: 1px solid var(--border);
            border-left: 3px solid var(--accent);
            border-radius: 0 12px 12px 0; padding: 2rem;
            margin-top: 2rem;
        }
        .contact-quote p {
            font-style: italic; color: var(--text-secondary);
            font-size: 1.1rem; line-height: 1.8;
        }

        /* ─── FOOTER ─── */
        footer {
            border-top: 1px solid var(--border);
            padding: 2rem 0; text-align: center;
            color: var(--text-muted); font-size: 0.85rem;
        }

        /* ─── ANIMATIONS ─── */
        .fade-in {
            opacity: 0; transform: translateY(30px);
            transition: opacity 0.6s ease, transform 0.6s ease;
        }
        .fade-in.visible { opacity: 1; transform: translateY(0); }
        .stagger-1 { transition-delay: 0.1s; }
        .stagger-2 { transition-delay: 0.2s; }
        .stagger-3 { transition-delay: 0.3s; }
        .stagger-4 { transition-delay: 0.4s; }

        /* ─── RESPONSIVE ─── */
        @media (max-width: 768px) {
            .nav-links { display: none; position: absolute; top: 100%; left: 0; right: 0; background: var(--bg-secondary); flex-direction: column; padding: 1.5rem 2rem; gap: 1rem; border-bottom: 1px solid var(--border); }
            .nav-links.open { display: flex; }
            .hamburger { display: flex; }
            .hero h1 { font-size: 2.2rem; }
            .about-grid, .contact-grid { grid-template-columns: 1fr; gap: 2rem; }
            .projects-grid { grid-template-columns: 1fr; }
            .about-stats { grid-template-columns: 1fr 1fr; }
        }
    </style>
</head>
<body>

<!-- ─── NAV ─── -->
<nav id="navbar">
    <div class="nav-inner">
        <a href="#" class="nav-logo" onclick="showPage('home')">AS.</a>
        <ul class="nav-links" id="navLinks">
            <li><a href="#" onclick="showPage('home')" class="active" data-page="home">Home</a></li>
            <li><a href="#" onclick="showPage('projects')" data-page="projects">Projects</a></li>
            <li><a href="#" onclick="showPage('about')" data-page="about">About</a></li>
            <li><a href="#" onclick="showPage('contact')" data-page="contact">Contact</a></li>
        </ul>
        <div class="hamburger" onclick="toggleMenu()">
            <span></span><span></span><span></span>
        </div>
    </div>
</nav>

<!-- ═══════════════ HOME PAGE ═══════════════ -->
<div id="page-home" class="page active">

    <div class="hero">
        <div class="hero-bg"></div>
        <div class="container hero-content">
            <div class="hero-label fade-in">AI Research Engineer & Electrical Engineer</div>
            <h1 class="fade-in stagger-1">Ahtisham<br><span class="highlight">Saleem</span></h1>
            <p class="hero-desc fade-in stagger-2">Building intelligent systems at the intersection of hardware and machine learning — from brain-computer interfaces to cloud-deployed AI, I engineer solutions that think, sense, and adapt.</p>
            <div class="hero-links fade-in stagger-3">
                <a href="#" class="btn btn-primary" onclick="showPage('projects')">View Projects →</a>
                <a href="https://www.linkedin.com/in/ahtisham-salim" target="_blank" class="btn btn-outline">LinkedIn</a>
                <a href="https://github.com/codebyahtisham" target="_blank" class="btn btn-outline">GitHub</a>
            </div>
        </div>
        <div class="scroll-indicator">scroll ↓</div>
    </div>

    <!-- Skills Preview -->
    <div class="section container">
        <div class="section-label fade-in">Expertise</div>
        <h2 class="section-title fade-in">Tech Stack</h2>
        <div class="skills-grid">
            <div class="skill-category fade-in">
                <h3>Machine Learning & AI</h3>
                <div class="skill-tags">
                    <span class="skill-tag">Python</span>
                    <span class="skill-tag">TensorFlow</span>
                    <span class="skill-tag">PyTorch</span>
                    <span class="skill-tag">scikit-learn</span>
                    <span class="skill-tag">XGBoost</span>
                    <span class="skill-tag">OpenCV</span>
                    <span class="skill-tag">Streamlit</span>
                </div>
            </div>
            <div class="skill-category fade-in stagger-1">
                <h3>Hardware & Embedded</h3>
                <div class="skill-tags">
                    <span class="skill-tag">Verilog</span>
                    <span class="skill-tag">MATLAB</span>
                    <span class="skill-tag">Simulink</span>
                    <span class="skill-tag">ATmega328P</span>
                    <span class="skill-tag">Proteus</span>
                    <span class="skill-tag">Ansys HFSS</span>
                </div>
            </div>
            <div class="skill-category fade-in stagger-2">
                <h3>Programming & Tools</h3>
                <div class="skill-tags">
                    <span class="skill-tag">C++</span>
                    <span class="skill-tag">C</span>
                    <span class="skill-tag">Git</span>
                    <span class="skill-tag">Linux</span>
                    <span class="skill-tag">Cisco Packet Tracer</span>
                    <span class="skill-tag">NumPy</span>
                    <span class="skill-tag">Pandas</span>
                </div>
            </div>
            <div class="skill-category fade-in stagger-3">
                <h3>Research Interests</h3>
                <div class="skill-tags">
                    <span class="skill-tag">BCI Systems</span>
                    <span class="skill-tag">EEG/EMG</span>
                    <span class="skill-tag">Edge AI</span>
                    <span class="skill-tag">MLOps</span>
                    <span class="skill-tag">Cloud-Edge Hybrid</span>
                </div>
            </div>
        </div>
    </div>
</div>

<!-- ═══════════════ PROJECTS PAGE ═══════════════ -->
<div id="page-projects" class="page">
    <div class="section container">
        <div class="section-label fade-in">Portfolio</div>
        <h2 class="section-title fade-in">Projects</h2>
        <p class="section-desc fade-in">13 university and research projects spanning ML, digital systems, control, RF, and networking.</p>

        <div class="project-filters fade-in">
            <button class="filter-btn active" onclick="filterProjects('all')">All</button>
            <button class="filter-btn" onclick="filterProjects('ml')">Machine Learning</button>
            <button class="filter-btn" onclick="filterProjects('hardware')">Hardware</button>
            <button class="filter-btn" onclick="filterProjects('software')">Software</button>
            <button class="filter-btn" onclick="filterProjects('simulation')">Simulation</button>
        </div>

        <div class="projects-grid" id="projectsGrid">

            <div class="project-card pinned fade-in" data-category="ml software">
                <div class="project-number">01 — Final Year Project</div>
                <h3>Cloud-Based Rice Classification System</h3>
                <p>Classifies 7 Pakistani rice varieties using 49 handcrafted features and XGBoost, deployed on Namal HPC Cloud via Streamlit. Built with Alkaram Rice Engineering (PVT) Ltd.</p>
                <div class="project-meta">
                    <div class="project-tags">
                        <span class="project-tag">Python</span>
                        <span class="project-tag">XGBoost</span>
                        <span class="project-tag">Streamlit</span>
                        <span class="project-tag">OpenCV</span>
                    </div>
                    <a href="https://github.com/codebyahtisham/-Cloud-Based-Rice-Classification-System-Pakistan" target="_blank" class="project-link">View →</a>
                </div>
            </div>

            <div class="project-card fade-in" data-category="hardware">
                <div class="project-number">02 — Computer Architecture</div>
                <h3>RISC-V Pipelined Processor (RV32I)</h3>
                <p>32-bit, 5-stage pipelined RISC-V processor in Verilog with data forwarding and hazard detection. All 47 baseline instructions verified via GTKWave.</p>
                <div class="project-meta">
                    <div class="project-tags">
                        <span class="project-tag">Verilog</span>
                        <span class="project-tag">RISC-V</span>
                        <span class="project-tag">GTKWave</span>
                    </div>
                    <a href="https://github.com/codebyahtisham/RISC-V-Pipelined-Processor-RV32I" target="_blank" class="project-link">View →</a>
                </div>
            </div>

            <div class="project-card fade-in" data-category="hardware simulation">
                <div class="project-number">03 — Control Systems</div>
                <h3>PID-Controlled Lego EV3 Robot</h3>
                <p>LEGO Mindstorms EV3 robot using closed-loop PID in MATLAB/Simulink. Encoder feedback synchronizes wheel speeds for straight-line driving.</p>
                <div class="project-meta">
                    <div class="project-tags">
                        <span class="project-tag">MATLAB</span>
                        <span class="project-tag">Simulink</span>
                        <span class="project-tag">PID</span>
                    </div>
                    <a href="https://github.com/codebyahtisham/PID-Controlled-Lego-EV3-Robot" target="_blank" class="project-link">View →</a>
                </div>
            </div>

            <div class="project-card fade-in" data-category="ml">
                <div class="project-number">04 — Machine Learning</div>
                <h3>Real vs AI-Generated Image Classification</h3>
                <p>Psychophysics experiments + SVM, MLP, CNN to classify real vs AI-generated images. Explores human perception vs machine accuracy.</p>
                <div class="project-meta">
                    <div class="project-tags">
                        <span class="project-tag">Python</span>
                        <span class="project-tag">CNN</span>
                        <span class="project-tag">SVM</span>
                    </div>
                    <a href="https://github.com/codebyahtisham/Real-vs-AI-Generated-Image-Classification" target="_blank" class="project-link">View →</a>
                </div>
            </div>

            <div class="project-card fade-in" data-category="simulation">
                <div class="project-number">05 — Wireless Communication</div>
                <h3>Microstrip Patch Antenna — 6.4 GHz</h3>
                <p>Patch antenna on Rogers 5880 substrate designed in Ansys HFSS, achieving –19.57 dB return loss with full E/H-field and gain analysis.</p>
                <div class="project-meta">
                    <div class="project-tags">
                        <span class="project-tag">HFSS</span>
                        <span class="project-tag">RF</span>
                        <span class="project-tag">Rogers 5880</span>
                    </div>
                    <a href="https://github.com/codebyahtisham/Microstrip-Patch-Antenna-6.4GHz-HFSS" target="_blank" class="project-link">View →</a>
                </div>
            </div>

            <div class="project-card fade-in" data-category="ml simulation">
                <div class="project-number">06 — Digital Image Processing</div>
                <h3>Image Noise Estimation & Removal</h3>
                <p>Automatic noise type detection and adaptive denoising in MATLAB. Identifies 5 noise types via statistical analysis and applies optimal filters.</p>
                <div class="project-meta">
                    <div class="project-tags">
                        <span class="project-tag">MATLAB</span>
                        <span class="project-tag">Filtering</span>
                    </div>
                    <a href="https://github.com/codebyahtisham/Image-Noise-Estimation-Removal-MATLAB" target="_blank" class="project-link">View →</a>
                </div>
            </div>

            <div class="project-card fade-in" data-category="simulation software">
                <div class="project-number">07 — Computer Networks</div>
                <h3>University Campus Network Subnetting</h3>
                <p>Campus-wide network for Namal University using VLSM subnetting from a single Class C block. Six /28 subnets with 5 routers in Cisco Packet Tracer.</p>
                <div class="project-meta">
                    <div class="project-tags">
                        <span class="project-tag">Cisco</span>
                        <span class="project-tag">VLSM</span>
                        <span class="project-tag">Routing</span>
                    </div>
                    <a href="https://github.com/codebyahtisham/University-Network-Design-Packet-Tracer" target="_blank" class="project-link">View →</a>
                </div>
            </div>

            <div class="project-card fade-in" data-category="hardware">
                <div class="project-number">08 — Electronic Devices</div>
                <h3>Automatic Dusk to Dawn Light</h3>
                <p>Automated lighting system using LDR and BJT that switches lights ON at dusk and OFF at dawn. Built in both Proteus simulation and on hardware.</p>
                <div class="project-meta">
                    <div class="project-tags">
                        <span class="project-tag">Proteus</span>
                        <span class="project-tag">LDR</span>
                        <span class="project-tag">BJT</span>
                    </div>
                    <a href="https://github.com/codebyahtisham/Automatic-Dusk-to-Dawn-Light" target="_blank" class="project-link">View →</a>
                </div>
            </div>

            <div class="project-card fade-in" data-category="hardware simulation">
                <div class="project-number">09 — Electronic Devices</div>
                <h3>DC-DC Boost Converter (MOSFET)</h3>
                <p>Switched-mode boost converter using IRFZ44N MOSFET, stepping up 12V to 48V at 75% duty cycle. Designed analytically and verified in Proteus.</p>
                <div class="project-meta">
                    <div class="project-tags">
                        <span class="project-tag">Proteus</span>
                        <span class="project-tag">IRFZ44N</span>
                        <span class="project-tag">SMPS</span>
                    </div>
                    <a href="https://github.com/codebyahtisham/DC-DC-Boost-Converter-Proteus" target="_blank" class="project-link">View →</a>
                </div>
            </div>

            <div class="project-card fade-in" data-category="hardware">
                <div class="project-number">10 — Microprocessors</div>
                <h3>DC Motor Control & Ultrasonic Sensing</h3>
                <p>2WD robot using ATmega328P with L293D motor driver and HC-SR04 ultrasonic sensor. Obstacle detection, motor control, LEDs, and buzzer alerts.</p>
                <div class="project-meta">
                    <div class="project-tags">
                        <span class="project-tag">ATmega328P</span>
                        <span class="project-tag">L293D</span>
                        <span class="project-tag">HC-SR04</span>
                    </div>
                    <a href="https://github.com/codebyahtisham/DC-Motor-Control-Ultrasonic-Sensing" target="_blank" class="project-link">View →</a>
                </div>
            </div>

            <div class="project-card fade-in" data-category="hardware">
                <div class="project-number">11 — Digital Logic Design</div>
                <h3>4-Bit ALU</h3>
                <p>4-bit Arithmetic Logic Unit built on the MCP M21-7000 trainer board using discrete ICs and simulated in Verilog via ModelSim. Performs 8 operations.</p>
                <div class="project-meta">
                    <div class="project-tags">
                        <span class="project-tag">Verilog</span>
                        <span class="project-tag">ModelSim</span>
                        <span class="project-tag">ICs</span>
                    </div>
                    <a href="https://github.com/codebyahtisham/4-Bit-ALU" target="_blank" class="project-link">View →</a>
                </div>
            </div>

            <div class="project-card fade-in" data-category="software">
                <div class="project-number">12 — Data Structures</div>
                <h3>Library Management System</h3>
                <p>Role-based library system in Python with CSV persistence. Supports Librarian and Student roles with book issue/return tracking and search.</p>
                <div class="project-meta">
                    <div class="project-tags">
                        <span class="project-tag">Python</span>
                        <span class="project-tag">CSV</span>
                        <span class="project-tag">DSA</span>
                    </div>
                    <a href="https://github.com/codebyahtisham/Library-Management-System" target="_blank" class="project-link">View →</a>
                </div>
            </div>

            <div class="project-card fade-in" data-category="software">
                <div class="project-number">13 — Programming Fundamentals</div>
                <h3>Car Parking Reservation System</h3>
                <p>Console-based parking management in C++ using OOP and file handling. Supports slot booking, cancellation, and persistent storage.</p>
                <div class="project-meta">
                    <div class="project-tags">
                        <span class="project-tag">C++</span>
                        <span class="project-tag">OOP</span>
                        <span class="project-tag">File I/O</span>
                    </div>
                    <a href="https://github.com/codebyahtisham/Car-Parking-Reservation-System" target="_blank" class="project-link">View →</a>
                </div>
            </div>

        </div>
    </div>
</div>

<!-- ═══════════════ ABOUT PAGE ═══════════════ -->
<div id="page-about" class="page">
    <div class="section container">
        <div class="section-label fade-in">Background</div>
        <h2 class="section-title fade-in">About Me</h2>

        <div class="about-grid">
            <div class="about-text fade-in">
                <p>I'm <strong>Ahtisham Saleem</strong>, a final-year Electrical Engineering student at <strong>Namal University, Mianwali</strong> and an AI Research Engineer at <strong>E-Intel, LCE (LUMS)</strong> — a deep-tech startup building Brain-Computer Interface systems that connect brain and body sensors with intelligent AI applications.</p>

                <p>My work at E-Intel involves designing <strong>ML pipelines for biosignal classification</strong> (EEG/EMG), developing Python scripts for hardware–software integration, and automating data collection, preprocessing, and model validation workflows. I operate at the boundary where AI research meets real-world embedded systems.</p>

                <p>Throughout my undergraduate journey, I've built projects across a wide spectrum — from a <strong>32-bit pipelined RISC-V processor</strong> in Verilog to a <strong>cloud-deployed rice classification system</strong> using XGBoost, from PID-controlled robots to microstrip antenna design. This range reflects my belief that the best engineers understand systems end-to-end.</p>

                <p>I'm currently exploring <strong>real-time ML inference on embedded devices</strong>, <strong>brain and biosignal decoding for BCI</strong>, and <strong>Cloud–Edge hybrid AI architectures</strong> — work that sits at the frontier of intelligent systems.</p>
            </div>

            <div class="about-stats fade-in stagger-2">
                <div class="stat-card">
                    <div class="stat-number">13+</div>
                    <div class="stat-label">University Projects</div>
                </div>
                <div class="stat-card">
                    <div class="stat-number">7+</div>
                    <div class="stat-label">Programming Languages</div>
                </div>
                <div class="stat-card">
                    <div class="stat-number">BCI</div>
                    <div class="stat-label">Current Research Domain</div>
                </div>
                <div class="stat-card">
                    <div class="stat-number">BSEE</div>
                    <div class="stat-label">Namal University '25</div>
                </div>
            </div>
        </div>
    </div>
</div>

<!-- ═══════════════ CONTACT PAGE ═══════════════ -->
<div id="page-contact" class="page">
    <div class="section container">
        <div class="contact-grid">
            <div class="contact-text fade-in">
                <div class="section-label">Get in Touch</div>
                <h2>Let's Connect</h2>
                <p>Whether it's a collaboration opportunity, research discussion, or just a conversation about engineering and AI — I'd love to hear from you.</p>

                <div class="contact-links">
                    <a href="mailto:engr.ahtishamsaleem@gmail.com" class="contact-item">
                        <div class="contact-icon">✉</div>
                        <div>
                            <div class="contact-item-label">Email</div>
                            <div class="contact-item-value">engr.ahtishamsaleem@gmail.com</div>
                        </div>
                    </a>
                    <a href="https://www.linkedin.com/in/ahtisham-salim" target="_blank" class="contact-item">
                        <div class="contact-icon">in</div>
                        <div>
                            <div class="contact-item-label">LinkedIn</div>
                            <div class="contact-item-value">linkedin.com/in/ahtisham-salim</div>
                        </div>
                    </a>
                    <a href="https://github.com/codebyahtisham" target="_blank" class="contact-item">
                        <div class="contact-icon">&lt;/&gt;</div>
                        <div>
                            <div class="contact-item-label">GitHub</div>
                            <div class="contact-item-value">github.com/codebyahtisham</div>
                        </div>
                    </a>
                </div>
            </div>

            <div class="fade-in stagger-2">
                <div class="contact-quote">
                    <p>"Merging hardware and intelligence — building systems that think, sense, and adapt."</p>
                </div>
            </div>
        </div>
    </div>
</div>

<!-- ─── FOOTER ─── -->
<footer>
    <div class="container">
        <p>© 2025 Ahtisham Saleem. Built with purpose.</p>
    </div>
</footer>

<script>
    // ─── PAGE NAVIGATION ───
    function showPage(page) {
        document.querySelectorAll('.page').forEach(p => p.classList.remove('active'));
        document.getElementById('page-' + page).classList.add('active');
        document.querySelectorAll('.nav-links a').forEach(a => a.classList.remove('active'));
        document.querySelector('[data-page="' + page + '"]').classList.add('active');
        window.scrollTo(0, 0);
        document.getElementById('navLinks').classList.remove('open');
        setTimeout(triggerAnimations, 100);
    }

    // ─── MOBILE MENU ───
    function toggleMenu() {
        document.getElementById('navLinks').classList.toggle('open');
    }

    // ─── NAV SCROLL EFFECT ───
    window.addEventListener('scroll', () => {
        document.getElementById('navbar').classList.toggle('scrolled', window.scrollY > 50);
    });

    // ─── PROJECT FILTER ───
    function filterProjects(category) {
        document.querySelectorAll('.filter-btn').forEach(b => b.classList.remove('active'));
        event.target.classList.add('active');
        document.querySelectorAll('.project-card').forEach(card => {
            if (category === 'all' || card.dataset.category.includes(category)) {
                card.style.display = 'block';
            } else {
                card.style.display = 'none';
            }
        });
    }

    // ─── SCROLL ANIMATIONS ───
    function triggerAnimations() {
        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.classList.add('visible');
                }
            });
        }, { threshold: 0.1 });
        document.querySelectorAll('.fade-in').forEach(el => {
            el.classList.remove('visible');
            observer.observe(el);
        });
    }
    triggerAnimations();
</script>

</body>
</html>
