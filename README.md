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

        /* --- NAVIGATION --- */
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

        nav a:hover { color: var(--text-main); }

        /* --- HEADER --- */
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
            border: none;
        }

        .btn-cv:hover {
            transform: translateY(-3px);
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

        .card:hover { border-color: #444; transform: translateY(-10px); }

        .card img {
            width: 100%;
            height: 280px;
            object-fit: cover;
            filter: grayscale(100%);
            transition: 0.8s cubic-bezier(0.16, 1, 0.3, 1);
        }

        .card:hover img { filter: grayscale(0%); transform: scale(1.05); }

        .card-content { padding: 30px; flex-grow: 1; }

        /* --- CERTIFICATE FIX --- */
        .cert-card img {
            height: auto;
            max-height: 500px;
            object-fit: contain;
            background: #000;
        }

        /* --- CONTACT FIX --- */
        .contact-container {
            text-align: center;
            max-width: 600px;
            margin: 0 auto;
        }

        .social-links {
            display: flex;
            justify-content: center;
            gap: 30px;
            margin-top: 30px;
        }

        .social-links a {
            color: var(--text-dim);
            font-size: 1.8rem;
            transition: var(--transition);
        }

        .social-links a:hover {
            color: var(--text-main);
            transform: translateY(-5px);
        }

        /* --- CHATBOT --- */
        #chatbot-container { position: fixed; bottom: 30px; right: 30px; z-index: 2000; }
        #chat-btn {
            width: 60px; height: 60px; background: var(--text-main); color: var(--bg-dark);
            border-radius: 50%; display: flex; align-items: center; justify-content: center;
            cursor: pointer; box-shadow: 0 10px 30px rgba(0,0,0,0.4); font-size: 1.4rem;
        }
        #chat-box {
            position: absolute; bottom: 80px; right: 0; width: 320px; height: 480px;
            background: var(--bg-card); border: 1px solid var(--border); border-radius: 24px;
            display: none; flex-direction: column; overflow: hidden; box-shadow: 0 25px 50px rgba(0,0,0,0.6);
        }
        #chat-header { padding: 18px 20px; background: #1a1a1a; display: flex; justify-content: space-between; align-items: center; }
        #chat-messages { flex: 1; padding: 20px; overflow-y: auto; display: flex; flex-direction: column; gap: 12px; }
        .msg { max-width: 85%; padding: 12px 16px; border-radius: 18px; font-size: 0.85rem; }
        .bot-msg { background: var(--border); color: #fff; align-self: flex-start; border-bottom-left-radius: 4px; }
        .user-msg { background: var(--text-main); color: var(--bg-dark); align-self: flex-end; border-bottom-right-radius: 4px; }
        #chat-input-area { padding: 15px 20px; border-top: 1px solid var(--border); display: flex; gap: 12px; }
        #chat-input-area input { flex: 1; background: transparent; border: none; color: #fff; outline: none; }
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
        <p style="color: var(--text-dim); letter-spacing: 2px;">STRATEGIC GRAPHICS DESIGNER | IT PROFESSIONAL</p>
        <a href="Professional Minimalist CV Resume.jpg" class="btn-cv" download>
            <i class="fas fa-file-pdf"></i> DOWNLOAD CV
        </a>
    </header>
    
    <section id="about">
        <h2>ABOUT ME</h2>
        <div class="grid" style="align-items: center;">
            <img src="https://daverezaba123-qghmk.wordpress.com/wp-content/uploads/2026/04/img_20260421_1341155322485705782540295.png?w=815" alt="Anthony" style="width: 100%; border-radius: 20px;">
            <div>
                <p style="font-size: 1.25rem; font-weight: 500;">Strategic Graphic Designer focused on high-performing visual assets and MERN stack development.</p>
                <p style="margin-top: 25px; color: var(--text-dim);">Expert in Adobe Creative Suite and brand systems, bridging IT infrastructure with creative design architecture.</p>
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
                    <p>Prototyping and design systems built in Figma.</p>
                </div>
            </a>
            <div class="card">
                <img src="https://daverezaba123-qghmk.wordpress.com/wp-content/uploads/2026/04/received_267360033126596614052547090387034825.jpeg?w=632" alt="Layout">
                <div class="card-content"><h3>Design & Layout</h3><p>T-shirt sublimation and brand identity.</p></div>
            </div>
            <div class="card">
                <img src="https://daverezaba123-qghmk.wordpress.com/wp-content/uploads/2026/04/received_14720831838393725292710248625092296.jpeg?w=683" alt="IT">
                <div class="card-content"><h3>Technical IT</h3><p>SEO and JS-based simulations.</p></div>
            </div>
        </div>
    </section>

    <section id="certificates">
        <h2>CERTIFICATES</h2>
        <div class="card cert-card" style="max-width: 800px; margin: 0 auto;">
            <img src="https://daverezaba123-qghmk.wordpress.com/wp-content/uploads/2026/04/received_9445525915134996693128524351569481.jpeg?w=716" alt="Cyber Security">
            <div class="card-content">
                <h3>Cyber Security Completion</h3>
                <p>Fundamental mastery in network defense and security practices.</p>
            </div>
        </div>
    </section>

    <section id="contact">
        <h2>CONTACT</h2>
        <div class="contact-container">
            <p style="font-size: 1.5rem; font-weight: 700;">Ready to collaborate?</p>
            <p style="color: var(--text-dim);">Phone: 09815600546 | Email: espinosaanthony50@gmail.com</p>
            <div class="social-links">
                <a href="mailto:espinosaanthony50@gmail.com"><i class="fas fa-envelope"></i></a>
                <a href="https://www.facebook.com/anthony.ortegaespinosa.1" target="_blank"><i class="fab fa-facebook-f"></i></a>
                <a href="https://www.instagram.com/toni_2high" target="_blank"><i class="fab fa-instagram"></i></a>
                <a href="https://github.com" target="_blank"><i class="fab fa-github"></i></a>
            </div>
        </div>
    </section>

    <div id="chatbot-container">
        <div id="chat-box">
            <div id="chat-header">
                <span style="font-weight: 800; font-size: 0.75rem;">AI ASSISTANT</span>
                <i class="fas fa-times" onclick="toggleChat()" style="cursor:pointer; opacity: 0.5;"></i>
            </div>
            <div id="chat-messages">
                <div class="msg bot-msg">Hello! I'm Anthony's AI assistant. Ask me about his work!</div>
            </div>
            <div id="chat-input-area">
                <input type="text" id="user-input" placeholder="Ask a question..." onkeypress="if(event.key==='Enter') sendMessage()">
                <i class="fas fa-paper-plane" onclick="sendMessage()" style="cursor:pointer;"></i>
            </div>
        </div>
        <div id="chat-btn" onclick="toggleChat()"><i class="fas fa-robot"></i></div>
    </div>

    <script>
        function toggleChat() {
            const cb = document.getElementById('chat-box');
            cb.style.display = cb.style.display === 'flex' ? 'none' : 'flex';
        }

        function sendMessage() {
            const input = document.getElementById('user-input');
            const msgs = document.getElementById('chat-messages');
            if (input.value.trim() !== "") {
                const uDiv = document.createElement('div');
                uDiv.className = 'msg user-msg';
                uDiv.textContent = input.value;
                msgs.appendChild(uDiv);
                
                const q = input.value.toLowerCase();
                input.value = "";
                msgs.scrollTop = msgs.scrollHeight;

                setTimeout(() => {
                    const bDiv = document.createElement('div');
                    bDiv.className = 'msg bot-msg';
                    if (q.includes("skill") || q.includes("mern")) {
                        bDiv.textContent = "Anthony is skilled in MERN Stack, UI/UX Design, and Graphic Layout.";
                    } else if (q.includes("contact") || q.includes("hire")) {
                        bDiv.textContent = "You can email him at espinosaanthony50@gmail.com.";
                    } else {
                        bDiv.textContent = "I'm here to help! Ask about Anthony's IT or design expertise.";
                    }
                    msgs.appendChild(bDiv);
                    msgs.scrollTop = msgs.scrollHeight;
                }, 1000);
            }
        }
    </script>
</body>
</html>
