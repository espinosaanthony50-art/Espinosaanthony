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

        /* --- AI CHATBOT STYLES --- */
        #chatbot-container {
            position: fixed;
            bottom: 30px;
            right: 30px;
            z-index: 2000;
        }

        #chat-btn {
            width: 60px;
            height: 60px;
            background: var(--text-main);
            color: var(--bg-dark);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            box-shadow: 0 10px 30px rgba(0,0,0,0.4);
            transition: var(--transition);
            font-size: 1.4rem;
        }

        #chat-btn:hover { transform: scale(1.1) rotate(5deg); }

        #chat-box {
            position: absolute;
            bottom: 80px;
            right: 0;
            width: 320px;
            height: 480px;
            background: var(--bg-card);
            border: 1px solid var(--border);
            border-radius: 24px;
            display: none;
            flex-direction: column;
            overflow: hidden;
            box-shadow: 0 25px 50px rgba(0,0,0,0.6);
            backdrop-filter: blur(10px);
        }

        #chat-header {
            padding: 18px 20px;
            background: #1a1a1a;
            border-bottom: 1px solid var(--border);
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        #chat-messages {
            flex: 1;
            padding: 20px;
            overflow-y: auto;
            display: flex;
            flex-direction: column;
            gap: 12px;
        }

        .msg {
            max-width: 85%;
            padding: 12px 16px;
            border-radius: 18px;
            font-size: 0.85rem;
            line-height: 1.5;
            animation: fadeIn 0.3s ease forwards;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }

        .bot-msg {
            background: var(--border);
            color: var(--text-main);
            align-self: flex-start;
            border-bottom-left-radius: 4px;
        }

        .user-msg {
            background: var(--text-main);
            color: var(--bg-dark);
            align-self: flex-end;
            border-bottom-right-radius: 4px;
            font-weight: 500;
        }

        .typing {
            font-style: italic;
            font-size: 0.75rem;
            color: var(--text-dim);
            margin-bottom: 10px;
            display: none;
        }

        #chat-input-area {
            padding: 15px 20px;
            border-top: 1px solid var(--border);
            display: flex;
            gap: 12px;
            background: #0d0d0d;
        }

        #chat-input-area input {
            flex: 1;
            background: transparent;
            border: none;
            color: #fff;
            outline: none;
            font-size: 0.85rem;
        }

        /* --- RESPONSIVE --- */
        @media (max-width: 750px) {
            header { padding: 100px 20px 60px; }
            section { padding: 80px 20px; }
            .grid { grid-template-columns: 1fr; }
            #chat-box { width: 280px; height: 420px; right: -10px; }
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
        
        <a href="Professional Minimalist CV Resume.jpg" class="btn-cv" download>
            <i class="fas fa-file-pdf"></i> DOWNLOAD CV
        </a>
    </header>
    
    <section id="about">
        <h2>ABOUT ME</h2>
        <div class="grid" style="align-items: center;">
            <div>
                <img src="https://daverezaba123-qghmk.wordpress.com/wp-content/uploads/2026/04/img_20260421_1341155322485705782540295.png?w=815" alt="Anthony" style="width: 100%; border-radius: 20px; box-shadow: 0 20px 40px rgba(0,0,0,0.3);">
            </div>
            <div>
                <p style="font-size: 1.25rem; line-height: 1.8; font-weight: 500;">Strategic Graphic Designer with a proven track record of translating complex briefs into high-performing visual assets.</p>
                <p style="margin-top: 25px; color: var(--text-dim);">Expert in Adobe Creative Suite and brand systems, based in the Philippines with a Bachelor in Information Technology from Central Philippine State University. I bridge the gap between technical IT infrastructure and creative digital architecture.</p>
            </div>
        </div>
    </section>

    <section id="skills">
        <h2>SKILLS & PROJECTS</h2>
        <div class="grid">
            <a href="https://www.figma.com/proto/YXytqyexSEyzcwuYyX9gi2/Untitled?node-id=2-109" target="_blank" class="card">
                <div style="height: 280px; background: #1e1e1e; display: flex; align-items: center; justify-content: center;">
                    <i class="fab fa-figma" style="font-size: 5rem; color: #F24E1E;"></i>
                </div>
                <div class="card-content">
                    <h3>UI/UX Design</h3>
                    <p>Interface prototypes and design systems built for high-conversion user experiences.</p>
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
                    <p>SEO optimization and custom JavaScript-based physics simulations.</p>
                </div>
            </div>
        </div>
    </section>

    <section id="contact">
        <h2>CONTACT</h2>
        <div style="text-align: center;">
            <p style="font-size: 1.5rem; color: #fff; font-weight: 700;">Ready to collaborate?</p>
            <p style="color: var(--text-dim); margin-bottom: 20px;">Email: espinosaanthony50@gmail.com</p>
            <div class="social-icons">
                <a href="mailto:espinosaanthony50@gmail.com"><i class="fas fa-envelope"></i></a>
                <a href="https://github.com" target="_blank"><i class="fab fa-github"></i></a>
                <a href="https://www.instagram.com/toni_2high" target="_blank"><i class="fab fa-instagram"></i></a>
            </div>
        </div>
    </section>

    <div id="chatbot-container">
        <div id="chat-box">
            <div id="chat-header">
                <span style="font-weight: 800; font-size: 0.75rem; letter-spacing: 1px; color: var(--text-main);">AI ASSISTANT</span>
                <i class="fas fa-times" onclick="toggleChat()" style="cursor:pointer; opacity: 0.5;"></i>
            </div>
            <div id="chat-messages">
                <div class="msg bot-msg">Hello! I'm Anthony's AI assistant. How can I help you explore his work today?</div>
            </div>
            <div id="typing-indicator" class="typing" style="margin-left: 20px;">AI is thinking...</div>
            <div id="chat-input-area">
                <input type="text" id="user-input" placeholder="Ask about skills, contact, or projects..." onkeypress="handleKey(event)">
                <i class="fas fa-paper-plane" onclick="sendMessage()" style="cursor:pointer; color: var(--text-main);"></i>
            </div>
        </div>
        <div id="chat-btn" onclick="toggleChat()">
            <i class="fas fa-robot"></i>
        </div>
    </div>

    <script>
        function toggleChat() {
            const chatBox = document.getElementById('chat-box');
            chatBox.style.display = chatBox.style.display === 'flex' ? 'none' : 'flex';
        }

        function handleKey(e) {
            if (e.key === 'Enter') sendMessage();
        }

        function sendMessage() {
            const input = document.getElementById('user-input');
            const messages = document.getElementById('chat-messages');
            const typing = document.getElementById('typing-indicator');
            const val = input.value.trim();
            
            if (val !== "") {
                const userDiv = document.createElement('div');
                userDiv.className = 'msg user-msg';
                userDiv.textContent = val;
                messages.appendChild(userDiv);
                input.value = "";
                messages.scrollTop = messages.scrollHeight;

                // Show Typing Indicator
                typing.style.display = 'block';

                setTimeout(() => {
                    typing.style.display = 'none';
                    const botDiv = document.createElement('div');
                    botDiv.className = 'msg bot-msg';
                    
                    const query = val.toLowerCase();
                    if (query.includes("skill") || query.includes("do")) {
                        botDiv.textContent = "Anthony is an IT professional specializing in UI/UX Design (Figma), Graphic Layout, and Web Development (MERN Stack).";
                    } else if (query.includes("contact") || query.includes("email") || query.includes("hire")) {
                        botDiv.textContent = "You can reach Anthony at espinosaanthony50@gmail.com or call 09815600546.";
                    } else if (query.includes("mern") || query.includes("code")) {
                        botDiv.textContent = "He is an aspiring Full-Stack Developer with a focus on MongoDB, Express, React, and Node.js.";
                    } else if (query.includes("hi") || query.includes("hello")) {
                        botDiv.textContent = "Hi there! I'm an AI trained on Anthony's portfolio. Ask me about his projects or education!";
                    } else {
                        botDiv.textContent = "That's a great question! Anthony's expertise covers both creative design and technical IT infrastructure. Would you like to see his projects?";
                    }
                    
                    messages.appendChild(botDiv);
                    messages.scrollTop = messages.scrollHeight;
                }, 1200);
            }
        }
    </script>
</body>
</html>
