<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Anthony Espinosa | IT Portfolio</title>
  
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;600;800&display=swap" rel="stylesheet">
  
  <style>
    :root {
      --bg: #050505;
      --card: #0f0f0f;
      --accent: #38bdf8;
      --accent-soft: rgba(56, 189, 248, 0.1);
      --text: #f8fafc;
      --dim: #94a3b8;
      --border: rgba(255, 255, 255, 0.05);
      --transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
    }

    * { margin: 0; padding: 0; box-sizing: border-box; scroll-behavior: smooth; }

    body { 
      background-color: var(--bg);
      color: var(--text);
      font-family: 'Inter', sans-serif;
      line-height: 1.6;
      overflow-x: hidden;
    }

    /* Ambient Lighting Effect */
    .glow {
      position: fixed;
      top: -10%;
      right: -10%;
      width: 600px;
      height: 600px;
      background: radial-gradient(circle, rgba(56, 189, 248, 0.08) 0%, transparent 70%);
      z-index: -1;
      pointer-events: none;
    }

    /* Professional Navigation */
    nav {
      position: sticky;
      top: 0;
      z-index: 1000;
      display: flex;
      justify-content: center;
      padding: 20px;
      background: rgba(5, 5, 5, 0.8);
      backdrop-filter: blur(12px);
      border-bottom: 1px solid var(--border);
    }

    .nav-inner {
      display: flex;
      gap: 30px;
    }

    nav a {
      text-decoration: none;
      color: var(--dim);
      font-size: 0.85rem;
      font-weight: 600;
      letter-spacing: 0.5px;
      transition: var(--transition);
      cursor: pointer;
    }

    nav a:hover, nav a.active { color: var(--accent); }

    /* Layout Containers */
    header {
      max-width: 1000px;
      margin: 80px auto 40px;
      padding: 0 20px;
      text-align: center;
    }

    header h1 {
      font-size: clamp(2.5rem, 8vw, 4.5rem);
      font-weight: 800;
      letter-spacing: -2px;
      margin-bottom: 10px;
    }

    header span { color: var(--accent); }

    section {
      max-width: 1000px;
      margin: 0 auto 100px;
      padding: 0 20px;
      display: none;
      animation: fadeInUp 0.6s ease forwards;
    }

    section.active { display: block; }

    @keyframes fadeInUp {
      from { opacity: 0; transform: translateY(20px); }
      to { opacity: 1; transform: translateY(0); }
    }

    /* Professional Cards (Bento Style) */
    .bento-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
      gap: 20px;
      margin-top: 30px;
    }

    .card {
      background: var(--card);
      border: 1px solid var(--border);
      padding: 35px;
      border-radius: 24px;
      transition: var(--transition);
    }

    .card:hover {
      border-color: rgba(56, 189, 248, 0.3);
      transform: translateY(-5px);
      box-shadow: 0 20px 40px rgba(0,0,0,0.4);
    }

    h2 { font-size: 1.5rem; font-weight: 800; margin-bottom: 20px; color: var(--accent); }
    h3 { font-size: 1.1rem; margin-bottom: 10px; }
    p { color: var(--dim); font-size: 0.95rem; }

    /* Skills Badges */
    .skills-container { display: flex; flex-wrap: wrap; gap: 10px; margin-top: 20px; }
    .skill {
      background: var(--accent-soft);
      color: var(--accent);
      padding: 6px 14px;
      border-radius: 100px;
   7   font-size: 0.75rem;
      font-weight: 700;
      border: 1px solid rgba(56, 189, 248, 0.2);
    }

    /* Chatbot UI */
    .chat-widget {
      position: fixed;
      bottom: 30px;
      right: 30px;
      width: 340px;
      background: #111;
      border: 1px solid var(--border);
      border-radius: 20px;
      box-shadow: 0 25px 50px -12px rgba(0,0,0,0.5);
      z-index: 2000;
      overflow: hidden;
    }

    .chat-header {
      padding: 15px 20px;
      background: rgba(255,255,255,0.03);
      border-bottom: 1px solid var(--border);
      display: flex;
      align-items: center;
      gap: 10px;
      font-size: 0.7rem;
      font-weight: 800;
      color: var(--dim);
    }

    .status { width: 8px; height: 8px; background: #22c55e; border-radius: 50%; }

    .chat-body {
      height: 240px;
      padding: 20px;
      overflow-y: auto;
      display: flex;
      flex-direction: column;
      gap: 12px;
      font-size: 0.85rem;
    }

    .bubble { padding: 10px 14px; border-radius: 14px; max-width: 85%; }
    .bubble.bot { background: var(--accent-soft); color: var(--text); align-self: flex-start; border-bottom-left-radius: 2px; }
    .bubble.user { background: var(--accent); color: #000; font-weight: 600; align-self: flex-end; border-bottom-right-radius: 2px; }

    #chatInput {
      width: 100%;
      padding: 18px;
      background: transparent;
      border: none;
      border-top: 1px solid var(--border);
      color: white;
      outline: none;
      font-size: 0.85rem;
    }

    footer { text-align: center; padding: 60px; color: var(--dim); font-size: 0.75rem; border-top: 1px solid var(--border); }

    @media (max-width: 600px) {
      .chat-widget { display: none; }
      header h1 { font-size: 3rem; }
    }
  </style>
</head>
<body>

  <div class="glow"></div>

  <nav>
    <div class="nav-inner">
      <a href="#about" class="active" onclick="navigate(event, 'about')">ABOUT</a>
      <a href="#expertise" onclick="navigate(event, 'expertise')">EXPERTISE</a>
      <a href="#work" onclick="navigate(event, 'work')">STUDIES</a>
      <a href="#project" onclick="navigate(event, 'contact')">PROJECT</a>
       <a href="#contact" onclick="navigate(event, 'contact')">CONTACT</a>
    </div>
  </nav>

  <header>
    <h1>Anthony <span>Espinosa</span></h1>
    <p style="color: var(--dim); text-transform: uppercase; letter-spacing: 3px; font-weight: 600; font-size: 0.75rem;">Information Technology Student // Philippines</p>
  </header>

  <section id="about" class="active">
    <div class="card">
      <h2>The Objective</h2>
      <p>I am a student currently building a foundation in Information Technology.   <strong></strong> <strong></strong>. I believe that professional code isn't just about functionality, but also about simplicity and reliability.</p>
    </div>
  </section>

  <section id="expertise">
    <h2>Current Focus</h2>
    <div class="bento-grid">
      <div class="card">
        <h3>Programming</h3>
        <p>Mastering core logic and structured development.</p>
        <div class="skills-container">
          <div class="skill">JAVA</div>
          
          <div class="skill">HTML</div>
        </div>
      </div>
      <div class="card">
        <h3>Design Systems</h3>
          <div class="skills-container">
          <div class="skill">FIGMA</div>
          
        </div>
      </div>
    </div>
  </section>

  <section id="work">
    <h2>Academic Milestones</h2>
    <div class="bento-grid">
      <div class="card">
        <h3>Logic Lab</h3>
        <p>Researching and practicing algorithm efficiency using Java and JavaScript environments.</p>
      </div>
      <div class="card">
        <h3>Interface Development</h3>
        <p>Constructing responsive, high-performance web structures for personal academic review.</p>
      </div>
    </div>
  </section>

  <section id="contact">
    <div class="card" style="text-align: center;">
      <h2>Let's Connect</h2>
      <p style="margin-bottom: 20px;">Open for academic collaboration and technical discussions.</p>
      <a href="mailto:espinosaanthony50@gmail.com" style="color: var(--accent); text-decoration: none; font-weight: 800; font-size: 1.2rem;">espinosaanthony50@gmail.com</a>
      <a href="mailto:(https://www.facebook.com/anthony.ortegaespinosa.1)" style="color: var(--accent); text-decoration: none; font-weight: 800; font-size: 1.2rem;">Anthony Espinosa </a>
      <a href="mailto:https://www.instagram.com/toni_2high?igsh=MXFxcXVwc2Y5bXRpeQ==" style="color: var(--accent); text-decoration: none; font-weight: 800; font-size: 1.2rem;">toni_2high </a>
    </div>
  </section>

  <div class="chat-widget">
    <div class="chat-header">
      <div class="status"></div>
      VIRTUAL ASSISTANT // ONLINE
    </div>
    <div class="chat-body" id="chatBody">
      <div class="bubble bot">Welcome. How can I assist you with Anthony's portfolio today?</div>
    </div>
    <input type="text" id="chatInput" placeholder="Ask about 'skills' or 'studies'..." onkeypress="handleChat(event)">
  </div>

  <footer>
    &copy; 2026 ANTHONY ESPINOSA // DEVELOPING WITH PURPOSE
  </footer>

  <script>
    // Professional Navigation Logic
    function navigate(event, id) {
      event.preventDefault();
      document.querySelectorAll('section').forEach(s => s.classList.remove('active'));
      document.querySelectorAll('nav a').forEach(a => a.classList.remove('active'));
      
      document.getElementById(id).classList.add('active');
      event.currentTarget.classList.add('active');
      window.scrollTo({ top: 0, behavior: 'smooth' });
    }

    // Interactive Chatbot Logic
    function handleChat(e) {
      if (e.key === 'Enter') {
        const input = document.getElementById('chatInput');
        const body = document.getElementById('chatBody');
        const query = input.value.trim().toLowerCase();

        if (query) {
          body.innerHTML += `<div class="bubble user">${query}</div>`;
          
          let response = "I don't have information on that specific query. Please try asking about 'skills', 'studies', or 'contact'.";
          
          if (query.includes("skill") || query.includes("focus")) {
            response = "Anthony is focused on Java, JavaScript, and UI Design via Figma.";
          } else if (query.includes("study") || query.includes("work")) {
            response = "Anthony is currently documenting his academic progress in algorithm logic and web architecture.";
          } else if (query.includes("contact") || query.includes("email")) {
            response = "Official correspondence can be sent to espinosaanthony50@gmail.com.";
          } else if (query.includes("hi") || query.includes("hello")) {
            response = "Hello. I am here to provide details on Anthony's technical journey.";
          }

          setTimeout(() => {
            body.innerHTML += `<div class="bubble bot">${response}</div>`;
            body.scrollTop = body.scrollHeight;
          }, 450);

          input.value = "";
        }
      }
    }
  </script>
</body>
</html>
