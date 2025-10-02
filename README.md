<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My Portfolio</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        /* Added smooth scrolling behavior */
        html {
            scroll-behavior: smooth;
        }
        
        body {
            font-family: -apple-system, BlinkMacSystemFont, 'SF Pro Display', 'Segoe UI', Roboto, sans-serif;
            margin: 0;
            padding: 0;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 25%, #f093fb 50%, #4facfe 75%, #00f2fe 100%);
            background-size: 400% 400%;
            background-attachment: fixed;
            /* Slowed down gradient animation from 15s to 30s */
            animation: gradientShift 30s ease infinite;
            color: #1d1d1f;
            overflow-x: hidden;
            min-height: 100vh;
        }
        
        @keyframes gradientShift {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }
        
        .container {
            max-width: 920px;
            margin: 0 auto;
            padding: 80px 24px;
        }
        
        .glass-card {
            background: rgba(255, 255, 255, 0.18);
            backdrop-filter: blur(40px) saturate(200%);
            -webkit-backdrop-filter: blur(40px) saturate(200%);
            border: 1.5px solid rgba(255, 255, 255, 0.4);
            border-radius: 32px;
            box-shadow: 0 8px 32px rgba(31, 38, 135, 0.15),
                        0 2px 8px rgba(0, 0, 0, 0.1),
                        inset 0 1px 1px rgba(255, 255, 255, 0.6),
                        inset 0 -1px 1px rgba(0, 0, 0, 0.05);
            padding: 48px;
            margin-bottom: 32px;
            opacity: 0;
            transform: translateY(40px);
            /* Simplified transition, removed cubic-bezier for smoother feel */
            transition: all 0.5s ease;
            position: relative;
            overflow: hidden;
        }
        
        .glass-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.2), transparent);
            transition: left 0.7s;
        }
        
        .glass-card:hover::before {
            left: 100%;
        }
        
        .glass-card.visible {
            opacity: 1;
            transform: translateY(0);
        }
        
        .glass-card:hover {
            background: rgba(255, 255, 255, 0.25);
            border: 1.5px solid rgba(255, 255, 255, 0.5);
            box-shadow: 0 16px 64px rgba(31, 38, 135, 0.2),
                        0 4px 16px rgba(0, 0, 0, 0.12),
                        inset 0 1px 1px rgba(255, 255, 255, 0.7),
                        inset 0 -1px 1px rgba(0, 0, 0, 0.05);
            transform: translateY(-4px);
        }
        
        .profile {
            text-align: center;
            margin-bottom: 0;
        }
        
        .profile-image-wrapper {
            position: relative;
            display: inline-block;
            margin-bottom: 32px;
        }
        
        .profile img {
            border-radius: 50%;
            width: 180px;
            height: 180px;
            object-fit: cover;
            border: 5px solid rgba(255, 255, 255, 0.7);
            box-shadow: 0 12px 48px rgba(0, 0, 0, 0.25),
                        0 0 0 1px rgba(255, 255, 255, 0.2),
                        inset 0 2px 4px rgba(255, 255, 255, 0.3);
            /* Removed floating animation */
            position: relative;
        }
        
        .profile h1 {
            font-size: 48px;
            font-weight: 800;
            color: #ffffff;
            margin-bottom: 16px;
            letter-spacing: -1px;
            text-shadow: 0 2px 16px rgba(0, 0, 0, 0.2),
                         0 4px 32px rgba(0, 0, 0, 0.15);
            background: linear-gradient(135deg, #ffffff 0%, rgba(255, 255, 255, 0.9) 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }
        
        .profile p {
            font-size: 20px;
            color: rgba(255, 255, 255, 0.95);
            margin-bottom: 32px;
            font-weight: 500;
            letter-spacing: 0.3px;
        }
        
        .social-cards {
            display: flex;
            justify-content: center;
            gap: 12px;
            margin-top: 32px;
            flex-wrap: wrap;
        }
        
        .social-card {
            background: rgba(255, 255, 255, 0.25);
            backdrop-filter: blur(20px);
            -webkit-backdrop-filter: blur(20px);
            border: 1.5px solid rgba(255, 255, 255, 0.4);
            border-radius: 20px;
            padding: 14px 28px;
            font-size: 15px;
            font-weight: 600;
            color: #ffffff;
            /* Simplified transition */
            transition: all 0.3s ease;
            cursor: pointer;
            text-decoration: none;
            display: inline-flex;
            align-items: center;
            gap: 8px;
            box-shadow: 0 4px 16px rgba(0, 0, 0, 0.1),
                        inset 0 1px 0 rgba(255, 255, 255, 0.5);
            position: relative;
            overflow: hidden;
        }
        
        .social-card:hover {
            transform: translateY(-4px);
            background: rgba(255, 255, 255, 0.35);
            box-shadow: 0 12px 32px rgba(0, 0, 0, 0.2),
                        inset 0 1px 0 rgba(255, 255, 255, 0.6);
            border: 1.5px solid rgba(255, 255, 255, 0.6);
        }
        
        .social-card:active {
            transform: translateY(-2px);
        }
        
        h2 {
            font-size: 36px;
            font-weight: 800;
            color: #ffffff;
            margin-bottom: 16px;
            letter-spacing: -0.8px;
            text-shadow: 0 2px 12px rgba(0, 0, 0, 0.15);
            background: linear-gradient(135deg, #ffffff 0%, rgba(255, 255, 255, 0.9) 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }
        
        p {
            font-size: 17px;
            line-height: 1.7;
            color: rgba(255, 255, 255, 0.95);
            font-weight: 400;
            letter-spacing: 0.2px;
        }
        
        .services-grid {
            display: flex;
            flex-direction: column;
            gap: 16px;
            margin-top: 32px;
        }
        
        .service-item {
            background: rgba(255, 255, 255, 0.2);
            backdrop-filter: blur(20px);
            border: 1.5px solid rgba(255, 255, 255, 0.3);
            border-radius: 24px;
            padding: 32px;
            text-align: left;
            /* Simplified transition */
            transition: all 0.3s ease;
            display: flex;
            align-items: center;
            gap: 24px;
            box-shadow: 0 4px 16px rgba(0, 0, 0, 0.08),
                        inset 0 1px 0 rgba(255, 255, 255, 0.4);
            position: relative;
            overflow: hidden;
        }
        
        .service-item::before {
            content: '';
            position: absolute;
            left: 0;
            top: 0;
            height: 100%;
            width: 4px;
            background: linear-gradient(180deg, rgba(255, 255, 255, 0.8), rgba(255, 255, 255, 0.3));
            transform: scaleY(0);
            /* Simplified transition */
            transition: transform 0.3s ease;
        }
        
        .service-item:hover::before {
            transform: scaleY(1);
        }
        
        .service-item:hover {
            background: rgba(255, 255, 255, 0.3);
            transform: translateX(8px);
            box-shadow: 0 12px 32px rgba(0, 0, 0, 0.15),
                        inset 0 1px 0 rgba(255, 255, 255, 0.5);
            border: 1.5px solid rgba(255, 255, 255, 0.5);
        }
        
        .service-icon {
            font-size: 56px;
            flex-shrink: 0;
            width: 80px;
            height: 80px;
            display: flex;
            align-items: center;
            justify-content: center;
            background: linear-gradient(135deg, rgba(255, 255, 255, 0.3), rgba(255, 255, 255, 0.1));
            border-radius: 20px;
            border: 1.5px solid rgba(255, 255, 255, 0.4);
            box-shadow: 0 4px 16px rgba(0, 0, 0, 0.1),
                        inset 0 1px 0 rgba(255, 255, 255, 0.5);
            /* Simplified transition, removed rotation */
            transition: transform 0.3s ease;
        }
        
        .service-item:hover .service-icon {
            /* Removed rotation, kept scale only */
            transform: scale(1.08);
        }
        
        .service-content {
            flex: 1;
        }
        
        .service-item h3 {
            font-size: 22px;
            font-weight: 700;
            color: #ffffff;
            margin-bottom: 10px;
            letter-spacing: -0.3px;
        }
        
        .service-item p {
            font-size: 16px;
            color: rgba(255, 255, 255, 0.9);
            line-height: 1.6;
        }
        
        .intro img {
            max-width: 100%;
            border-radius: 24px;
            margin: 32px 0;
            box-shadow: 0 16px 64px rgba(0, 0, 0, 0.25),
                        0 4px 16px rgba(0, 0, 0, 0.15);
            /* Removed fadeIn animation */
            border: 2px solid rgba(255, 255, 255, 0.3);
            /* Simplified transition */
            transition: transform 0.3s ease;
        }
        
        .intro img:hover {
            transform: scale(1.02);
        }
        
        .video video {
            max-width: 100%;
            width: 100%;
            border-radius: 24px;
            box-shadow: 0 16px 64px rgba(0, 0, 0, 0.25),
                        0 4px 16px rgba(0, 0, 0, 0.15);
            /* Simplified transition */
            transition: transform 0.3s ease;
            border: 2px solid rgba(255, 255, 255, 0.3);
        }
        
        .video video:hover {
            transform: scale(1.02);
        }
        
        .testimonials-grid {
            display: grid;
            gap: 20px;
            margin-top: 32px;
        }
        
        .testimonial-card {
            background: rgba(255, 255, 255, 0.2);
            backdrop-filter: blur(20px);
            border: 1.5px solid rgba(255, 255, 255, 0.3);
            border-radius: 24px;
            padding: 32px;
            /* Simplified transition */
            transition: all 0.3s ease;
            box-shadow: 0 4px 16px rgba(0, 0, 0, 0.08),
                        inset 0 1px 0 rgba(255, 255, 255, 0.4);
            position: relative;
        }
        
        .testimonial-card::before {
            content: '"';
            position: absolute;
            top: 20px;
            left: 24px;
            font-size: 72px;
            font-weight: 800;
            color: rgba(255, 255, 255, 0.15);
            line-height: 1;
        }
        
        .testimonial-card:hover {
            background: rgba(255, 255, 255, 0.3);
            transform: translateY(-4px);
            box-shadow: 0 12px 32px rgba(0, 0, 0, 0.15),
                        inset 0 1px 0 rgba(255, 255, 255, 0.5);
            border: 1.5px solid rgba(255, 255, 255, 0.5);
        }
        
        .testimonial-text {
            font-size: 17px;
            font-style: italic;
            color: rgba(255, 255, 255, 0.95);
            margin-bottom: 16px;
            line-height: 1.7;
            position: relative;
            z-index: 1;
        }
        
        .testimonial-author {
            font-size: 15px;
            font-weight: 600;
            color: #ffffff;
            letter-spacing: 0.3px;
        }
        
        .contact form {
            display: flex;
            flex-direction: column;
            gap: 20px;
            max-width: 640px;
            margin: 32px auto 0;
        }
        
        .contact input, 
        .contact textarea {
            background: rgba(255, 255, 255, 0.25);
            backdrop-filter: blur(20px);
            border: 1.5px solid rgba(255, 255, 255, 0.4);
            border-radius: 18px;
            padding: 18px 24px;
            font-size: 16px;
            color: #ffffff;
            font-family: -apple-system, BlinkMacSystemFont, 'SF Pro Display', sans-serif;
            /* Simplified transition */
            transition: all 0.3s ease;
            box-shadow: 0 2px 8px rgba(0, 0, 0, 0.05),
                        inset 0 1px 0 rgba(255, 255, 255, 0.3);
        }
        
        .contact input::placeholder,
        .contact textarea::placeholder {
            color: rgba(255, 255, 255, 0.65);
        }
        
        .contact input:focus, 
        .contact textarea:focus {
            outline: none;
            background: rgba(255, 255, 255, 0.35);
            border: 1.5px solid rgba(255, 255, 255, 0.6);
            box-shadow: 0 8px 24px rgba(0, 122, 255, 0.12),
                        0 0 0 4px rgba(255, 255, 255, 0.15),
                        inset 0 1px 0 rgba(255, 255, 255, 0.4);
            transform: translateY(-2px);
        }
        
        .contact textarea {
            min-height: 160px;
            resize: vertical;
        }
        
        .contact button {
            background: linear-gradient(135deg, #007aff 0%, #0051d5 100%);
            color: white;
            border: none;
            border-radius: 18px;
            padding: 18px 36px;
            font-size: 17px;
            font-weight: 700;
            cursor: pointer;
            /* Simplified transition */
            transition: all 0.3s ease;
            box-shadow: 0 8px 24px rgba(0, 122, 255, 0.35),
                        0 2px 8px rgba(0, 0, 0, 0.1),
                        inset 0 1px 0 rgba(255, 255, 255, 0.3);
            letter-spacing: 0.3px;
            position: relative;
            overflow: hidden;
        }
        
        .contact button:hover {
            transform: translateY(-4px);
            box-shadow: 0 16px 40px rgba(0, 122, 255, 0.45),
                        0 4px 12px rgba(0, 0, 0, 0.15),
                        inset 0 1px 0 rgba(255, 255, 255, 0.4);
            background: linear-gradient(135deg, #0077ed 0%, #0047c2 100%);
        }
        
        .contact button:active {
            transform: translateY(-1px);
        }
        
        @media (max-width: 768px) {
            .container {
                padding: 48px 20px;
            }
            
            .glass-card {
                padding: 32px 24px;
                border-radius: 28px;
            }
            
            .profile h1 {
                font-size: 40px;
            }
            
            h2 {
                font-size: 32px;
            }
            
            .profile img {
                width: 140px;
                height: 140px;
            }
            
            .service-icon {
                width: 64px;
                height: 64px;
                font-size: 40px;
            }
            
            .service-item {
                padding: 24px;
                gap: 16px;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <!-- Profile Section -->
        <div class="profile glass-card">
            <div class="profile-image-wrapper">
                <img src="/placeholder.svg?height=180&width=180" alt="Profile Photo">
            </div>
            <h1>Alex Morgan</h1>
            <p>Creative Developer & Designer</p>
            <div class="social-cards">
                <a href="#" class="social-card">📷 Instagram</a>
                <a href="#" class="social-card">✈️ Telegram</a>
                <a href="#" class="social-card">💼 LinkedIn</a>
            </div>
        </div>

        <!-- Services Section -->
        <div class="services glass-card">
            <h2>What I Do</h2>
            <p>Crafting digital experiences that blend creativity with functionality</p>
            <div class="services-grid">
                <div class="service-item">
                    <div class="service-icon">💻</div>
                    <div class="service-content">
                        <h3>Web Development</h3>
                        <p>Building responsive, modern websites with cutting-edge technologies and best practices</p>
                    </div>
                </div>
                <div class="service-item">
                    <div class="service-icon">🎨</div>
                    <div class="service-content">
                        <h3>UI/UX Design</h3>
                        <p>Creating intuitive and beautiful user interfaces that delight and engage users</p>
                    </div>
                </div>
                <div class="service-item">
                    <div class="service-icon">⚡</div>
                    <div class="service-content">
                        <h3>Performance Optimization</h3>
                        <p>Enhancing speed, efficiency, and overall user experience across all platforms</p>
                    </div>
                </div>
            </div>
        </div>

        <!-- Introduction Section -->
        <div class="intro glass-card">
            <h2>About Me</h2>
            <img src="/placeholder.svg?height=400&width=800" alt="Workspace">
            <p>Welcome to my portfolio! I'm a passionate developer and designer with over 5 years of experience creating elegant digital solutions. I specialize in transforming ideas into beautiful, functional experiences that users love. My approach combines technical expertise with creative vision to deliver projects that exceed expectations.</p>
        </div>

        <!-- Video Section -->
        <div class="video glass-card">
            <h2>Featured Work</h2>
            <video controls poster="/placeholder.svg?height=450&width=800">
                <source src="your-video.mp4" type="video/mp4">
                Your browser does not support the video tag.
            </video>
        </div>

        <!-- Testimonials Section -->
        <div class="testimonials glass-card">
            <h2>Client Testimonials</h2>
            <div class="testimonials-grid">
                <div class="testimonial-card">
                    <p class="testimonial-text">"Working with Alex was an absolute pleasure. The attention to detail and creative solutions exceeded our expectations. Highly recommended!"</p>
                    <p class="testimonial-author">— Sarah Johnson, CEO at TechStart</p>
                </div>
                <div class="testimonial-card">
                    <p class="testimonial-text">"Exceptional work! The project was delivered on time and the quality was outstanding. Will definitely work together again."</p>
                    <p class="testimonial-author">— Michael Chen, Product Manager at InnovateCo</p>
                </div>
                <div class="testimonial-card">
                    <p class="testimonial-text">"A true professional who brings both technical skills and creative vision. The results speak for themselves!"</p>
                    <p class="testimonial-author">— Emma Williams, Founder of DesignHub</p>
                </div>
            </div>
        </div>

        <!-- Contact Section -->
        <div class="contact glass-card">
            <h2>Get In Touch</h2>
            <p>Have a project in mind? Let's create something amazing together!</p>
            <form id="contactForm">
                <input type="text" id="name" placeholder="Your Name" required>
                <input type="email" id="email" placeholder="Your Email" required>
                <textarea id="message" placeholder="Tell me about your project..." required></textarea>
                <button type="submit">Send Message</button>
            </form>
        </div>
    </div>

    <script>
        // Smooth scroll reveal animations
        const cards = document.querySelectorAll('.glass-card');
        const observer = new IntersectionObserver(entries => {
            entries.forEach((entry, index) => {
                if (entry.isIntersecting) {
                    setTimeout(() => {
                        entry.target.classList.add('visible');
                    }, index * 50);
                }
            });
        }, { 
            threshold: 0.1,
            rootMargin: '0px 0px -50px 0px'
        });

        cards.forEach(card => observer.observe(card));

        // Contact form handling with iOS-style feedback
        const form = document.getElementById('contactForm');
        form.addEventListener('submit', function(e) {
            e.preventDefault();
            const name = document.getElementById('name').value;
            const email = document.getElementById('email').value;
            const message = document.getElementById('message').value;
            
            if (name && email && message) {
                // Create iOS-style success feedback
                const button = form.querySelector('button');
                const originalText = button.textContent;
                button.textContent = '✓ Message Sent!';
                button.style.background = 'linear-gradient(135deg, #34c759 0%, #30d158 100%)';
                
                setTimeout(() => {
                    button.textContent = originalText;
                    button.style.background = '';
                    form.reset();
                }, 2000);
            }
        });

    </script>
</body>
</html>
