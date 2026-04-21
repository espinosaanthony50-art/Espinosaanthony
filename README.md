<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Anthony Espinosa | Portfolio</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">
    <style>
        :root {
            --bg-dark: #0a0a0a;
            --bg-card: #141414;
            --text-main: #f5f5f5;
            --text-dim: #999999;
            --accent: #ffffff;
            --border: #222222;
            --nav-height: 70px;
            --transition: all 0.4s cubic-bezier(0.16, 1, 0.3, 1);
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            scroll-behavior: smooth;
        }

        body {
            font-family: 'Inter', -apple-system, system-ui, sans-serif;
            background-color: var(--bg-dark);
            color: var(--text-main);
            line-height: 1.7;
            -webkit-font-smoothing: antialiased;
        }

        /* --- HEADER & NAVIGATION --- */
        header {
            text-align: center;
            padding: 140px 20px 100px;
            background: radial-gradient(circle at top, #1a1a1a 0%, #0a0a0a 100%);
        }

        .main-title {
            font-size: clamp(2.5rem, 8vw, 4.5rem);
            font-weight: 900;
            letter-spacing: -2px;
            text-transform: uppercase;
            margin-bottom: 15px;
            background: linear-gradient(to bottom, #fff 40%, #555 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        nav {
            position: sticky;
            top: 0;
            background: rgba(10, 10, 10, 0.8);
            backdrop-filter: saturate(180%) blur(20px);
            border-bottom: 1px solid var(--border);
            z-index: 1000;
            display: flex;
            justify-content: center;
            padding: 0 15px;
            gap: 30px;
            height: var(--nav-height);
            align-items: center;
        }

        nav a {
            color: var(--text-dim);
            text-decoration: none;
            font-weight: 600;
            font-size: 0.8rem;
            text-transform: uppercase;
            letter-spacing: 1px;
            transition: var(--transition);
        }

        nav a:hover {
            color: var(--text-main);
        }

        /* --- BUTTONS --- */
        .btn-cv {
            display: inline-flex;
            align-items: center;
            gap: 10px;
            margin-top: 30px;
            padding: 14px 32px;
            background-color: var(--text-main);
            color: var(--bg-dark);
            text-decoration: none;
            font-weight: 700;
            font-size: 0.9rem;
            border-radius: 100px;
            transition: var(--transition);
            cursor: pointer;
            border: none;
            box-shadow: 0 10px 20px rgba(255,255,255,0.05);
        }

        .btn-cv:hover {
            transform: translateY(-3px) scale(1.02);
            box-shadow: 0 15px 30px rgba(255,255,255,0.1);
            background-color: #fff;
        }

        /* --- SECTIONS --- */
        section {
            max-width: 1100px;
            margin: 0 auto;
            padding: 120px 25px;
            scroll-margin-top: var(--nav-height);
        }

        h2 {
            font-size: 0.85rem;
            letter-spacing: 4px;
            color: var(--text-dim);
            margin-bottom: 60px;
            text-transform: uppercase;
            display: flex;
            align-items: center;
            gap: 20px;
        }

        h2::after {
            content: "";
            height: 1px;
            background: var(--border);
            flex: 1;
        }

        /* --- GRID LAYOUTS --- */
        .grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
            gap: 40px;
        }

        .card {
            background: var(--bg-card);
            border: 1px solid var(--border);
            border-radius: 16px;
            overflow: hidden;
            transition: var(--transition);
            display: flex;
            flex-direction: column;
            text-decoration: none;
            color: inherit;
        }

        .card:hover {
            border-color: #444;
            transform: translateY(-10px);
            box-shadow: 0 20px 40px rgba(0,0,0,0.4);
        }

        .card img {
            width: 100%;
            height: 280px;
            object-fit: cover;
            filter: grayscale(100%);
            transition: 0.8s cubic-bezier(0.16, 1, 0.3, 1);
        }

        .card:hover img {
            filter: grayscale(0%);
            transform: scale(1.05);
        }

        .card-content {
            padding: 30px;
            flex-grow: 1;
        }

        .card-content h3 {
            margin-bottom: 10px;
            font-size: 1.25rem;
        }

        .card-content p {
            color: var(--text-dim);
            font-size: 0.95rem;
        }

        .figma-link {
            display: inline-block;
            margin-top: 15px;
            color: var(--text-main);
            font-size: 0.8rem;
            text-transform: uppercase;
            letter-spacing: 1px;
            font-weight: 700;
        }

        /* --- CONTACT --- */
        .social-icons {
            margin-top: 40px;
            display: flex;
            justify-content: center;
            gap: 40px;
        }

        .social-icons a {
            color: var(--text-dim);
            font-size: 1.8rem;
            transition: var(--transition);
        }

        .social-icons a:hover {
            color: var(--text-main);
            transform: translateY(-5px);
        }

        /* --- RESPONSIVE --- */
        @media (max-width: 600px) {
            header { padding: 100px 20px 60px; }
            section { padding: 80px 20px; }
            nav { gap: 15px; }
        }
    </style>
</head>
<body>

    <nav>
        <a href="#about">About</a>
        <a href="#skills">Skills</a>
        <a href="#certificates">Certificates</a>
        <a href="#contact">Contact</a>
    </nav>

    <header>
        <h1 class="main-title">ANTHONY ESPINOSA</h1>
        <p style="color: var(--text-dim); letter-spacing: 2px; font-weight: 300;">STRATEGIC GRAPHICS DESIGNER | IT PROFESSIONAL</p>
        
        <a href="Professional Minimalist CV Resume.jpg" class="btn-cv" download="Professional Minimalist CV Resume.jpg">
            <i class="fas fa-file-pdf"></i> DOWNLOAD CV
        </a>
    </header>
    
    <section id="about">
        <h2>ABOUT ME</h2>
        <div class="grid" style="align-items: center; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));">
            <div style="position: relative;">
                <img src="https://daverezaba123-qghmk.wordpress.com/wp-content/uploads/2026/04/img_20260421_1341155322485705782540295.png?w=815" alt="Anthony Espinosa" style="width: 100%; border-radius: 20px; filter: contrast(1.05); box-shadow: 0 20px 40px rgba(0,0,0,0.3);">
            </div>
            <div>
                <p style="font-size: 1.25rem; line-height: 1.8; font-weight: 500;">Strategic Graphic Designer with a proven track record of translating complex briefs into high-performing visual assets.</p>
                <p style="margin-top: 25px; color: var(--text-dim);">Expert in Adobe Creative Suite and brand systems, dedicated to enhancing market presence through cohesive storytelling and data-driven design solutions. Based in the Philippines with a Bachelor in Information Technology from Central Philippine State University.</p>
            </div>
        </div>
    </section>

    <section id="skills">
        <h2>SKILLS & PROJECTS</h2>
        <div class="grid">
            <a href="https://www.figma.com" target="_blank" class="card">
                <div style="height: 280px; background: #1e1e1e; display: flex; align-items: center; justify-content: center;">
                    <i class="fab fa-figma" style="font-size: 5rem; color: #F24E1E;"></i>
                </div>
                <div class="card-content">
                    <h3>UI/UX Design</h3>
                    <p>Interface prototypes and design systems built for high-conversion user experiences.</p>
                    <span class="figma-link">View Figma Project <i class="fas fa-external-link-alt"></i></span>
                </div>
            </a>

            <div class="card">
                <img src="https://daverezaba123-qghmk.wordpress.com/wp-content/uploads/2026/04/received_267360033126596614052547090387034825.jpeg?w=632" alt="Layout">
                <div class="card-content">
                    <h3>Design & Layout</h3>
                    <p>Expertise in T-shirt sublimation layout, brand identity, and Adobe Creative Suite.</p>
                </div>
            </div>

            <div class="card">
                <img src="https://daverezaba123-qghmk.wordpress.com/wp-content/uploads/2026/04/received_14720831838393725292710248625092296.jpeg?w=683" alt="Dev">
                <div class="card-content">
                    <h3>Technical IT</h3>
                    <p>Digital Marketing, SEO, and Physics-based game simulation hosted on GitHub.</p>
                </div>
            </div>
            
            <div class="card">
                <img src="https://daverezaba123-qghmk.wordpress.com/wp-content/uploads/2026/04/received_16477739230848778504253922941591082.jpeg?w=768" alt="3D">
                <div class="card-content">
                    <h3>3D Modeling</h3>
                    <p>Conceptualized and built the "Hoopshot Vendo Machine" prototype from 3D model to physical output.</p>
                </div>
            </div>
        </div>
    </section>

    <section id="certificates">
        <h2>CERTIFICATES</h2>
        <div class="card" style="max-width: 700px; margin: 0 auto; display: flex; flex-direction: column;">
            <img src="https://daverezaba123-qghmk.wordpress.com/wp-content/uploads/2026/04/received_9445525915134996693128524351569481.jpeg?w=716" alt="Cyber Security" style="height: 400px;">
            <div class="card-content">
                <h3>Cyber Security Completion</h3>
                <p>Verified mastery in fundamental Cyber Security practices and network defense strategy.</p>
            </div>
        </div>
    </section>

    <section id="contact">
        <h2>CONTACT</h2>
        <div class="contact-info" style="text-align: center;">
            <p style="font-size: 1.5rem; color: #fff; font-weight: 700;">Ready to collaborate?</p>
            <p style="color: var(--text-dim);">Phone: 09815600546 | Email: espinosaanthony50@gmail.com</p>
            <div class="social-icons">
                <a href="mailto:espinosaanthony50@gmail.com" title="Email"><i class="fas fa-envelope"></i></a>
                <a href="https://www.facebook.com/anthony.ortegaespinosa.1" target="_blank" title="Facebook"><i class="fab fa-facebook-f"></i></a>
                <a href="https://www.instagram.com/toni_2high" target="_blank" title="Instagram"><i class="fab fa-instagram"></i></a>
                <a href="https://www.figma.com" target="_blank" title="Figma"><i class="fab fa-figma"></i></a>
                <a href="https://github.com" target="_blank" title="GitHub"><i class="fab fa-github"></i></a>
            </div>
        </div>
    </section>

</body>
</html>
