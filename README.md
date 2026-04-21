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

        /* --- UPGRADED CHATBOT UI --- */
        #chat-widget {
            position: fixed;
            bottom: 100px;
            right: 30px;
            width: 350px;
            height: 500px;
            background: rgba(20, 20, 20, 0.8);
            backdrop-filter: blur(25px) saturate(150%);
            -webkit-backdrop-filter: blur(25px);
            border: 1px solid rgba(255, 255, 255, 0.1);
            border-radius: 24px;
            display: none;
            flex-direction: column;
            box-shadow: 0 30px 60px rgba(0,0,0,0.8);
            z-index: 2100;
            overflow: hidden;
            animation: chatSlide 0.4s cubic-bezier(0.16, 1, 0.3, 1);
        }

        @keyframes chatSlide {
            from { opacity: 0; transform: translateY(20px) scale(0.95); }
            to { opacity: 1; transform: translateY(0) scale(1); }
        }

        #chat-header {
            padding: 20px;
            background: rgba(255, 255, 255, 0.03);
            border-bottom: 1px solid rgba(255, 255, 255, 0.05);
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .bot-status {
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .status-dot {
            width: 8px;
            height: 8px;
            background: #00ff88;
            border-radius: 50%;
            box-shadow: 0 0 10px #00ff88;
        }

        #chat-messages {
            flex: 1;
            padding: 20px;
            overflow-y: auto;
            display: flex;
            flex-direction: column;
            gap: 12px;
            scrollbar-width: thin;
            scrollbar-color: var(--border) transparent;
        }

        .msg {
            max-width: 85%;
            padding: 12px 16px;
            border-radius: 18px;
            font-size: 0.9rem;
            line-height: 1.5;
        }

        .bot { 
            background: rgba(255, 255, 255, 0.08); 
            color: #fff; 
            align-self: flex-start; 
            border-bottom-left-radius: 4px;
        }

        .user { 
            background: #fff; 
            color: #000; 
            align-self: flex-end; 
            border-bottom-right-radius: 4px; 
            font-weight: 500;
        }

        #chat-input-area {
            padding: 20px;
            background: rgba(0,0,0,0.2);
            border-top: 1px solid rgba(255, 255, 255, 0.05);
            display: flex;
            gap: 12px;
            align-items: center;
        }

        #chat-input {
            flex: 1;
            background: rgba(255, 255, 255, 0.05);
            border: 1px solid rgba(255, 255, 255, 0.1);
            border-radius: 12px;
            padding: 10px 15px;
            color: white;
            outline: none;
            font-size: 0.9rem;
            transition: var(--transition);
        }

        #chat-trigger {
            position: fixed;
            bottom: 30px;
            right: 30px;
            background: #fff;
            color: #000;
            width: 60px;
            height: 60px;
            border-radius: 50%;
            display: flex;
            justify-content: center;
            align-items: center;
            cursor: pointer;
            z-index: 2000;
            box-shadow: 0 10px 30px rgba(0,0,0,0.5);
            transition: var(--transition);
        }

        .pulse {
            position: absolute;
            width: 100%;
            height: 100%;
            border-radius: 50%;
            background: rgba(255,255,255,0.4);
            animation: pulse-ring 2s infinite;
        }

        @keyframes pulse-ring {
            0% { transform: scale(0.8); opacity: 0.5; }
            100% { transform: scale(1.5); opacity: 0; }
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
                <p style="font-size: 1.1rem; color: var(--text-dim);">I am an IT student at Central Philippine State University, bridging the gap between technical efficiency and user experience. As an aspiring full-stack developer, I focus on building digital solutions that are both robust and visually engaging.</p>
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
                    <p>Strategic interface prototypes and design systems built in Figma.</p>
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
                    <p>Development focus on the MERN stack and data workflow simulations.</p>
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

    <div id="chat-trigger" onclick="toggleChat()">
        <div class="pulse"></div>
        <i class="fas fa-comment-alt"></i>
    </div>

    <div id="chat-widget">
        <div id="chat-header">
            <div class="bot-status">
                <div class="status-dot"></div>
                <div>
                    <div style="font-weight: 800; font-size: 0.75rem; letter-spacing: 1px;">ANTHONY AI</div>
                    <div style="font-size: 0.6rem; color: #00ff88; text-transform: uppercase;">Always Online</div>
                </div>
            </div>
            <i class="fas fa-times" onclick="toggleChat()" style="cursor:pointer; opacity: 0.5;"></i>
        </div>
        <div id="chat-messages">
            <div class="msg bot">Hello! I'm Anthony's personal AI assistant. How can I help you today?</div>
        </div>
        <div id="chat-input-area">
            <input type="text" id="chat-input" placeholder="Ask about skills, Figma, or contact..." onkeypress="if(event.key==='Enter') handleChat()">
            <button onclick="handleChat()" style="background: none; border: none; cursor: pointer; color: #fff;">
                <i class="fas fa-paper-plane"></i>
            </button>
        </div>
    </div>

    <script>
        function toggleChat() {
            const chat = document.getElementById('chat-widget');
            const isVisible = chat.style.display === 'flex';
            chat.style.display = isVisible ? 'none' : 'flex';
        }

        function handleChat() {
            const input = document.getElementById('chat-input');
            const text = input.value.trim();

            if (text) {
                appendMsg(text, 'user');
                input.value = '';

                setTimeout(() => {
                    const query = text.toLowerCase();
                    let reply = "";

                    // --- SMART RESPONSE LOGIC ---
                    if (query.includes('skill') || query.includes('can do') || query.includes('expertise')) {
                        reply = "Anthony is an IT professional skilled in UI/UX Design (Figma), Graphic Layout, and Web Development. He has a particular interest in the MERN stack.";
                    } 
                    else if (query.includes('mern') || query.includes('react') || query.includes('node')) {
                        reply = "Yes! Anthony is an aspiring Full-Stack Developer specializing in the MERN stack (MongoDB, Express, React, and Node.js).";
                    }
                    else if (query.includes('project') || query.includes('work') || query.includes('build')) {
                        reply = "Anthony has developed several projects, including an Academic Management System (Capstone), a Personal Finance Tracker using Firebase, and various logic engines.";
                    }
                    else if (query.includes('figma') || query.includes('design') || query.includes('ui')) {
                        reply = "Anthony is a 'Digital Architect' who uses Figma to bridge the gap between technical efficiency and user experience. You can see his prototype in the Skills section!";
                    }
                    else if (query.includes('contact') || query.includes('email') || query.includes('hire') || query.includes('phone')) {
                        reply = "You can reach Anthony at espinosaanthony50@gmail.com or call 09815600546. He is currently open to new collaborations!";
                    }
                    else if (query.includes('education') || query.includes('school') || query.includes('college')) {
                        reply = "Anthony is an Information Technology student at Central Philippine State University (CPSU).";
                    }
                    else if (query.includes('hello') || query.includes('hi') || query.includes('hey')) {
                        reply = "Hello! I'm Anthony's AI assistant. Ask me about his MERN stack projects, his design skills, or how to contact him.";
                    }
                    else if (query.includes('certif') || query.includes('cyber')) {
                        reply = "Anthony holds a verified certificate in Cyber Security, focusing on network defense and security strategy.";
                    }
                    else {
                        reply = "That's a great question! While I'm still learning, I can tell you that Anthony is a dedicated IT student and aspiring developer. Would you like his contact info?";
                    }

                    appendMsg(reply, 'bot');
                }, 600);
            }
        }

        function appendMsg(text, sender) {
            const messages = document.getElementById('chat-messages');
            const div = document.createElement('div');
            div.className = `msg ${sender}`;
            div.innerText = text;
            messages.appendChild(div);
            
            messages.scrollTo({
                top: messages.scrollHeight,
                behavior: 'smooth'
            });
        }
    </script>
</body>
</html>
