<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Oluwadamilola Abraham David - Frontend Engineer</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        :root {
            --primary-orange: #ff6b35;
            --dark-orange: #e55a2b;
            --primary-black: #1a1a1a;
            --light-black: #2d2d2d;
            --text-white: #ffffff;
            --text-gray: #cccccc;
            --accent-orange: #ff8c42;
        }

        body {
            font-family: 'Arial', sans-serif;
            background: linear-gradient(135deg, var(--primary-black) 0%, var(--light-black) 100%);
            color: var(--text-white);
            line-height: 1.6;
            overflow-x: hidden;
        }

        /* Navigation */
        .navbar {
            position: fixed;
            top: 0;
            width: 100%;
            background: rgba(26, 26, 26, 0.95);
            backdrop-filter: blur(10px);
            padding: 1rem 0;
            z-index: 1000;
            transition: all 0.3s ease;
        }

        .navbar.scrolled {
            background: rgba(26, 26, 26, 0.98);
            box-shadow: 0 2px 20px rgba(255, 107, 53, 0.3);
        }

        .nav-container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 2rem;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .logo {
            font-size: 1.5rem;
            font-weight: bold;
            color: var(--primary-orange);
            text-decoration: none;
            transition: all 0.3s ease;
        }

        .logo:hover {
            transform: scale(1.05);
            text-shadow: 0 0 10px var(--primary-orange);
        }

        .nav-menu {
            display: flex;
            list-style: none;
            gap: 2rem;
        }

        .nav-menu a {
            color: var(--text-white);
            text-decoration: none;
            font-weight: 500;
            transition: all 0.3s ease;
            position: relative;
        }

        .nav-menu a::before {
            content: '';
            position: absolute;
            bottom: -5px;
            left: 0;
            width: 0;
            height: 2px;
            background: var(--primary-orange);
            transition: width 0.3s ease;
        }

        .nav-menu a:hover::before {
            width: 100%;
        }

        .nav-menu a:hover {
            color: var(--primary-orange);
        }

        .hamburger {
            display: none;
            flex-direction: column;
            cursor: pointer;
            gap: 4px;
        }

        .hamburger span {
            width: 25px;
            height: 3px;
            background: var(--primary-orange);
            transition: all 0.3s ease;
        }

        /* Hero Section */
        .hero {
            min-height: 100vh;
            display: flex;
            align-items: center;
            padding: 0 2rem;
            position: relative;
            overflow: hidden;
        }

        .hero::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: 
                radial-gradient(circle at 20% 50%, rgba(255, 107, 53, 0.1) 0%, transparent 50%),
                radial-gradient(circle at 80% 20%, rgba(255, 107, 53, 0.1) 0%, transparent 50%);
            z-index: -1;
        }

        .hero-container {
            max-width: 1200px;
            margin: 0 auto;
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 4rem;
            align-items: center;
        }

        .hero-content h1 {
            font-size: 3.5rem;
            font-weight: bold;
            margin-bottom: 1rem;
            background: linear-gradient(135deg, var(--text-white) 0%, var(--primary-orange) 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            animation: fadeInUp 1s ease;
        }

        .hero-content .subtitle {
            font-size: 1.3rem;
            color: var(--primary-orange);
            margin-bottom: 1.5rem;
            animation: fadeInUp 1s ease 0.2s both;
        }

        .hero-content p {
            font-size: 1.1rem;
            color: var(--text-gray);
            margin-bottom: 2.5rem;
            line-height: 1.7;
            animation: fadeInUp 1s ease 0.4s both;
        }

        .hero-buttons {
            display: flex;
            gap: 1.5rem;
            animation: fadeInUp 1s ease 0.6s both;
        }

        .btn {
            padding: 12px 30px;
            border: none;
            border-radius: 50px;
            font-size: 1rem;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
            text-decoration: none;
            display: inline-block;
            text-align: center;
        }

        .btn-primary {
            background: linear-gradient(135deg, var(--primary-orange) 0%, var(--dark-orange) 100%);
            color: var(--text-white);
            box-shadow: 0 4px 15px rgba(255, 107, 53, 0.4);
        }

        .btn-primary:hover {
            transform: translateY(-2px);
            box-shadow: 0 8px 25px rgba(255, 107, 53, 0.6);
        }

        .btn-secondary {
            background: transparent;
            color: var(--primary-orange);
            border: 2px solid var(--primary-orange);
        }

        .btn-secondary:hover {
            background: var(--primary-orange);
            color: var(--text-white);
            transform: translateY(-2px);
        }

        .hero-image {
            display: flex;
            justify-content: center;
            align-items: center;
            animation: fadeIn 1s ease 0.8s both;
        }

        .profile-img {
            width: 350px;
            height: 350px;
            border-radius: 50%;
            object-fit: cover;
            border: 4px solid var(--primary-orange);
            box-shadow: 0 20px 40px rgba(255, 107, 53, 0.3);
            transition: all 0.3s ease;
        }

        .profile-img:hover {
            transform: scale(1.05);
            box-shadow: 0 25px 50px rgba(255, 107, 53, 0.5);
        }

        /* About Section */
        .about {
            padding: 6rem 2rem;
            background: var(--light-black);
        }

        .section-container {
            max-width: 1200px;
            margin: 0 auto;
        }

        .section-title {
            text-align: center;
            font-size: 2.5rem;
            margin-bottom: 3rem;
            color: var(--primary-orange);
            position: relative;
        }

        .section-title::after {
            content: '';
            position: absolute;
            bottom: -10px;
            left: 50%;
            transform: translateX(-50%);
            width: 80px;
            height: 3px;
            background: var(--primary-orange);
        }

        .about-content {
            display: grid;
            grid-template-columns: 1fr 2fr;
            gap: 4rem;
            align-items: center;
        }

        .about-text {
            font-size: 1.1rem;
            color: var(--text-gray);
            line-height: 1.8;
        }

        .skills-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
            gap: 1.5rem;
        }

        .skill-card {
            background: var(--primary-black);
            padding: 1.5rem;
            border-radius: 10px;
            text-align: center;
            border: 2px solid transparent;
            transition: all 0.3s ease;
        }

        .skill-card:hover {
            border-color: var(--primary-orange);
            transform: translateY(-5px);
            box-shadow: 0 10px 25px rgba(255, 107, 53, 0.2);
        }

        .skill-card h3 {
            color: var(--primary-orange);
            margin-bottom: 0.5rem;
        }

        /* Projects Section */
        .projects {
            padding: 6rem 2rem;
        }

        .projects-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 2rem;
            margin-top: 3rem;
        }

        .project-card {
            background: var(--light-black);
            border-radius: 15px;
            overflow: hidden;
            transition: all 0.3s ease;
            border: 2px solid transparent;
        }

        .project-card:hover {
            transform: translateY(-10px);
            border-color: var(--primary-orange);
            box-shadow: 0 20px 40px rgba(255, 107, 53, 0.2);
        }

        .project-image {
            width: 100%;
            height: 200px;
            background: linear-gradient(135deg, var(--primary-orange) 0%, var(--dark-orange) 100%);
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 3rem;
            color: var(--text-white);
        }

        .project-content {
            padding: 2rem;
        }

        .project-content h3 {
            color: var(--primary-orange);
            margin-bottom: 1rem;
            font-size: 1.3rem;
        }

        .project-content p {
            color: var(--text-gray);
            margin-bottom: 1.5rem;
            line-height: 1.6;
        }

        .project-tags {
            display: flex;
            flex-wrap: wrap;
            gap: 0.5rem;
            margin-bottom: 1.5rem;
        }

        .tag {
            background: var(--primary-black);
            color: var(--primary-orange);
            padding: 0.3rem 0.8rem;
            border-radius: 20px;
            font-size: 0.8rem;
            border: 1px solid var(--primary-orange);
        }

        /* Contact Section */
        .contact {
            padding: 6rem 2rem;
            background: var(--light-black);
        }

        .contact-content {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 4rem;
            margin-top: 3rem;
        }

        .contact-info h3 {
            color: var(--primary-orange);
            margin-bottom: 2rem;
        }

        .contact-item {
            display: flex;
            align-items: center;
            gap: 1rem;
            margin-bottom: 1.5rem;
            color: var(--text-gray);
        }

        .contact-item i {
            color: var(--primary-orange);
            font-size: 1.2rem;
            width: 20px;
        }

        .contact-form {
            display: flex;
            flex-direction: column;
            gap: 1.5rem;
        }

        .form-group {
            display: flex;
            flex-direction: column;
        }

        .form-group label {
            color: var(--primary-orange);
            margin-bottom: 0.5rem;
            font-weight: 600;
        }

        .form-group input,
        .form-group textarea {
            background: var(--primary-black);
            border: 2px solid transparent;
            border-radius: 8px;
            padding: 1rem;
            color: var(--text-white);
            font-size: 1rem;
            transition: all 0.3s ease;
        }

        .form-group input:focus,
        .form-group textarea:focus {
            outline: none;
            border-color: var(--primary-orange);
            box-shadow: 0 0 10px rgba(255, 107, 53, 0.3);
        }

        .form-group textarea {
            resize: vertical;
            min-height: 120px;
        }

        /* Footer */
        .footer {
            background: var(--primary-black);
            padding: 2rem;
            text-align: center;
            border-top: 2px solid var(--primary-orange);
        }

        .social-links {
            display: flex;
            justify-content: center;
            gap: 2rem;
            margin-bottom: 2rem;
        }

        .social-links a {
            color: var(--text-gray);
            font-size: 1.5rem;
            transition: all 0.3s ease;
        }

        .social-links a:hover {
            color: var(--primary-orange);
            transform: translateY(-3px);
        }

        /* Animations */
        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        @keyframes fadeIn {
            from {
                opacity: 0;
            }
            to {
                opacity: 1;
            }
        }

        /* Responsive Design */
        @media (max-width: 768px) {
            .hamburger {
                display: flex;
            }

            .nav-menu {
                position: fixed;
                top: 70px;
                left: -100%;
                width: 100%;
                height: calc(100vh - 70px);
                background: var(--primary-black);
                flex-direction: column;
                justify-content: center;
                align-items: center;
                transition: left 0.3s ease;
            }

            .nav-menu.active {
                left: 0;
            }

            .hero-container {
                grid-template-columns: 1fr;
                text-align: center;
                gap: 2rem;
            }

            .hero-content h1 {
                font-size: 2.5rem;
            }

            .profile-img {
                width: 250px;
                height: 250px;
            }

            .about-content {
                grid-template-columns: 1fr;
                gap: 2rem;
            }

            .contact-content {
                grid-template-columns: 1fr;
                gap: 2rem;
            }

            .hero-buttons {
                flex-direction: column;
                align-items: center;
            }

            .btn {
                width: 200px;
            }
        }

        @media (max-width: 480px) {
            .hero-content h1 {
                font-size: 2rem;
            }

            .section-title {
                font-size: 2rem;
            }

            .projects-grid {
                grid-template-columns: 1fr;
            }

            .profile-img {
                width: 200px;
                height: 200px;
            }
        }

        /* Smooth scrolling */
        html {
            scroll-behavior: smooth;
        }

        /* Loading animation for profile image */
        .profile-img {
            opacity: 0;
            animation: profileLoad 1s ease 1s forwards;
        }

        @keyframes profileLoad {
            to {
                opacity: 1;
            }
        }
    </style>
</head>
<body>
    <!-- Navigation -->
    <nav class="navbar" id="navbar">
        <div class="nav-container">
            <a href="#" class="logo">OAD</a>
            <ul class="nav-menu" id="nav-menu">
                <li><a href="#home">Home</a></li>
                <li><a href="#about">About</a></li>
                <li><a href="#projects">Projects</a></li>
                <li><a href="#contact">Contact</a></li>
            </ul>
            <div class="hamburger" id="hamburger">
                <span></span>
                <span></span>
                <span></span>
            </div>
        </div>
    </nav>

    <!-- Hero Section -->
    <section class="hero" id="home">
        <div class="hero-container">
            <div class="hero-content">
                <h1>Oluwadamilola Abraham David</h1>
                <div class="subtitle">Frontend Engineer</div>
                <p>Passionate about creating exceptional digital experiences through clean code and innovative design. I transform ideas into interactive, responsive, and user-friendly web applications.</p>
                <div class="hero-buttons">
                    <a href="#projects" class="btn btn-primary">View My Work</a>
                    <a href="#contact" class="btn btn-secondary">Get In Touch</a>
                </div>
            </div>
            <div class="hero-image">
                <img src="data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMzUwIiBoZWlnaHQ9IjM1MCIgdmlld0JveD0iMCAwIDM1MCAzNTAiIGZpbGw9Im5vbmUiIHhtbG5zPSJodHRwOi8vd3d3LnczLm9yZy8yMDAwL3N2ZyI+CjxjaXJjbGUgY3g9IjE3NSIgY3k9IjE3NSIgcj0iMTc1IiBmaWxsPSJ1cmwoI2dyYWRpZW50KSIvPgo8dGV4dCB4PSI1MCUiIHk9IjUwJSIgZG9taW5hbnQtYmFzZWxpbmU9Im1pZGRsZSIgdGV4dC1hbmNob3I9Im1pZGRsZSIgZmlsbD0id2hpdGUiIGZvbnQtc2l6ZT0iNjAiIGZvbnQtZmFtaWx5PSJBcmlhbCwgc2Fucy1zZXJpZiIgZm9udC13ZWlnaHQ9ImJvbGQiPk9BRDwvdGV4dD4KPGRlZnM+CjxsaW5lYXJHcmFkaWVudCBpZD0iZ3JhZGllbnQiIHgxPSIwJSIgeTE9IjAlIiB4Mj0iMTAwJSIgeTI9IjEwMCUiPgo8c3RvcCBvZmZzZXQ9IjAlIiBzdG9wLWNvbG9yPSIjZmY2YjM1Ii8+CjxzdG9wIG9mZnNldD0iMTAwJSIgc3RvcC1jb2xvcj0iI2U1NWEyYiIvPgo8L2xpbmVhckdyYWRpZW50Pgo8L2RlZnM+Cjwvc3ZnPgo=" alt="Oluwadamilola Abraham David" class="profile-img">
            </div>
        </div>
    </section>

    <!-- About Section -->
    <section class="about" id="about">
        <div class="section-container">
            <h2 class="section-title">About Me</h2>
            <div class="about-content">
                <div class="about-text">
                    <p>I'm a passionate Frontend Engineer with a keen eye for detail and a love for creating seamless user experiences. With expertise in modern web technologies, I bring designs to life through clean, efficient, and scalable code.</p>
                    <br>
                    <p>My journey in web development has equipped me with a strong foundation in both technical skills and creative problem-solving. I enjoy working on challenging projects that push the boundaries of what's possible on the web.</p>
                </div>
                <div class="skills-grid">
                    <div class="skill-card">
                        <h3>JavaScript</h3>
                        <p>ES6+, Modern JS</p>
                    </div>
                    <div class="skill-card">
                        <h3>React</h3>
                        <p>Hooks, Context, Redux</p>
                    </div>
                    <div class="skill-card">
                        <h3>CSS3</h3>
                        <p>Flexbox, Grid, Animations</p>
                    </div>
                    <div class="skill-card">
                        <h3>HTML5</h3>
                        <p>Semantic, Accessible</p>
                    </div>
                    <div class="skill-card">
                        <h3>TypeScript</h3>
                        <p>Type Safety, Interfaces</p>
                    </div>
                    <div class="skill-card">
                        <h3>Git</h3>
                        <p>Version Control</p>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Projects Section -->
    <section class="projects" id="projects">
        <div class="section-container">
            <h2 class="section-title">Featured Projects</h2>
            <div class="projects-grid">
                <div class="project-card">
                    <div class="project-image">🚀</div>
                    <div class="project-content">
                        <h3>E-Commerce Platform</h3>
                        <p>A fully responsive e-commerce solution with modern UI/UX, shopping cart functionality, and secure payment integration.</p>
                        <div class="project-tags">
                            <span class="tag">React</span>
                            <span class="tag">JavaScript</span>
                            <span class="tag">CSS3</span>
                            <span class="tag">API</span>
                        </div>
                        <a href="#" class="btn btn-primary">View Project</a>
                    </div>
                </div>
                <div class="project-card">
                    <div class="project-image">📱</div>
                    <div class="project-content">
                        <h3>Task Management App</h3>
                        <p>An intuitive task management application with drag-and-drop functionality, real-time updates, and team collaboration features.</p>
                        <div class="project-tags">
                            <span class="tag">React</span>
                            <span class="tag">TypeScript</span>
                            <span class="tag">Redux</span>
                            <span class="tag">CSS Grid</span>
                        </div>
                        <a href="#" class="btn btn-primary">View Project</a>
                    </div>
                </div>
                <div class="project-card">
                    <div class="project-image">🌐</div>
                    <div class="project-content">
                        <h3>Portfolio Website</h3>
                        <p>A modern, responsive portfolio website showcasing creative animations, smooth scrolling, and optimized performance.</p>
                        <div class="project-tags">
                            <span class="tag">HTML5</span>
                            <span class="tag">CSS3</span>
                            <span class="tag">JavaScript</span>
                            <span class="tag">Animations</span>
                        </div>
                        <a href="#" class="btn btn-primary">View Project</a>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Contact Section -->
    <section class="contact" id="contact">
        <div class="section-container">
            <h2 class="section-title">Get In Touch</h2>
            <div class="contact-content">
                <div class="contact-info">
                    <h3>Let's Connect</h3>
                    <p style="color: var(--text-gray); margin-bottom: 2rem;">I'm always open to discussing new opportunities, interesting projects, or just having a chat about technology and innovation.</p>
                    <div class="contact-item">
                        <i>📧</i>
                        <span>hello@oluwadamilola.dev</span>
                    </div>
                    <div class="contact-item">
                        <i>📱</i>
                        <span>+234 (0) 123 456 7890</span>
                    </div>
                    <div class="contact-item">
                        <i>📍</i>
                        <span>Lagos, Nigeria</span>
                    </div>
                    <div class="contact-item">
                        <i>💼</i>
                        <span>Available for Freelance & Full-time</span>
                    </div>
                </div>
                <form class="contact-form">
                    <div class="form-group">
                        <label for="name">Name</label>
                        <input type="text" id="name" name="name" required>
                    </div>
                    <div class="form-group">
                        <label for="email">Email</label>
                        <input type="email" id="email" name="email" required>
                    </div>
                    <div class="form-group">
                        <label for="subject">Subject</label>
                        <input type="text" id="subject" name="subject" required>
                    </div>
                    <div class="form-group">
                        <label for="message">Message</label>
                        <textarea id="message" name="message" required></textarea>
                    </div>
                    <button type="submit" class="btn btn-primary">Send Message</button>
                </form>
            </div>
        </div>
    </section>

    <!-- Footer -->
    <footer class="footer">
        <div class="social-links">
            <a href="#" title="GitHub">💻</a>
            <a href="#" title="LinkedIn">💼</a>
            <a href="#" title="Twitter">🐦</a>
            <a href="#" title="Instagram">📷</a>
        </div>
        <p>&copy; 2025 Oluwadamilola Abraham David. All rights reserved.</p>
    </footer>

    <script>
        // Navbar scroll effect
        window.addEventListener('scroll', function() {
            const navbar = document.getElementById('navbar');
            if (window.scrollY > 50) {
                navbar.classList.add('scrolled');
            } else {
                navbar.classList.remove('scrolled');
            }
        });

        // Mobile menu toggle
        const hamburger = document.getElementById('hamburger');
        const navMenu = document.getElementById('nav-menu');

        hamburger.addEventListener('click', function() {
            navMenu.classList.toggle('active');
            
            // Animate hamburger
            const spans = hamburger.querySelectorAll('span');
            if (navMenu.classList.contains('active')) {
                spans[0].style.transform = 'rotate(45deg) translate(5px, 5px)';
                spans[1].style.opacity = '0';
                spans[2].style.transform = 'rotate(-45deg) translate(7px, -6px)';
            } else {
                spans[0].style.transform = 'none';
                spans[1].style.opacity = '1';
                spans[2].style.transform = 'none';
            }
        });

        // Close mobile menu when clicking on a link
        document.querySelectorAll('.nav-menu a').forEach(link => {
            link.addEventListener('click', function() {
                navMenu.classList.remove('active');
                const spans = hamburger.querySelectorAll('span');
                spans[0].style.transform = 'none';
                spans[1].style.opacity = '1';
                spans[2].style.transform = 'none';
            });
        });

        // Smooth scrolling for navigation links
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                const target = document.querySelector(this.getAttribute('href'));
                if (target) {
                    target.scrollIntoView({
                        behavior: 'smooth',
                        block: 'start'
                    });
                }
            });
        });

        // Form submission
        document.querySelector('.contact-form').addEventListener('submit', function(e) {
            e.preventDefault();
            
            // Get form data
            const formData = new FormData(this);
            const name = formData.get('name');
            const email = formData.get('email');
            const subject = formData.get('subject');
            const message = formData.get('message');
            
            // Simple validation
            if (!name || !email || !subject || !message) {
                alert('Please fill in all fields.');
                return;
            }
            
            // Simulate form submission
            const submitBtn = this.querySelector('button[type="submit"]');
            const originalText = submitBtn.textContent;
            submitBtn.textContent = 'Sending...';
            submitBtn.disabled = true;
            
            setTimeout(() => {
                alert('Thank you for your message! I\'ll get back to you soon.');
                this.reset();
                submitBtn.textContent = originalText;
                submitBtn.disabled = false;
            }, 2000);
        });

        // Intersection Observer for animations
        const observerOptions = {
            threshold: 0.1,
            rootMargin: '0px 0px -50px 0px'
        };

        const observer = new IntersectionObserver(function(entries) {
            entries.forEach(entry => {
                if (
