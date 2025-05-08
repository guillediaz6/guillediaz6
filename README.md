<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

  
    <style>
        :root {
            --primary: #2b2d42;
            --secondary: #8d99ae;
            --accent: #ef233c;
            --light: #edf2f4;
            --dark: #1a1a2e;
            --tech-js: #f0db4f;
            --tech-java: #5382a1;
            --tech-sql: #00758f;
            --tech-html: #e34c26;
            --tech-css: #2965f1;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background-color: var(--dark);
            color: var(--light);
            overflow-x: hidden;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 2rem;
        }

        header {
            text-align: center;
            position: relative;
            padding: 3rem 0;
            overflow: hidden;
        }

        .header-bg {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(135deg, var(--primary) 0%, var(--dark) 100%);
            z-index: -2;
        }

        .header-pattern {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-image: radial-gradient(circle, rgba(255,255,255,0.1) 1px, transparent 1px);
            background-size: 20px 20px;
            z-index: -1;
            opacity: 0.5;
        }

        .profile-pic {
            width: 150px;
            height: 150px;
            border-radius: 50%;
            object-fit: cover;
            border: 5px solid var(--light);
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
            transition: all 0.3s ease;
            margin-bottom: 1.5rem;
        }

        .profile-pic:hover {
            transform: scale(1.05) rotate(5deg);
            box-shadow: 0 15px 40px rgba(0, 0, 0, 0.4);
        }

        h1 {
            font-size: 3rem;
            margin-bottom: 0.5rem;
            background: linear-gradient(to right, var(--light), var(--secondary));
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.2);
        }

        .title {
            font-size: 1.5rem;
            color: var(--secondary);
            margin-bottom: 2rem;
            position: relative;
            display: inline-block;
        }

        .title::after {
            content: '';
            position: absolute;
            bottom: -10px;
            left: 50%;
            transform: translateX(-50%);
            width: 50%;
            height: 3px;
            background: linear-gradient(to right, transparent, var(--accent), transparent);
            border-radius: 3px;
        }

        .social-links {
            display: flex;
            justify-content: center;
            gap: 1.5rem;
            margin-bottom: 2rem;
        }

        .social-link {
            color: var(--light);
            font-size: 1.5rem;
            transition: all 0.3s ease;
        }

        .social-link:hover {
            color: var(--accent);
            transform: translateY(-3px);
        }

        .tech-section {
            margin: 3rem 0;
            text-align: center;
        }

        h2 {
            font-size: 2rem;
            margin-bottom: 2rem;
            color: var(--light);
            position: relative;
            display: inline-block;
        }

        h2::before, h2::after {
            content: '✧';
            position: absolute;
            top: 50%;
            transform: translateY(-50%);
            color: var(--accent);
            font-size: 1.2rem;
        }

        h2::before {
            left: -40px;
        }

        h2::after {
            right: -40px;
        }

        .tech-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
            gap: 2rem;
            margin-top: 2rem;
        }

        .tech-card {
            background: rgba(255, 255, 255, 0.05);
            border-radius: 15px;
            padding: 1.5rem;
            transition: all 0.3s ease;
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.1);
            position: relative;
            overflow: hidden;
        }

        .tech-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 15px 30px rgba(0, 0, 0, 0.3);
            border-color: rgba(255, 255, 255, 0.3);
        }

        .tech-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 5px;
            background: linear-gradient(to right, var(--accent), transparent);
        }

        .tech-icon {
            font-size: 3rem;
            margin-bottom: 1rem;
        }

        .tech-name {
            font-size: 1.2rem;
            margin-bottom: 0.5rem;
        }

        .tech-desc {
            font-size: 0.9rem;
            color: var(--secondary);
        }

        .js { color: var(--tech-js); }
        .java { color: var(--tech-java); }
        .sql { color: var(--tech-sql); }
        .html { color: var(--tech-html); }
        .css { color: var(--tech-css); }

        .floating-elements {
            position: absolute;
            width: 100%;
            height: 100%;
            top: 0;
            left: 0;
            pointer-events: none;
            z-index: -1;
            overflow: hidden;
        }

        .floating-element {
            position: absolute;
            opacity: 0.1;
            animation: float 15s infinite linear;
        }

        .floating-element:nth-child(1) {
            top: 20%;
            left: 10%;
            font-size: 2rem;
            animation-delay: 0s;
        }

        .floating-element:nth-child(2) {
            top: 60%;
            left: 80%;
            font-size: 3rem;
            animation-delay: 2s;
            animation-duration: 20s;
        }

        .floating-element:nth-child(3) {
            top: 30%;
            left: 50%;
            font-size: 1.5rem;
            animation-delay: 5s;
            animation-duration: 12s;
        }

        .floating-element:nth-child(4) {
            top: 70%;
            left: 30%;
            font-size: 2.5rem;
            animation-delay: 7s;
            animation-duration: 18s;
        }

        @keyframes float {
            0% {
                transform: translateY(0) rotate(0deg);
            }
            50% {
                transform: translateY(-50px) rotate(180deg);
            }
            100% {
                transform: translateY(0) rotate(360deg);
            }
        }

        .projects-btn {
            display: inline-block;
            padding: 0.8rem 2rem;
            background: linear-gradient(45deg, var(--accent), #f15e5e);
            color: white;
            border-radius: 50px;
            text-decoration: none;
            font-weight: bold;
            margin-top: 1rem;
            transition: all 0.3s ease;
            box-shadow: 0 5px 15px rgba(239, 35, 60, 0.3);
            position: relative;
            overflow: hidden;
        }

        .projects-btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 8px 20px rgba(239, 35, 60, 0.4);
        }

        .projects-btn::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.2), transparent);
            transition: 0.5s;
        }

        .projects-btn:hover::before {
            left: 100%;
        }

        footer {
            text-align: center;
            padding: 2rem 0;
            margin-top: 3rem;
            border-top: 1px solid rgba(255, 255, 255, 0.1);
            color: var(--secondary);
        }

        .typing-effect {
            display: inline-block;
            position: relative;
        }

        .typing-effect::after {
            content: '|';
            position: absolute;
            right: -8px;
            animation: blink 0.7s infinite;
        }

        @keyframes blink {
            0%, 100% { opacity: 1; }
            50% { opacity: 0; }
        }

        @media (max-width: 768px) {
            h1 {
                font-size: 2rem;
            }
            
            .title {
                font-size: 1.2rem;
            }
            
            .tech-grid {
                grid-template-columns: repeat(auto-fit, minmax(120px, 1fr));
            }
            
            h2::before, h2::after {
                display: none;
            }
        }
    </style>
</head>
<body>
    <div class="floating-elements">
        <div class="floating-element">{ }</div>
        <div class="floating-element">< ></div>
        <div class="floating-element">( )</div>
        <div class="floating-element">[ ]</div>
    </div>

    <div class="container">
        <header>
            <div class="header-bg"></div>
            <div class="header-pattern"></div>
            
            <img src="https://via.placeholder.com/150" alt="Tu foto de perfil" class="profile-pic">
            
            <h1>TU NOMBRE</h1>
            
            <div class="title typing-effect">Desarrollador Multiplataforma</div>
            
            <div class="social-links">
                <a href="https://github.com/tuusuario" class="social-link" target="_blank">
                    <i class="fab fa-github"></i>
                </a>
                <a href="#" class="social-link" target="_blank">
                    <i class="fab fa-linkedin"></i>
                </a>
                <a href="#" class="social-link" target="_blank">
                    <i class="fab fa-twitter"></i>
                </a>
                <a href="#" class="social-link" target="_blank">
                    <i class="fas fa-envelope"></i>
                </a>
            </div>
            
            <a href="#tech" class="projects-btn">Mis Tecnologías</a>
        </header>
        
        <section class="tech-section" id="tech">
            <h2>Tecnologías Principales</h2>
            
            <div class="tech-grid">
                <div class="tech-card">
                    <div class="tech-icon js">
                        <i class="fab fa-js"></i>
                    </div>
                    <h3 class="tech-name">JavaScript</h3>
                    <p class="tech-desc">Desarrollo frontend y backend con Node.js</p>
                </div>
                
                <div class="tech-card">
                    <div class="tech-icon java">
                        <i class="fab fa-java"></i>
                    </div>
                    <h3 class="tech-name">Java</h3>
                    <p class="tech-desc">Aplicaciones empresariales y Android</p>
                </div>
                
                <div class="tech-card">
                    <div class="tech-icon sql">
                        <i class="fas fa-database"></i>
                    </div>
                    <h3 class="tech-name">SQL</h3>
                    <p class="tech-desc">Diseño y optimización de bases de datos</p>
                </div>
                
                <div class="tech-card">
                    <div class="tech-icon html">
                        <i class="fab fa-html5"></i>
                    </div>
                    <h3 class="tech-name">HTML5</h3>
                    <p class="tech-desc">Estructura semántica y accesibilidad</p>
                </div>
                
                <div class="tech-card">
                    <div class="tech-icon css">
                        <i class="fab fa-css3-alt"></i>
                    </div>
                    <h3 class="tech-name">CSS3</h3>
                    <p class="tech-desc">Diseño responsive y animaciones</p>
                </div>
            </div>
        </section>
        
        <footer>
            <p>© <span id="year"></span> - Hecho con ❤️ y código</p>
        </footer>
    </div>

    <script>
        // Año actual para el footer
        document.getElementById('year').textContent = new Date().getFullYear();
        
        // Efecto de escritura
        const titles = ["Desarrollador Multiplataforma", "Programador Full Stack", "Especialista en JavaScript", "Apasionado por el código"];
        let currentTitle = 0;
        let charIndex = 0;
        let isDeleting = false;
        let typingSpeed = 100;
        
        const typeEffect = () => {
            const titleElement = document.querySelector('.typing-effect');
            const fullText = titles[currentTitle];
            
            if (isDeleting) {
                titleElement.textContent = fullText.substring(0, charIndex - 1);
                charIndex--;
                typingSpeed = 50;
            } else {
                titleElement.textContent = fullText.substring(0, charIndex + 1);
                charIndex++;
                typingSpeed = 100;
            }
            
            if (!isDeleting && charIndex === fullText.length) {
                isDeleting = true;
                typingSpeed = 1500; // Pausa al final
            } else if (isDeleting && charIndex === 0) {
                isDeleting = false;
                currentTitle = (currentTitle + 1) % titles.length;
                typingSpeed = 500; // Pausa al inicio
            }
            
            setTimeout(typeEffect, typingSpeed);
        };
        
        // Iniciar el efecto después de que cargue la página
        window.addEventListener('load', () => {
            setTimeout(typeEffect, 1000);
            
            // Efecto de aparición suave
            const elements = document.querySelectorAll('header, .tech-section');
            elements.forEach((el, index) => {
                setTimeout(() => {
                    el.style.opacity = '1';
                    el.style.transform = 'translateY(0)';
                }, index * 200);
            });
        });
        
        // Estilos iniciales para la animación
        document.querySelectorAll('header, .tech-section').forEach(el => {
            el.style.opacity = '0';
            el.style.transform = 'translateY(20px)';
            el.style.transition = 'opacity 0.5s ease, transform 0.5s ease';
        });
    </script>
</body>
</html>
