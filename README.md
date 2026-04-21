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
            --text-main: #ffffff;
            --text-dim: #b0b0b0;
            --accent: #f5f5f5;
            --border: #222222;
            --transition: all 0.3s cubic-bezier(0.16, 1, 0.3, 1);
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
            line-height: 1.6;
            -webkit-font-smoothing: antialiased;
        }

        /* --- HEADER & NAVIGATION --- */
        header {
            text-align: center;
            padding: 100px 20px;
            background: radial-gradient(circle at top, #1a1a1a 0%, #0a0a0a 100%);
        }

        .main-title {
            font-size: clamp(2rem, 8vw, 3.5rem);
            font-weight: 900;
            letter-spacing: -1px;
            text-transform: uppercase;
            margin-bottom: 10px;
        }

        nav {
            position: sticky;
            top: 0;
            background: rgba(10, 10, 10, 0.85);
            backdrop-filter: blur(15px);
            border-bottom: 1px solid var(--border);
            z-index: 1000;
            display: flex;
            justify-content: center;
            padding: 15px;
            gap: 25px;
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

        nav a:hover { color: var(--text-main); }

        /* --- BUTTONS --- */
        .btn-cv {
            display: inline-flex;
            align-items: center;
            gap: 10px;
            margin-top: 20px;
            padding: 12px 28px;
            background-color: var(--accent);
            color: var(--bg-dark);
            text-decoration: none;
            font-weight: 800;
            font-size: 0.9rem;
            border-radius: 50px;
            transition: var(--transition);
        }

        .btn-cv:hover { transform: translateY(-3px); background-color: #fff; }

        /* --- SECTIONS --- */
        section {
            max-width: 1100px;
            margin: 0 auto;
            padding: 80px 25px;
        }

        h2 {
            font-size: 0.9rem;
            letter-spacing: 3px;
            color: var(--text-dim);
            margin-bottom: 40px;
            text-transform: uppercase;
            display: flex;
            align-items: center;
            gap: 15px;
        }

        h2::after { content: ""; height: 1px; background: var(--border); flex: 1; }

        /* --- GRID LAYOUTS --- */
        .grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 30px;
        }

        .card {
            background: var(--bg-card);
            border: 1px solid var(--border);
            border-radius: 16px;
            overflow: hidden;
            transition: var(--transition);
            text-decoration: none;
            color: inherit;
        }

        .card:hover { border-color: #444; transform: translateY(-8px); }

        .card img {
            width: 100%;
            height: 250px;
            object-fit: cover;
            filter: grayscale(100%);
            transition: 0.6s ease;
        }

        .card:hover img { filter: grayscale(0%); }

        .card-content { padding: 25px; }

        .figma-tag {
            display: inline-block;
            margin-top: 10px;
            font-size: 0.75rem;
            font-weight: 700;
            color: #F24E1E;
            text-transform: uppercase;
        }

        /* --- CHATBOT UI --- */
        #chat-widget {
            position: fixed;
            bottom: 90px;
            right: 25px;
            width: 320px;
            height: 450px;
            background: var(--bg-card);
            border: 1px solid var(--border);
            border-radius: 20px;
            display: none;
            flex-direction: column;
            box-shadow: 0 20px 50px rgba(0,0,0,0.6);
            z-index: 2000;
            overflow: hidden;
        }

        #chat-header {
            padding: 15px 20px;
            background: #1a1a1a;
            border-bottom: 1px solid var(--border);
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        #chat-messages {
            flex: 1;
            padding: 15px;
            overflow-y: auto;
            display: flex;
            flex-direction: column;
            gap: 10px;
        }

        .msg {
            max-width: 85%;
            padding: 10px 14px;
            border-radius: 15px;
            font-size: 0.85rem;
            line-height: 1.4;
            animation: fadeIn 0.3s ease;
        }

        .bot { background: var(--border); color: var(--text-main); align-self: flex-start; border-bottom-left-radius: 2px; }
        .user { background: var(--accent); color: var(--bg-dark); align-self: flex-end; border-bottom-right-radius: 2px; font-weight: 500; }

        #chat-input-area {
            padding: 15px;
            border-top: 1px solid var(--border);
            display: flex;
            gap: 10px;
        }

        #chat-input {
            flex: 1;
            background: transparent;
            border: none;
            color: white;
            outline: none;
            font-size: 0.85rem;
        }

        #chat-trigger {
            position: fixed;
            bottom: 25px;
            right: 25px;
            background: var(--accent);
            color: var(--bg-dark);
            width: 55px;
            height: 55px;
            border-radius: 50%;
            display: flex;
            justify-content: center;
            align-items: center;
            cursor: pointer;
            z-index: 1999;
            box-shadow: 0 10px 20px rgba(0,0,0,0.3);
            transition: var(--transition);
        }

        #chat-trigger:hover { transform: scale(1.1) rotate(5deg); }

        @keyframes fadeIn { from { opacity: 0; transform: translateY(5px); } to { opacity: 1; transform: translateY(0); } }

        @media (max-width: 600px) {
            #chat-widget { width: calc(100% - 50px); bottom: 85px; }
            .grid { grid-template-columns: 1fr; }
        }
    </style>
</head>
<body>

    <header>
        <h1 class="main-title">ANTHONY ESPINOSA</h1>
        <p style="color: var(--text-dim); letter-spacing: 2px; font-weight: 300;">STRATEGIC GRAPHICS DESIGNER | IT PROFESSIONAL</p>
        
        <a href="Professional Minimalist CV Resume.jpg" class="btn-cv" download="Anthony_Espinosa_CV.jpg">
            <i class="fas fa-file-download"></i> DOWNLOAD CV
        </a>
    </header>

    <nav>
        <a href="#about">About</a>
        <a href="#skills">Skills</a>
        <a href="#certificates">Certificates</a>
        <a href="#contact">Contact</a>
    </nav>

    <section id="about">
        <h2>ABOUT ME</h2>
        <div class="grid" style="align-items: center;">
            <img src="https://daverezaba123-qghmk.wordpress.com/wp-content/uploads/2026/04/img_20260421_1341155322485705782540295.png?w=815" alt="Anthony" style="width: 100%; border-radius: 20px;">
            <div>
                <p style="font-size: 1.1rem; color: var(--text-dim);">I am an IT professional with a dual focus on <strong>Technical Architecture</strong> and <strong>Visual Design</strong>. My goal is to build digital experiences that are as efficient as they are beautiful.</p>
            </div>
        </div>
    </section>

    <section id="skills">
        <h2>SKILLS & PROJECTS</h2>
        <div class="grid">
            <a href="https://www.figma.com/proto/YXytqyexSEyzcwuYyX9gi2/Untitled?node-id=2-109&t=j7OVhsdOplpEgxmC-1" target="_blank" class="card">
                <div style="height: 250px; background: #1e1e1e; display: flex; align-items: center; justify-content: center;">
                    <i class="fab fa-figma" style="font-size: 5rem; color: #F24E1E;"></i>
                </div>
                <div class="card-content">
                    <h3>UI/UX Design</h3>
                    <p>Interface prototypes and design systems built for high-performance apps.</p>
                    <span class="figma-tag">View Figma Prototype <i class="fas fa-external-link-alt"></i></span>
                </div>
            </a>

            <div class="card">
                <img src="https://daverezaba123-qghmk.wordpress.com/wp-content/uploads/2026/04/received_267360033126596614052547090387034825.jpeg?w=632" alt="Layout">
                <div class="card-content">
                    <h3>Design & Layout</h3>
                    <p>Expertise in T-shirt sublimation layout and brand identity systems.</p>
                </div>
            </div>

            <div class="card">
                <img src="https://daverezaba123-qghmk.wordpress.com/wp-content/uploads/2026/04/received_14720831838393725292710248625092296.jpeg?w=683" alt="Dev">
                <div class="card-content">
                    <h3>Technical IT</h3>
                    <p>Physics-based game development and MERN stack interest.</p>
                </div>
            </div>
        </div>
    </section>

    <section id="certificates">
        <h2>CERTIFICATES</h2>
        <div class="card" style="max-width: 600px; margin: 0 auto;">
            <img src="https://daverezaba123-qghmk.wordpress.com/wp-content/uploads/2026/04/received_9445525915134996693128524351569481.jpeg?w=716" alt="Cyber Security">
            <div class="card-content">
                <h3>Cyber Security Completion</h3>
                <p>Verified mastery in network defense and fundamental security practices.</p>
            </div>
        </div>
    </section>

    <section id="contact" style="text-align: center;">
        <h2>CONTACT</h2>
        <p style="font-size: 1.5rem; font-weight: 700; margin-bottom: 20px;">Let's build something together.</p>
        <p style="color: var(--text-dim);">Email: espinosaanthony50@gmail.com</p>
        <div style="margin-top: 30px; font-size: 1.8rem; display: flex; justify-content: center; gap: 40px;">
            <a href="mailto:espinosaanthony50@gmail.com" style="color:var(--text-dim)"><i class="fas fa-envelope"></i></a>
            <a href="https://github.com" target="_blank" style="color:var(--text-dim)"><i class="fab fa-github"></i></a>
            <a href="https://www.facebook.com/anthony.ortegaespinosa.1" target="_blank" style="color:var(--text-dim)"><i class="fab fa-facebook-f"></i></a>
        </div>
    </section>

    <div id="chat-trigger" onclick="toggleChat()"><i class="fas fa-robot"></i></div>
    <div id="chat-widget">
        <div id="chat-header">
            <span style="font-weight: 800; font-size: 0.7rem; letter-spacing: 1px;">AE ASSISTANT</span>
            <i class="fas fa-times" onclick="toggleChat()" style="cursor:pointer; opacity: 0.5;"></i>
        </div>
        <div id="chat-messages" id="chatMessages">
            <div class="msg bot">Hi! I'm Anthony's assistant. You can ask me about his IT skills, Figma projects, or how to contact him!</div>
        </div>
        <div id="chat-input-area">
            <input type="text" id="chat-input" placeholder="Ask me something..." onkeypress="if(event.key==='Enter') handleChat()">
            <i class="fas fa-paper-plane" onclick="handleChat()" style="cursor:pointer; color: var(--text-dim);"></i>
        </div>
    </div>

    <script>
        function toggleChat() {
            const chat = document.getElementById('chat-widget');
            chat.style.display = (chat.style.display === 'flex') ? 'none' : 'flex';
        }

        function handleChat() {
            const input = document.getElementById('chat-input');
            const messages = document.getElementById('chat-messages');
            const text = input.value.trim();

            if (text) {
                // Add User Message
                appendMsg(text, 'user');
                input.value = '';

                // Bot Logic
                setTimeout(() => {
                    const query = text.toLowerCase();
                    let reply = "I'm not sure about that, but Anthony is a great IT professional! Would you like his email?";

                    if (query.includes('skill') || query.includes('can do')) {
                        reply = "Anthony specializes in UI/UX Design (Figma), Graphic Layout, 3D Modeling, and Web Development.";
                    } else if (query.includes('figma') || query.includes('design')) {
                        reply = "You can see his latest UI project by clicking the Figma card in the Skills section!";
                    } else if (query.includes('contact') || query.includes('email')) {
                        reply = "You can reach Anthony at: espinosaanthony50@gmail.com. He usually responds within 24 hours.";
                    } else if (query.includes('hello') || query.includes('hi')) {
                        reply = "Hello! Ready to learn more about Anthony's professional background?";
                    } else if (query.includes('mern')) {
                        reply = "Yes! Anthony is highly interested in the MERN stack (MongoDB, Express, React, Node.js).";
                    }

                    appendMsg(reply, 'bot');
                }, 700);
            }
        }

        function appendMsg(text, sender) {
            const messages = document.getElementById('chat-messages');
            const div = document.createElement('div');
            div.className = `msg ${sender}`;
            div.innerText = text;
            messages.appendChild(div);
            messages.scrollTop = messages.scrollHeight;
        }
    </script>
</body>
</html>
