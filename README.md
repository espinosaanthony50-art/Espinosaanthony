<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Anthony Espinosa | IT Professional Portfolio</title>
  
  <meta name="description" content="Portfolio of Anthony Espinosa, an IT Student & Developer based in the Philippines.">
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
      font-size: clamp(2.5rem, 8vw, 4.5rem);
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
      flex-wrap: wrap;
      gap: 15px;
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
      font-size: 0.85rem;
      text-transform: uppercase;
      letter-spacing: 1px;
      transition: var(--transition);
      cursor: pointer;
    }

    nav a:hover, nav a.active {
      color: var(--accent);
    }

    section {
      display: none;
      max-width: 900px;
      margin: 40px auto;
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
      grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
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
      height: 180px;
      object-fit: cover;
      border-radius: 14px;
      margin-bottom: 20px;
      border: 1px solid var(--border);
    }

    .btn-group {
      display: flex;
      flex-wrap: wrap;
      gap: 15px;
      margin-top: 30px;
    }

    .primary-btn, .cv-btn {
      padding: 14px 30px;
      border-radius: 12px;
      text-decoration: none;
      font-weight: 700;
      transition: var(--transition);
      text-align: center;
    }

    .primary-btn {
      background: var(--accent);
      color: var(--bg);
    }

    .primary-btn:hover {
      transform: scale(1.05);
      box-shadow: 0 0 20px rgba(56, 189, 248, 0.4);
    }

    .cv-btn {
      background: transparent;
      color: var(--accent);
      border: 1px solid var(--accent);
    }

    .cv-btn:hover {
      background: rgba(56, 189, 248, 0.1);
    }

    /* Chatbot */
    .chatbot {
      position: fixed;
      bottom: 20px;
      right: 20px;
      width: 300px;
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
      padding: 12px;
      font-weight: 800;
      text-align: center;
      font-size: 0.7rem;
      letter-spacing: 1px;
    }

    .chat-body {
      height: 200px;
      padding: 15px;
      overflow-y: auto;
      font-size: 0.8rem;
      background: #020617;
      display: flex;
      flex-direction: column;
      gap: 10px;
      scroll-behavior: smooth;
    }

    #chatInput {
      width: 100%;
      background: var(--card-bg);
      border: none;
      border-top: 1px solid var(--border);
      padding: 12px;
      color: white;
      outline: none;
    }

    footer {
      text-align: center;
      padding: 60px 20px;
      color: var(--text-dim);
      font-size: 0.75rem;
    }

    @media (max-width: 600px) {
      section { padding: 30px 20px; margin: 20px; }
      .chatbot { display: none; } /* Hide chat on mobile for better UX */
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
    <a href="#home" onclick="showSection(event, 'home')">Home</a>
    <a href="#about" onclick="showSection(event, 'about')">About</a>
    <a href="#projects" onclick="showSection(event, 'projects')">Projects</a>
    <a href="#skills" onclick="showSection(event, 'skills')">Skills</a>
    <a href="#contact" onclick="showSection(event, 'contact')">Contact</a>
  </nav>

  <section id="home" class="active">
    <h2>Welcome</h2>
    <p>I build clean, logical, and user-centered digital experiences. Based in the Philippines, I'm currently focused on bridging the gap between technical efficiency and intuitive design.</p>
    <div class="btn-group">
      <a href="#projects" class="primary-btn" onclick="showSection(event, 'projects')">View My Work</a>
      <a href="cv.pdf" download class="cv-btn">Download CV</a>
    </div>
  </section>

  <section id="about">
    <h2>About Me</h2>
    <p>I am an IT student with a passion for full-stack development. I believe that great software is born at the intersection of technical logic and human experience.</p>
  </section>

  <section id="projects">
    <h2>Featured Work</h2>
    <div class="grid">
      <div class="item-card">
        <div style="background:#1f2937; height:180px; border-radius:14px; margin-bottom:20px; display:flex; align-items:center; justify-content:center;">
            <span>Project A Image</span>
        </div>
        <h3>Jersey Layout Engine</h3>
        <p>A specialized configuration tool for apparel design.</p>
      </div>
      <div class="item-card">
        <div style="background:#1f2937; height:180px; border-radius:14px; margin-bottom:20px; display:flex; align-items:center; justify-content:center;">
            <span>Project B Image</span>
        </div>
        <h3>Logic Engine</h3>
        <p>JS utilities designed to automate data workflows.</p>
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
    </div>
  </section>

  <section id="contact">
    <h2>Let's Connect</h2>
    <div style="display: flex; flex-direction: column; gap: 15px;">
      <a href="mailto:espinosaanthony50@gmail.com" style="color:var(--accent); text-decoration:none;">📧 espinosaanthony50@gmail.com</a>
      <a href="#" style="color:var(--accent); text-decoration:none;">👤 Anthony Espinosa (Facebook)</a>
    </div>
  </section>

  <div class="chatbot">
    <div class="chat-header">SYSTEM ASSISTANT // ACTIVE</div>
    <div class="chat-body" id="chatBody">
      <p><span style="color:var(--accent)">[Bot]:</span> Hello. Ask me about Anthony's skills or projects.</p>
    </div>
    <input type="text" id="chatInput" placeholder="Type a command..." onkeypress="handleChat(event)">
  </div>

  <footer>
    <p>&copy; 2026 Anthony Espinosa // Built for Performance.</p>
  </footer>

  <script>
    function showSection(event, sectionId) {
      if(event) event.preventDefault();
      
      // Hide all sections
      document.querySelectorAll('section').forEach(sec => sec.classList.remove('active'));
      // Remove active class from all links
      document.querySelectorAll('nav a').forEach(link => link.classList.remove('active'));

      const target = document.getElementById(sectionId);
      if(target) {
        target.classList.add('active');
        // Add active class to clicked link
        const activeLink = document.querySelector(`nav a[href="#${sectionId}"]`);
        if (activeLink) activeLink.classList.add('active');
        
        // Scroll to top of section
        window.scrollTo({ top: 0, behavior: 'smooth' });
      }
    }

    const botResponses = {
      skills: "Anthony is proficient in HTML5, Java, and JavaScript, with specialized skills in UI/UX Design.",
      projects: "He has developed a Jersey Layout Engine and custom Logic Engines.",
      contact: "Email him at espinosaanthony50@gmail.com.",
      hi: "Hello! How can I help you today?"
    };

    function handleChat(event) {
      if (event.key === 'Enter') {
        const input = document.getElementById('chatInput');
        const chatBody = document.getElementById('chatBody');
        const val = input.value.trim().toLowerCase();

        if (val) {
          chatBody.innerHTML += `<p><span style="color:#fff">[You]:</span> ${val}</p>`;
          
          let response = "Try asking about 'skills', 'projects', or 'contact'.";
          if(val.includes("skill")) response = botResponses.skills;
          else if(val.includes("project")) response = botResponses.projects;
          else if(val.includes("contact")) response = botResponses.contact;
          else if(val.includes("hi") || val.includes("hello")) response = botResponses.hi;
          
          setTimeout(() => {
            chatBody.innerHTML += `<p><span style="color:var(--accent)">[Bot]:</span> ${response}</p>`;
            chatBody.scrollTop = chatBody.scrollHeight;
          }, 300);

          input.value = "";
        }
      }
    }

    // Initial load
    window.addEventListener('load', () => {
      const hash = window.location.hash.substring(1) || 'home';
      showSection(null, hash);
    });
  </script>
</body>
</html>
