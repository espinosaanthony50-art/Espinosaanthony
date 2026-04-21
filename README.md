<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Anthony Espinosa | Portfolio</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">
    <style>
        /* --- DESIGN TOKENS & RESET --- */
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
        }

        .card-content h3 {
            margin-bottom: 10px;
            font-size: 1.25rem;
        }

        .card-content p {
            color: var(--text-dim);
            font-size: 0.95rem;
        }

        /* --- CHATBOT UI --- */
        #chat-widget {
            position: fixed;
            bottom: 100px;
            right: 30px;
            width: 350px;
            height: 500px;
            background: #1a1a1a;
            border: 1px solid var(--border);
            border-radius: 24px;
            display: none;
            flex-direction: column;
            box-shadow: 0 24px 48px rgba(0,0,0,0.8);
            z-index: 2000;
            overflow: hidden;
        }

        #chat-header {
            padding: 20px;
            background: #222;
            display: flex;
            justify-content: space-between;
            align-items: center;
            border-bottom: 1px solid var(--border);
        }

        #chat-messages {
            flex: 1;
            padding: 20px;
            overflow-y: auto;
            font-size: 0.9rem;
            display: flex;
            flex-direction: column;
            gap: 12px;
        }

        .msg { padding: 12px 16px; border-radius: 14px; max-width: 85%; }
        .bot { background: #262626; color: var(--text-main); align-self: flex-start; border-bottom-left-radius: 2px; }
        .user { background: var(--text-main); color: var(--bg-dark); align-self: flex-end; border-bottom-right-radius: 2px; font-weight: 500; }

        .chat-options {
            display: flex;
            flex-wrap: wrap;
            gap: 8px;
            padding: 15px;
            background: #151515;
        }

        .opt-btn {
            background: #222;
            border: 1px solid var(--border);
            color: var(--text-dim);
            padding: 6px 12px;
            border-radius: 8px;
            font-size: 0.75rem;
            cursor: pointer;
            transition: 0.2s;
        }

        .opt-btn:hover {
            background: #333;
            color: #fff;
        }

        #chat-input-area {
            display: flex;
            padding: 15px;
            background: #111;
            border-top: 1px solid var(--border);
        }

        #chat-input {
            flex: 1;
            background: transparent;
            border: none;
            color: white;
            outline: none;
            font-size: 0.9rem;
        }

        #chat-trigger {
            position: fixed;
            bottom: 30px;
            right: 30px;
            background: var(--text-main);
            color: var(--bg-dark);
            width: 64px;
            height: 64px;
            border-radius: 50%;
            display: flex;
            justify-content: center;
            align-items: center;
            cursor: pointer;
            z-index: 1999;
            box-shadow: 0 8px 24px rgba(255,255,255,0.1);
            font-size: 1.5rem;
            transition: var(--transition);
        }

        #chat-trigger:hover {
            transform: rotate(15deg) scale(1.1);
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
            #chat-widget { width: calc(100% - 40px); right: 20px; bottom: 100px; }
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
        <p style="color: var(--text-dim); letter-spacing: 2px; font-weight: 300;">ASPIRING IT PROFESSIONAL | SYSTEMS & DESIGN</p>
        <button class="btn-cv" onclick="downloadCV()">
            <i class="fas fa-arrow-down-long"></i> DOWNLOAD CV
        </button>
    </header>

    <section id="about">
        <h2>ABOUT ME</h2>
        <div class="grid" style="align-items: center; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));">
            <div style="position: relative;">
                <img src="https://daverezaba123-qghmk.wordpress.com/wp-content/uploads/2026/04/img_20260421_1341155322485705782540295.png?w=815" alt="Anthony Espinosa" style="width: 100%; border-radius: 20px; filter: contrast(1.1);">
            </div>
            <div>
                <p style="font-size: 1.2rem; line-height: 1.8;">I am an aspiring IT Professional driven by how complex systems solve real-world problems. My focus is on bridging the gap between technical efficiency and user experience.</p>
                <p style="margin-top: 25px; color: var(--text-dim);">Based in the Philippines, I specialize in creative technical solutions ranging from 3D modeling to cybersecurity.</p>
            </div>
        </div>
    </section>

    <section id="skills">
        <h2>SKILLS & PROJECTS</h2>
        <div class="grid">
            <div class="card">
                <img src="https://daverezaba123-qghmk.wordpress.com/wp-content/uploads/2026/04/received_267360033126596614052547090387034825.jpeg?w=632" alt="Layout">
                <div class="card-content">
                    <h3>Design & Layout</h3>
                    <p>T-shirt sublimation layout and high-quality image editing using professional tools.</p>
                </div>
            </div>
            <div class="card">
                <img src="https://daverezaba123-qghmk.wordpress.com/wp-content/uploads/2026/04/received_14720831838393725292710248625092296.jpeg?w=683" alt="Dev">
                <div class="card-content">
                    <h3>Game Simulation</h3>
                    <p>Physics-based game development and logic simulations hosted on GitHub.</p>
                </div>
            </div>
            <div class="card">
                <img src="https://daverezaba123-qghmk.wordpress.com/wp-content/uploads/2026/04/received_16477739230848778504253922941591082.jpeg?w=768" alt="3D">
                <div class="card-content">
                    <h3>3D Modeling</h3>
                    <p>Hoopshot Vendo Machine: From 3D conceptual modeling to physical prototype output.</p>
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
                <p>Verified course completion in fundamental Cyber Security practices and network defense.</p>
            </div>
        </div>
    </section>

    <section id="contact">
        <h2>CONTACT</h2>
        <div class="contact-info">
            <p style="font-size: 1.5rem; color: #fff; font-weight: 700;">Ready to collaborate or hire?</p>
            <div class="social-icons">
                <a href="mailto:espinosaanthony50@gmail.com" title="Email"><i class="fas fa-envelope"></i></a>
                <a href="https://www.facebook.com/anthony.ortegaespinosa.1" target="_blank" title="Facebook"><i class="fab fa-facebook-f"></i></a>
                <a href="https://www.instagram.com/toni_2high" target="_blank" title="Instagram"><i class="fab fa-instagram"></i></a>
                <a href="https://github.com" target="_blank" title="GitHub"><i class="fab fa-github"></i></a>
            </div>
        </div>
    </section>

    <div id="chat-trigger" onclick="toggleChat()"><i class="fas fa-comment"></i></div>
    
    <div id="chat-widget">
        <div id="chat-header">
            <div style="display:flex; align-items:center; gap:10px;">
                <div style="width:8px; height:8px; background:#00ff00; border-radius:50%;"></div>
                <strong style="font-size:0.8rem; letter-spacing:1px; text-transform:uppercase;">AI Assistant</strong>
            </div>
            <span onclick="toggleChat()" style="cursor:pointer; font-size: 1.5rem; color: var(--text-dim);">&times;</span>
        </div>
        <div id="chat-messages">
            <div class="msg bot">Hi! I'm Anthony's AI. How can I help you today?</div>
        </div>
        
        <div class="chat-options">
            <button class="opt-btn" onclick="handleQuickAction('Skills')">Skills</button>
            <button class="opt-btn" onclick="handleQuickAction('Certificates')">Certificates</button>
            <button class="opt-btn" onclick="handleQuickAction('Contact')">Contact</button>
            <button class="opt-btn" onclick="handleQuickAction('3D Projects')">3D Projects</button>
        </div>

        <div id="chat-input-area">
            <input type="text" id="chat-input" placeholder="Ask a question..." onkeypress="handleChat(event)">
        </div>
    </div>

    <script>
        function downloadCV() {
            const cvContent = "Anthony Espinosa CV\nIT Professional\nSkills: Web Dev, 3D Modeling, Cyber Security.";
            const blob = new Blob([cvContent], { type: 'text/plain' });
            const url = window.URL.createObjectURL(blob);
            const a = document.createElement('a');
            a.href = url;
            a.download = 'Anthony_Espinosa_CV.txt';
            document.body.appendChild(a);
            a.click();
            document.body.removeChild(a);
        }

        function toggleChat() {
            const chat = document.getElementById('chat-widget');
            chat.style.display = (chat.style.display === 'flex') ? 'none' : 'flex';
        }

        function handleQuickAction(action) {
            processChat(action);
        }

        function handleChat(e) {
            if (e.key === 'Enter') {
                const input = document.getElementById('chat-input');
                const text = input.value.trim();
                if (!text) return;
                input.value = '';
                processChat(text);
            }
        }

        function processChat(userInput) {
            appendMessage(userInput, 'user');
            
            const msg = userInput.toLowerCase();
            setTimeout(() => {
                let response = "I'm not sure about that. Try one of the buttons above!";
                
                if (msg.includes('skill') || msg.includes('do')) {
                    response = "Anthony is skilled in T-shirt layout, image editing, and Game Simulation in GitHub.";
                } else if (msg.includes('certif') || msg.includes('cyber')) {
                    response = "Anthony holds a certificate in Cyber Security completion.";
                } else if (msg.includes('hoopshot') || msg.includes('3d') || msg.includes('vendo')) {
                    response = "He designed and built a 'Hoopshot Vendo Machine' using 3D modeling and physical construction.";
                } else if (msg.includes('contact') || msg.includes('email') || msg.includes('gmail') || msg.includes('social')) {
                    response = "You can contact Anthony at espinosaanthony50@gmail.com or find his social links in the contact section!";
                } else if (msg.includes('who') || msg.includes('about')) {
                    response = "Anthony is an aspiring IT professional specializing in systems and user experience.";
                }
                
                appendMessage(response, 'bot');
            }, 600);
        }

        function appendMessage(text, sender) {
            const container = document.getElementById('chat-messages');
            const div = document.createElement('div');
            div.className = `msg ${sender}`;
            div.innerText = text;
            container.appendChild(div);
            container.scrollTop = container.scrollHeight;
        }
    </script>
</body>
</html>
