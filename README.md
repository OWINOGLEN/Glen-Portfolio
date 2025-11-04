<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Owino Glen | Frontend | Backend Developer</title>
    <link rel="icon" href="Portfolio Images/favicon.jpg" type="image/jpg" style="border-radius:50%;">
    <meta name="theme-color" content="#2563eb">
    <link href='https://unpkg.com/boxicons@2.1.4/css/boxicons.min.css' rel='stylesheet'>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/animate.css/4.1.1/animate.min.css">
    <style>
        :root {
            --primary: #2563eb;
            --secondary: #1e40af;
            --dark: #1e293b;
            --light: #f8fafc;
            --gray: #94a3b8;
            --success: #10b981;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background-color: var(--light);
            color: var(--dark);
            overflow-x: hidden;
        }

        /* Header Styles */
        .header {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            padding: 1.5rem 10%;
            background-color: rgba(248, 250, 252, 0.9);
            backdrop-filter: blur(10px);
            display: flex;
            justify-content: space-between;
            align-items: center;
            z-index: 100;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
            transition: all 0.3s ease;
        }

        .header.scrolled {
            padding: 1rem 10%;
            background-color: rgba(255, 255, 255, 0.98);
        }

        .logo {
            width: 50px;
            height: 50px;
            border-radius: 50%;
            object-fit: cover;
            border: 2px solid var(--primary);
            transition: all 0.3s ease;
        }

        .header.scrolled .logo {
            width: 40px;
            height: 40px;
        }

        .navbar ul {
            display: flex;
            list-style: none;
            gap: 2rem;
        }

        .navbar a {
            text-decoration: none;
            color: var(--dark);
            font-weight: 600;
            font-size: 1rem;
            position: relative;
            transition: color 0.3s ease;
        }

        .navbar a::after {
            content: '';
            position: absolute;
            width: 0;
            height: 2px;
            background-color: var(--primary);
            bottom: -4px;
            left: 0;
            transition: width 0.3s ease;
        }

        .navbar a:hover,
        .navbar a.active {
            color: var(--primary);
        }

        .navbar a:hover::after,
        .navbar a.active::after {
            width: 100%;
        }

        /* Hamburger Menu */
        .hamburger {
            display: none;
            cursor: pointer;
            z-index: 101;
        }

        .hamburger span {
            display: block;
            width: 25px;
            height: 3px;
            background-color: var(--dark);
            margin: 5px 0;
            transition: all 0.3s ease;
        }

        .hamburger.active span:nth-child(1) {
            transform: translateY(8px) rotate(45deg);
        }

        .hamburger.active span:nth-child(2) {
            opacity: 0;
        }

        .hamburger.active span:nth-child(3) {
            transform: translateY(-8px) rotate(-45deg);
        }

        /* Home Section */
        .home {
            min-height: 100vh;
            padding: 10rem 10% 5rem;
            display: flex;
            align-items: center;
            justify-content: space-between;
            position: relative;
            overflow: hidden;
        }

        .home-content {
            max-width: 600px;
            z-index: 2;
        }

        .home-content h1 {
            font-size: 3.5rem;
            font-weight: 700;
            line-height: 1.2;
            margin-bottom: 1rem;
            color: var(--dark);
        }

        .home-content h3 {
            font-size: 1.5rem;
            font-weight: 600;
            color: var(--primary);
            margin-bottom: 1.5rem;
        }

        .home-content p {
            font-size: 1.1rem;
            line-height: 1.6;
            margin-bottom: 2rem;
            color: var(--gray);
        }

        .btn-box {
            display: flex;
            gap: 1rem;
            margin-bottom: 2rem;
        }

        .btn-box a {
            display: inline-block;
            padding: 0.8rem 1.8rem;
            border-radius: 0.5rem;
            font-weight: 600;
            text-decoration: none;
            transition: all 0.3s ease;
        }

        #hire-me {
            background-color: var(--primary);
            color: white;
            border: 2px solid var(--primary);
        }

        #hire-me:hover {
            background-color: var(--secondary);
            border-color: var(--secondary);
            transform: translateY(-3px);
            box-shadow: 0 10px 20px rgba(37, 99, 235, 0.2);
        }

        .download-Owino  {
            background-color: transparent;
            color: var(--primary);
            border: 2px solid var(--primary);
        }

        .download-Owino :hover {
            background-color: rgba(37, 99, 235, 0.1);
            transform: translateY(3px);
            box-shadow: 0 10px 20px rgba(37, 99, 235, 0.1);
        }

        .home-sci {
            display: flex;
            gap: 1rem;
        }

        .home-sci a {
            display: flex;
            align-items: center;
            justify-content: center;
            width: 40px;
            height: 40px;
            background-color: white;
            border-radius: 50%;
            color: var(--dark);
            font-size: 1.2rem;
            text-decoration: none;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
            transition: all 0.3s ease;
        }

        .home-sci a:hover {
            background-color: var(--primary);
            color: white;
            transform: translateY(-5px);
        }

        .img-box {
            position: relative;
            width: 400px;
            height: 400px;
            border-radius: 50%;
            background: linear-gradient(45deg, var(--primary), #3b82f6);
            display: flex;
            align-items: center;
            justify-content: center;
            box-shadow: 0 20px 30px rgba(37, 99, 235, 0.3);
            animation: float 6s ease-in-out infinite;
        }

        @keyframes float {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-20px); }
        }

        .img-box img {
            width: 380px;
            height: 380px;
            border-radius: 50%;
            object-fit: cover;
            border: 10px solid white;
        }

        /* About Section */
        .about {
            padding: 6rem 10%;
            background-color: white;
        }

        .about-content {
            max-width: 1200px;
            margin: 0 auto;
        }

        .about-content h3 {
            font-size: 2rem;
            margin-bottom: 2rem;
            color: var(--dark);
            text-align: center;
            position: relative;
        }

        .about-content h3::after {
            content: '';
            position: absolute;
            width: 80px;
            height: 4px;
            background-color: var(--primary);
            bottom: -10px;
            left: 50%;
            transform: translateX(-50%);
            border-radius: 2px;
        }

        .about-content p {
            text-align: center;
            font-size: 1.2rem;
            color: var(--gray);
            margin-bottom: 3rem;
        }

        .skills-container {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(150px, 1fr));
            gap: 2rem;
            margin-bottom: 4rem;
        }

        .skill-card {
            background-color: white;
            border-radius: 0.5rem;
            padding: 1.5rem;
            text-align: center;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
            transition: all 0.3s ease;
            border: 1px solid rgba(0, 0, 0, 0.05);
        }

        .skill-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 15px 30px rgba(37, 99, 235, 0.1);
        }

        .skill-card img {
            width: 80px;
            height: 80px;
            object-fit: contain;
            margin-bottom: 1rem;
        }

        .skill-card h4 {
            font-size: 1.1rem;
            color: var(--dark);
        }

        .projects-container {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(350px, 1fr));
            gap: 2rem;
        }

        .project-card {
            background-color: white;
            border-radius: 0.5rem;
            overflow: hidden;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
            transition: all 0.3s ease;
            border: 1px solid rgba(0, 0, 0, 0.05);
        }

        .project-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 15px 30px rgba(37, 99, 235, 0.1);
        }

        .project-card img {
            width: 100%;
            height: 200px;
            object-fit: cover;
        }

        .project-info {
            padding: 1.5rem;
        }

        .project-info h4 {
            font-size: 1.2rem;
            margin-bottom: 0.5rem;
            color: var(--dark);
        }

        .project-info p {
            font-size: 0.9rem;
            color: var(--gray);
            margin-bottom: 1rem;
        }

        .project-links {
            display: flex;
            gap: 1rem;
        }

        .project-links a {
            display: inline-block;
            padding: 0.5rem 1rem;
            border-radius: 0.3rem;
            font-size: 0.9rem;
            font-weight: 600;
            text-decoration: none;
            transition: all 0.3s ease;
        }

        .project-links a:first-child {
            background-color: var(--primary);
            color: white;
        }

        .project-links a:first-child:hover {
            background-color: var(--secondary);
        }

        .project-links a:last-child {
            background-color: transparent;
            color: var(--primary);
            border: 1px solid var(--primary);
        }

        .project-links a:last-child:hover {
            background-color: rgba(37, 99, 235, 0.1);
        }

        /* Contact Section */
        .contact {
            padding: 6rem 10%;
            background-color: #f1f5f9;
        }

        .contact h3 {
            font-size: 2rem;
            margin-bottom: 2rem;
            color: var(--dark);
            text-align: center;
            position: relative;
        }

        .contact h3::after {
            content: '';
            position: absolute;
            width: 80px;
            height: 4px;
            background-color: var(--primary);
            bottom: -10px;
            left: 50%;
            transform: translateX(-50%);
            border-radius: 2px;
        }

        .contact-form {
            max-width: 600px;
            margin: 0 auto;
            background-color: white;
            padding: 2rem;
            border-radius: 0.5rem;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
        }

        .form-group {
            margin-bottom: 1.5rem;
        }

        .form-group label {
            display: block;
            margin-bottom: 0.5rem;
            font-weight: 600;
            color: var(--dark);
        }

        .form-group input,
        .form-group textarea {
            width: 100%;
            padding: 0.8rem 1rem;
            border: 1px solid #e2e8f0;
            border-radius: 0.3rem;
            font-size: 1rem;
            transition: all 0.3s ease;
        }

        .form-group input:focus,
        .form-group textarea:focus {
            outline: none;
            border-color: var(--primary);
            box-shadow: 0 0 0 3px rgba(37, 99, 235, 0.1);
        }

        .form-group textarea {
            min-height: 150px;
            resize: vertical;
        }

        .submit-btn {
            background-color: var(--primary);
            color: white;
            border: none;
            padding: 0.8rem 1.8rem;
            border-radius: 0.5rem;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
            width: 100%;
        }

        .submit-btn:hover {
            background-color: var(--secondary);
            transform: translateY(-3px);
            box-shadow: 0 10px 20px rgba(37, 99, 235, 0.2);
        }

        /* Footer */
        .footer {
            background-color: var(--dark);
            color: white;
            padding: 2rem 10%;
            text-align: center;
        }

        .footer p {
            margin-bottom: 1rem;
        }

        .footer-links {
            display: flex;
            justify-content: center;
            gap: 1.5rem;
            margin-bottom: 1.5rem;
        }

        .footer-links a {
            color: white;
            text-decoration: none;
            transition: color 0.3s ease;
        }

        .footer-links a:hover {
            color: var(--primary);
        }

        .footer-social {
            display: flex;
            justify-content: center;
            gap: 1rem;
        }

        .footer-social a {
            display: flex;
            align-items: center;
            justify-content: center;
            width: 40px;
            height: 40px;
            background-color: rgba(255, 255, 255, 0.1);
            border-radius: 50%;
            color: white;
            font-size: 1.2rem;
            text-decoration: none;
            transition: all 0.3s ease;
        }

        .footer-social a:hover {
            background-color: var(--primary);
            transform: translateY(-3px);
        }

        /* Responsive Styles */
        @media (max-width: 992px) {
            .home {
                flex-direction: column;
                text-align: center;
                padding-top: 8rem;
            }

            .home-content {
                margin-bottom: 3rem;
            }

            .btn-box {
                justify-content: center;
            }

            .home-sci {
                justify-content: center;
                margin-bottom: 2rem;
            }

            .img-box {
                width: 300px;
                height: 300px;
            }

            .img-box img {
                width: 280px;
                height: 280px;
            }
        }

        @media (max-width: 768px) {
            .header {
                padding: 1rem 5%;
            }

            .navbar {
                position: fixed;
                top: 0;
                right: -100%;
                width: 70%;
                height: 100vh;
                background-color: white;
                box-shadow: -5px 0 15px rgba(0, 0, 0, 0.1);
                display: flex;
                align-items: center;
                justify-content: center;
                transition: right 0.3s ease;
            }

            .navbar.active {
                right: 0;
            }

            .navbar ul {
                flex-direction: column;
                align-items: center;
                gap: 2rem;
            }

            .hamburger {
                display: block;
            }

            .home, .about, .contact {
                padding: 6rem 5% 3rem;
            }

            .home-content h1 {
                font-size: 2.5rem;
            }

            .home-content h3 {
                font-size: 1.3rem;
            }
        }

        @media (max-width: 480px) {
            .btn-box {
                flex-direction: column;
                gap: 1rem;
            }

            .skills-container {
                grid-template-columns: repeat(2, 1fr);
            }

            .projects-container {
                grid-template-columns: 1fr;
            }

            .img-box {
                width: 250px;
                height: 250px;
            }

            .img-box img {
                width: 230px;
                height: 230px;
            }
        }
    </style>
</head>
<body>
    <!-- Header -->
    <header class="header">
        <img src="Portfolio Images/glen.jpg" class="logo" alt="Glen Annex">
        <nav class="navbar">
            <ul>
                <li><a href="#home" class="active">Home</a></li>
                <li><a href="#about">About</a></li>
                <li><a href="#projects">Projects</a></li>
                <li><a href="#contact">Contact</a></li>
            </ul>
        </nav>
        <div class="hamburger">
            <span></span>
            <span></span>
            <span></span>
        </div>
    </header>

    <!-- Home Section -->
    <section class="home" id="home">
        <div class="home-content animate_animated animate_fadeInLeft">
            <h1>Hi, I'm Glen Annex</h1>
            <h3>Frontend Developer</h3>
            <p>I'm a multidisciplinary designer who focuses on telling my clients' stories visually, through enjoyable and meaningful experiences. I specialize in responsive websites and functional user interfaces.</p>
            <div class="btn-box">
                <a href="#contact" id="hire-me">Hire Me</a>
                <a href="#Owino CV_PDF.pdf" id="download-Owino CV_PDF.pdf" class="download-Owino CV_PDF.pdf">View | Download CV</a>
            </div>
            <div class="home-sci">
                <a href="https://github.com/OWINOGLEN" target="_blank"><i class='bx bxl-github'></i></a>
                <a href="#" target="_blank"><i class='bx bxl-twitter'></i></a>
                <a href="https://www.instagram.com/" target="_blank"><i class='bx bxl-instagram'></i></a>
                <a href="https://www.linkedin.com/in/owino-glen-048b012a1/" target="_blank"><i class='bx bxl-linkedin'></i></a>
                <a href="https://web.whatsapp.com/" target="_blank"><i class='bx bxl-whatsapp'></i></a>
            </div>
        </div>
        <div class="img-box animate_animated animate_fadeInRight">
            <img src="Portfolio Images/glen.jpg" alt="Glen Annex">
        </div>
    </section>

    <!-- About Section -->
    <section class="about" id="about">
        <div class="about-content">
            <h3 class="animate_animated animate_fadeIn">My Skills</h3>
            <p class="animate_animated animate_fadeIn">Here are the technologies I work with</p>
            <div class="skills-container">
                <div class="skill-card animate_animated animate_fadeInUp">
                    <img src="Portfolio Images/images-removebg-preview.png" alt="Machine Learning">
                    <h4>HTML</h4>
                </div>
                <div class="skill-card animate_animated animate_fadeInUp" style="animation-delay: 0.1s;">
                    <img src="Portfolio Images/css-removebg-preview.png" alt="CSS">
                    <h4>CSS</h4>
                </div>
                <div class="skill-card animate_animated animate_fadeInUp" style="animation-delay: 0.2s;">
                    <img src="Portfolio Images/aa8dpzdbo-ezgif.com-webp-to-jpg-converter-removebg-preview.png" alt="JavaScript">
                    <h4>JavaScript</h4>
                </div>
                <div class="skill-card animate_animated animate_fadeInUp" style="animation-delay: 0.3s;">
                    <img src="Portfolio Images/generic_pyth-removebg-preview.png" alt="Python">
                    <h4>Python</h4>
                </div>
                <div class="skill-card animate_animated animate_fadeInUp" style="animation-delay: 0.4s;">
                    <img src="Portfolio Images/react1-removebg-preview.png" alt="React">
                    <h4>React</h4>
                </div>
                <div class="skill-card animate_animated animate_fadeInUp" style="animation-delay: 0.5s;">
                    <img src="Portfolio Images/gh-removebg-preview.png" alt="GitHub">
                    <h4>GitHub</h4>
                </div>
            </div>
        </div>
    </section>

    <!-- Projects Section -->
    <section class="about" id="projects">
        <div class="about-content">
            <h3 class="animate_animated animate_fadeIn">My Projects</h3>
            <p class="animate_animated animate_fadeIn">Here are some of my recent works</p>
            <div class="projects-container">
                <div class="project-card animate_animated animate_fadeInUp">
                    <img src="imgs port/1.jpg" alt="Project 1">
                    <div class="project-info">
                        <h4>E-commerce Website</h4>
                        <p>A fully responsive e-commerce platform with product filtering and cart functionality.</p>
                        <div class="project-links">
                            <a href="#" target="_blank">Live Demo</a>
                            <a href="FoodKing.html" target="_blank">View Code</a>
                        </div>
                    </div>
                </div>
                <div class="project-card animate_animated animate_fadeInUp" style="animation-delay: 0.2s;">
                    <img src="imgs port/3.jpg" alt="Project 2">
                    <div class="project-info">
                        <h4>Task Management App</h4>
                        <p>A productivity application for managing tasks with drag-and-drop functionality.</p>
                        <div class="project-links">
                            <a href="#" target="_blank">In Process</a>
                            <a href="#" target="_blank">In Process</a>
                        </div>
                    </div>
                </div>
                <div class="project-card animate_animated animate_fadeInUp" style="animation-delay: 0.4s;">
                    <img src="imgs port/4.jpg" alt="Project 3">
                    <div class="project-info">
                        <h4>Weather Dashboard</h4>
                        <p>A weather application that displays current and forecasted weather conditions.</p>
                        <div class="project-links">
                            <a href="#" target="_blank">Coming Soon</a>
                            <a href="#" target="_blank">Coming Soon</a>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Contact Section -->
    <section class="contact" id="contact">
        <h3 class="animate_animated animate_fadeIn">Get In Touch</h3>
        <form class="contact-form animate_animated animate_fadeInUp" action="https://mail.google.com/mail/u/0/#inbox" method="POST">
            <div class="form-group">
                <label for="name">Name</label>
                <input type="text" id="name" name="name" required>
            </div>
            <div class="form-group">
                <label for="email">Email</label>
                <input type="email" id="email" name="email" required>
            </div>
            <div class="form-group"> 
                <label for="message">
                    <img src="Portfolio Images/glen.jpg" alt="glen annex" style="width:30px; height:30px; border-radius:50%;"> Message</label>
                <textarea id="message" name="message" required></textarea>
            </div>
            <button type="submit" class="submit-btn">Send Message</button>
        </form>
    </section>

    <!-- Footer -->
    <footer class="footer">
        <p>&copy; 2025 Glen Annex. All rights reserved.</p>
        <div class="footer-links">
            <a href="#home">Home</a>
            <a href="#about">About</a>
            <a href="#projects">Projects</a>
            <a href="#contact">Contact</a>
        </div>
        <div class="footer-social">
            <a href="https://github.com/OWINOGLEN" target="_blank"><i class='bx bxl-github'></i></a>
            <a href="#" target="_blank"><i class='bx bxl-twitter'></i></a>
            <a href="https://www.instagram.com/" target="_blank"><i class='bx bxl-instagram'></i></a>
            <a href="https://www.linkedin.com/in/owino-glen-048b012a1/" target="_blank"><i class='bx bxl-linkedin'></i></a>
        </div>
    </footer>

    <script>
        // Mobile Navigation Toggle
        const hamburger = document.querySelector('.hamburger');
        const navbar = document.querySelector('.navbar');

        hamburger.addEventListener('click', () => {
            hamburger.classList.toggle('active');
            navbar.classList.toggle('active');
        });

        // Close mobile menu when clicking a link
        document.querySelectorAll('.navbar a').forEach(link => {
            link.addEventListener('click', () => {
                hamburger.classList.remove('active');
                navbar.classList.remove('active');
            });
        });

        // Sticky Header
        window.addEventListener('scroll', () => {
            const header = document.querySelector('.header');
            header.classList.toggle('scrolled', window.scrollY > 0);
        });

        // Smooth Scrolling for Anchor Links
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function(e) {
                e.preventDefault();
                
                const targetId = this.getAttribute('href');
                const targetElement = document.querySelector(targetId);
                
                window.scrollTo({
                    top: targetElement.offsetTop - 80,
                    behavior: 'smooth'
                });
            });
        });

        // Active Link Highlighting
        const sections = document.querySelectorAll('section');
        const navLinks = document.querySelectorAll('.navbar a');

        window.addEventListener('scroll', () => {
            let current = '';
            
            sections.forEach(section => {
                const sectionTop = section.offsetTop;
                const sectionHeight = section.clientHeight;
                
                if (pageYOffset >= sectionTop - 100) {
                    current = section.getAttribute('id');
                }
            });
            
            navLinks.forEach(link => {
                link.classList.remove('active');
                if (link.getAttribute('href') === #${current}) {
                    link.classList.add('active');
                }
            });
        });

        // Form Submission
        const contactForm = document.querySelector('.contact-form');
        
        contactForm.addEventListener('submit', (e) => {
            e.preventDefault();
            
            // Get form values
            const name = document.getElementById('name').value;
            const email = document.getElementById('email').value;
            const message = document.getElementById('message').value;
            
            // Here you would typically send the form data to a server
            alert(Thank you, ${name}! Your message has been sent. I'll get back to you soon at ${email}.);
            
            // Reset the form
            contactForm.reset();
        });

        // Download CV Button
        document.getElementById('download-Owino CV_PDF.pdf').addEventListener('click', (e) => {
            e.preventDefault();
            alert('Click "OK" to View & Download CV.');
            window.location.href = 'Owino CV_PDF.pdf';
        });

        // Animation on Scroll
        const animateElements = document.querySelectorAll('.animate__animated');
        
        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    const animation = entry.target.getAttribute('data-animate');
                    entry.target.classList.add(animation);
                    observer.unobserve(entry.target);
                }
            });
        }, {
            threshold: 0.1
        });

        animateElements.forEach(element => {
            observer.observe(element);
        });
    </script>
</body>
</html>
