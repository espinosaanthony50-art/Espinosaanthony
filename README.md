
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Anthony Espinosa | IT Professional Portfolio</title>
  
  <meta name="description" content="Portfolio of Anthony Espinosa, an IT Student & Developer based in the Philippines.">
  <meta property="og:title" content="Anthony Espinosa | IT Portfolio">
  <meta property="og:description" content="Bridging technical logic with professional minimalist design.">
  <meta property="og:type" content="website">

  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@300;500;700&display=swap" rel="stylesheet">
  
  <style>
    :root {
      --bg: #030712;
      --card-bg: #111827;
      --accent: #38bdf8;
      --text-main: #f9fafb;
      --text-dim: #94a3b8;
      --border: rgba(255, 255, 255, 0.08);
      --transition: all 0.4s cubic-bezier(0.23, 1, 0.32, 1);
    }

    * { margin: 0; padding: 0; box-sizing: border-box; scroll-behavior: smooth; }

    body { 
      background-color: var(--bg);
      color: var(--text-main);
      font-family: 'Space Grotesk', sans-serif;
      overflow-x: hidden;
      line-height: 1.6;
    }

    /* Ambient background glow */
    .bg-glow {
      position: fixed;
      width: 500px;
      height: 500px;
      background: radial-gradient(circle, rgba(56, 189, 248, 0.1) 0%, transparent 70%);
      top: -150px;
      right: -150px;
      z-index: -1;
      pointer-events: none;
    }

    header {
      text-align: center;
      padding: 80px 20px 40px;
    }

    header h1 {
      font-size: clamp(2.8rem, 10vw, 4.5rem);
      margin: 0;
      background: linear-gradient(to right, #38bdf8, #818cf8);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      letter-spacing: -2px;
      font-weight: 700;
    }

    header p {
      font-size: 1.2rem;
      color: var(--text-dim);
      margin-top: 10px;
      font-weight: 300;
    }

    nav {
      display: flex;
      justify-content: center;
      gap: 30px;
      padding: 20px;
      background: rgba(3, 7, 18, 0.8);
      backdrop-filter: blur(12px);
      position: sticky;
      top: 0;
      z-index: 1000;
      border-bottom: 1px solid var(--border);
    }

    nav a {
      text-decoration: none;
      color: var(--text-dim);
      font-weight: 500;
      font-size: 0.9rem;
      text-transform: uppercase;
      letter-spacing: 1px;
      transition: var(--transition);
    }

    nav a:hover, nav a.active {
      color: var(--accent);
    }

    section {
      display: none;
      max-width: 900px;
      margin: 60px auto;
      padding: 50px 40px;
      background: var(--card-bg);
      border-radius: 32px;
      border: 1px solid var(--border);
      box-shadow: 0 25px 50px -12px rgba(0, 0, 0, 0.5);
    }

    section.active {
      display: block;
      animation: fadeIn 0.6s forwards;
    }

    @keyframes fadeIn {
      from { opacity: 0; transform: translateY(20px); }
      to { opacity: 1; transform: translateY(0); }
    }

    h2 {
      font-size: 2.2rem;
      margin-bottom: 30px;
      color: var(--accent);
      letter-spacing: -1px;
    }

    .grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
      gap: 25px;
    }

    .item-card {
      background: rgba(255, 255, 255, 0.02);
      padding: 30px;
      border-radius: 20px;
      border: 1px solid var(--border);
      transition: var(--transition);
    }

    .item-card:hover {
      transform: translateY(-10px);
      border-color: var(--accent);
      background: rgba(56, 189, 248, 0.03);
    }

    .project-thumb {
      width: 100%;
      height: 200px;
      object-fit: cover;
      border-radius: 14px;
      margin-bottom: 20px;
      border: 1px solid var(--border);
    }

    /* Buttons */
    .btn-group {
      display: flex;
      gap: 15px;
      margin-top: 30px;
    }

    .primary-btn {
      padding: 14px 35px;
      background: var(--accent);
      color: var(--bg);
      border-radius: 12px;
      text-decoration: none;
      font-weight: 700;
      transition: var(--transition);
      display: inline-block;
    }

    .primary-btn:hover {
      transform: scale(1.05);
      box-shadow: 0 0 20px rgba(56, 189, 248, 0.4);
    }

    .cv-btn {
      padding: 14px 35px;
      background: transparent;
      color: var(--accent);
      border: 1px solid var(--accent);
      border-radius: 12px;
      text-decoration: none;
      font-weight: 700;
      transition: var(--transition);
    }

    .cv-btn:hover {
      background: rgba(56, 189, 248, 0.1);
    }

    /* Chatbot */
    .chatbot {
      position: fixed;
      bottom: 25px;
      right: 25px;
      width: 320px;
      background: var(--card-bg);
      border-radius: 20px;
      border: 1px solid var(--border);
      overflow: hidden;
      box-shadow: 0 20px 40px rgba(0,0,0,0.6);
      z-index: 2000;
    }

    .chat-header {
      background: var(--accent);
      color: var(--bg);
      padding: 15px;
      font-weight: 800;
      text-align: center;
      font-size: 0.75rem;
      letter-spacing: 1px;
    }

    .chat-body {
      height: 250px;
      padding: 15px;
      overflow-y: auto;
      font-size: 0.85rem;
      background: #020617;
      display: flex;
      flex-direction: column;
      gap: 10px;
    }

    #chatInput {
      width: 100%;
      background: var(--card-bg);
      border: none;
      border-top: 1px solid var(--border);
      padding: 15px;
      color: white;
      outline: none;
    }

    footer {
      text-align: center;
      padding: 80px 20px;
      color: var(--text-dim);
      font-size: 0.8rem;
      letter-spacing: 1px;
    }
  </style>
</head>
<body>

  <div class="bg-glow"></div>

  <header>
    <h1>Anthony Espinosa</h1>
    <p>Digital Architect & IT Student</p>
  </header>

  <nav id="navbar">
    <a href="#home" class="active" onclick="showSection('home')">Home</a>
    <a href="#about" onclick="showSection('about')">About</a>
    <a href="#projects" onclick="showSection('projects')">Projects</a>
    <a href="#skills" onclick="showSection('skills')">Skills</a>
    <a href="#contact" onclick="showSection('contact')">Contact</a>
  </nav>

  <section id="home" class="active">
    <h2>Welcome</h2>
    <p>I build clean, logical, and user-centered digital experiences. Based in the Philippines, I'm currently focused on bridging the gap between technical efficiency and intuitive design.</p>
    <div class="btn-group">
      <a href="#projects" class="primary-btn" onclick="showSection('projects')">View My Work</a>
      <a href="cv.pdf" download class="cv-btn">Download CV</a>
    </div>
  </section>

  <section id="about">
    <h2>About Me</h2>
    <p>I am an IT student with a passion for full-stack development. I believe that great software is born at the intersection of technical logic and human experience.</p>
    <p>Currently dedicated to mastering modern UI frameworks and simplifying complex digital workflows.</p>
  </section>

  <section id="projects">
    <h2>Featured Work</h2>
    <div class="grid">
      <div class="item-card">
        <img src="A.jpg" alt="Jersey Layout" class="project-thumb">
        <h3>Jersey Layout Engine</h3>
        <p>A specialized configuration tool for apparel design and visualization.</p>
      </div>
      <div class="item-card">
        <img src="project2.png" alt="Logic Engine" class="project-thumb">
        <h3>Logic Engine</h3>
        <p>JavaScript utilities designed to automate complex data workflows.</p>
      </div>
    </div>
  </section>

  <section id="skills">
    <h2>Technical Stack</h2>
    <div class="grid">
      <div class="item-card">
        <h3>Languages</h3>
        <p>HTML5, Java, JavaScript (ES6+)</p>
      </div>
      <div class="item-card">
        <h3>Design</h3>
        <p>Figma, UI/UX Strategy, Minimalist Design</p>
      </div>
      <div class="item-card">
        <h3>Certification</h3>
        <img src="B.jpg" alt="Certification" class="project-thumb" style="height:120px;">
        <p>Verified Professional Training (2025)</p>
      </div>
    </div>
  </section>

  <section id="contact">
    <h2>Let's Connect</h2>
    <p>Available for freelance projects and IT consultancy. Reach out through any of these channels:</p>
    <div style="margin-top: 30px; display: flex; flex-direction: column; gap: 15px;">
      <a href="mailto:espinosaanthony50@gmail.com" style="color:var(--accent); text-decoration:none;">📧 espinosaanthony50@gmail.com</a>
      <a href="https://www.facebook.com/share/1AyUQ6gKmh/" target="_blank" style="color:var(--accent); text-decoration:none;">👤 Anthony Espinosa</a>
      <a href="https://www.instagram.com/toni_2high" target="_blank" style="color:var(--accent); text-decoration:none;">📸 @toni_2high</a>
    </div>
  </section>

  <div class="chatbot">
    <div class="chat-header">SYSTEM ASSISTANT // ACTIVE</div>
    <div class="chat-body" id="chatBody">
      <p><span style="color:var(--accent)">[Bot]:</span> Welcome. Ask me about Anthony's skills, projects, or background.</p>
    </div>
    <input type="text" id="chatInput" placeholder="Type a command..." onkeypress="handleChat(event)">
  </div>

  <footer>
    <p>&copy; 2026 Anthony Espinosa // Built for Performance.</p>
  </footer>

  <script>
    function showSection(sectionId) {
      document.querySelectorAll('section').forEach(sec => sec.classList.remove('active'));
      document.querySelectorAll('nav a').forEach(link => link.classList.remove('active'));

      const target = document.getElementById(sectionId);
      if(target) {
        target.classList.add('active');
        const activeLink = document.querySelector(`nav a[href="#${sectionId}"]`);
        if (activeLink) activeLink.classList.add('active');
        window.history.pushState(null, null, `#${sectionId}`);
      }
    }

    const botResponses = {
      skills: "Anthony is proficient in HTML5, Java, and JavaScript, with specialized skills in UI/UX Design using Figma.",
      projects: "He has developed a Jersey Layout Engine and custom Logic Engines for data automation.",
      about: "Anthony is an IT student focused on Full-Stack development and simplifying complex digital workflows.",
      contact: "You can reach Anthony via email at espinosaanthony50@gmail.com or find him on Instagram @toni_2high.",
      hi: "Hello! I am Anthony's virtual assistant. How can I help you navigate his portfolio today?"
    };

    function handleChat(event) {
      if (event.key === 'Enter') {
        const input = document.getElementById('chatInput');
        const chatBody = document.getElementById('chatBody');
        const val = input.value.trim().toLowerCase();

        if (val) {
          chatBody.innerHTML += `<p><span style="color:#fff">[You]:</span> ${val}</p>`;
          
          let response = "I'm not sure about that. Try asking about 'skills', 'projects', or 'contact'.";
          
          if(val.includes("skill")) response = botResponses.skills;
          if(val.includes("project")) response = botResponses.projects;
          if(val.includes("about") || val.includes("who")) response = botResponses.about;
          if(val.includes("contact") || val.includes("email")) response = botResponses.contact;
          if(val.includes("hi") || val.includes("hello")) response = botResponses.hi;
          
          setTimeout(() => {
            chatBody.innerHTML += `<p><span style="color:var(--accent)">[Bot]:</span> ${response}</p>`;
            chatBody.scrollTop = chatBody.scrollHeight;
          }, 400);

          input.value = "";
        }
      }
    }

    window.addEventListener('load', () => {
      const hash = window.location.hash.substring(1) || 'home';
      showSection(hash);
    });
  </script>
</body>
</html>

