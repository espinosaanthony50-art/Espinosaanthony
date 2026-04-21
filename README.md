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
            --bg-dark: #121212;
            --bg-card: #1e1e1e;
            --text-main: #ffffff;
            --text-dim: #b0b0b0;
            --accent: #e0e0e0;
            --border: #333333;
            --nav-height: 60px;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            scroll-behavior: smooth;
        }

        body {
            font-family: 'Inter', -apple-system, BlinkMacSystemFont, sans-serif;
            background-color: var(--bg-dark);
            color: var(--text-main);
            line-height: 1.6;
        }

        /* --- HEADER & NAVIGATION --- */
        header {
            text-align: center;
            padding: 100px 20px 60px;
            background: linear-gradient(to bottom, #000, var(--bg-dark));
        }

        .main-title {
            font-size: 3rem;
            font-weight: 900;
            letter-spacing: -1px;
            text-transform: uppercase;
            margin-bottom: 10px;
        }

        nav {
            position: sticky;
            top: 0;
            background: rgba(18, 18, 18, 0.95);
            backdrop-filter: blur(10px);
            border-bottom: 1px solid var(--border);
            z-index: 1000;
            display: flex;
            justify-content: center;
            padding: 15px;
            gap: 20px;
            height: var(--nav-height);
        }

        nav a {
            color: var(--text-dim);
            text-decoration: none;
            font-weight: 500;
            font-size: 0.9rem;
            text-transform: uppercase;
            transition: 0.3s;
        }

        nav a:hover {
            color: var(--text-main);
        }

        /* --- BUTTONS --- */
        .btn-cv {
            display: inline-block;
            margin-top: 20px;
            padding: 12px 25px;
            background-color: var(--text-main);
            color: var(--bg-dark);
            text-decoration: none;
            font-weight: bold;
            border-radius: 5px;
            transition: transform 0.2s, background-color 0.2s;
            cursor: pointer;
            border: none;
        }

        .btn-cv:hover {
            background-color: var(--accent);
            transform: translateY(-2px);
        }

        /* --- SECTIONS --- */
        section {
            max-width: 1000px;
            margin: 0 auto;
            padding: 80px 20px;
            /* Prevents nav from covering title when jumping to ID */
            scroll-margin-top: var(--nav-height);
        }

        h2 {
            font-size: 2rem;
            border-left: 4px solid var(--accent);
            padding-left: 15px;
            margin-bottom: 40px;
            text-transform: uppercase;
        }

        /* --- GRID LAYOUTS --- */
        .grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 30px;
        }

        .card {
            background: var(--bg-card);
            border: 1px solid var(--border);
            border-radius: 10px;
            overflow: hidden;
            transition: 0.3s;
        }

        .card:hover {
            border-color: var(--text-dim);
        }

        .card img {
            width: 100%;
            height: 250px;
            object-fit: cover;
            filter: grayscale(100%);
            transition: 0.5s;
        }

        .card:hover img {
            filter: grayscale(0%);
        }

        .card-content {
            padding: 20px;
        }

        /* --- CHATBOT UI --- */
        #chat-widget {
            position: fixed;
            bottom: 90px;
            right: 20px;
            width: 320px;
            height: 450px;
            background: var(--bg-card);
            border: 1px solid var(--border);
            border-radius: 15px;
            display: none;
            flex-direction: column;
            box-shadow: 0 10px 30px rgba(0,0,0,0.5);
            z-index: 2000;
        }

        #chat-header {
            padding: 15px;
            background: var(--border);
            border-radius: 15px 15px 0 0;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        #chat-messages {
            flex: 1;
            padding: 15px;
            overflow-y: auto;
            font-size: 0.85rem;
            display: flex;
            flex-direction: column;
        }

        .msg { margin-bottom: 10px; padding: 10px; border-radius: 8px; max-width: 85%; word-wrap: break-word; }
        .bot { background: var(--border); color: var(--text-main); align-self: flex-start; }
        .user { background: var(--text-main); color: var(--bg-dark); align-self: flex-end; }

        .chat-options {
            display: flex;
            flex-wrap: wrap;
            gap: 5px;
            padding: 10px;
            border-top: 1px solid var(--border);
        }

        .opt-btn {
            background: transparent;
            border: 1px solid var(--text-dim);
            color: var(--text-dim);
            padding: 5px 10px;
            border-radius: 15px;
            font-size: 0.75rem;
            cursor: pointer;
            transition: 0.2s;
        }

        .opt-btn:hover {
            border-color: var(--text-main);
            color: var(--text-main);
        }

        #chat-input-area {
            display: flex;
            padding: 10px;
            border-top: 1px solid var(--border);
        }

        #chat-input {
            flex: 1;
            background: transparent;
            border: none;
            color: white;
            outline: none;
        }

        #chat-trigger {
            position: fixed;
            bottom: 20px;
            right: 20px;
            background: var(--text-main);
            color: var(--bg-dark);
            width: 60px;
            height: 60px;
            border-radius: 50%;
            display: flex;
            justify-content: center;
            align-items: center;
            cursor: pointer;
            z-index: 1999;
            box-shadow: 0 4px 15px rgba(0,0,0,0.3);
            font-size: 1.5rem;
        }

        /* --- CONTACT --- */
        .contact-info {
            text-align: center;
            font-size: 1.2rem;
            color: var(--text-dim);
        }

        .social-icons {
            margin-top: 20px;
            display: flex;
            justify-content: center;
            gap: 30px;
        }

        .social-icons a {
            color: var(--text-main);
            font-size: 2rem;
            text-decoration: none;
            transition: transform 0.3s, color 0.3s;
        }

        .social-icons a:hover {
            color: var(--accent);
            transform: scale(1.1);
        }

        /* --- RESPONSIVE --- */
        @media (max-width: 600px) {
            .main-title { font-size: 2rem; }
            .grid { grid-template-columns: 1fr; }
            nav { gap: 10px; height: auto; padding: 10px; }
            nav a { font-size: 0.75rem; }
            #chat-widget { width: 90%; right: 5%; bottom: 90px; }
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
        <p style="color: var(--text-dim);">Aspiring IT Professional | Systems & Design</p>
        <button class="btn-cv" onclick="downloadCV()">
            <i class="fas fa-download"></i> DOWNLOAD CV
        </button>
    </header>

    <section id="about">
        <h2>About Me</h2>
        <div class="grid" style="align-items: center;">
            <img src="https://daverezaba123-qghmk.wordpress.com/wp-content/uploads/2026/04/img_20260421_1341155322485705782540295.png?w=815" alt="Anthony Espinosa" style="width: 100%; border-radius: 10px; border: 1px solid var(--border);">
            <div>
                <p>I am an aspiring IT Professional driven by how complex systems solve real-world problems. My focus is on bridging the gap between technical efficiency and user experience.</p>
                <p style="margin-top: 15px; color: var(--text-dim);">Based in the Philippines, I specialize in creative technical solutions ranging from 3D modeling to cybersecurity.</p>
            </div>
        </div>
    </section>

    <section id="skills">
        <h2>Skills & Projects</h2>
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
        <h2>Certificates</h2>
        <div class="card" style="max-width: 600px; margin: 0 auto;">
            <img src="https://daverezaba123-qghmk.wordpress.com/wp-content/uploads/2026/04/received_9445525915134996693128524351569481.jpeg?w=716" alt="Cyber Security">
            <div class="card-content">
                <h3>Cyber Security Completion</h3>
                <p>Verified course completion in fundamental Cyber Security practices and network defense.</p>
            </div>
        </div>
    </section>

    <section id="contact">
        <h2>Contact</h2>
        <div class="contact-info">
            <p>Ready to collaborate or hire?</p>
            <p style="margin-top:20px;">Email: espinosaanthony50@gmail.com</p>
            <div class="social-icons">
                <a href="mailto:espinosaanthony50@gmail.com" title="Email"><i class="fas fa-envelope"></i></a>
                <a href="https://www.facebook.com/anthony.ortegaespinosa.1" target="_blank" title="Facebook"><i class="fab fa-facebook"></i></a>
                <a href="https://www.instagram.com/toni_2high" target="_blank" title="Instagram"><i class="fab fa-instagram"></i></a>
                <a href="https://github.com" target="_blank" title="GitHub"><i class="fab fa-github"></i></a>
            </div>
        </div>
    </section>

    <div id="chat-trigger" onclick="toggleChat()"><i class="fas fa-comment-dots"></i></div>
    
    <div id="chat-widget">
        <div id="chat-header">
            <strong>Anthony's Assistant</strong>
            <span onclick="toggleChat()" style="cursor:pointer; font-size: 1.2rem;">&times;</span>
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
            <input type="text" id="chat-input" placeholder="Type a message..." onkeypress="handleChat(event)">
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
