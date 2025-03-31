<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Monkey Official</title>
    <style>
        :root {
            --accent-color: #AB002A;
            --background-color: #000000;
            --text-color: #ffffff;
            --card-bg: #111111;
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background-color: var(--background-color);
            color: var(--text-color);
            overflow-x: hidden;
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }
        
        header {
            position: relative;
            height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            text-align: center;
            padding: 0 20px;
            overflow: hidden;
        }
        
        .bg-overlay {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: radial-gradient(circle, rgba(171, 0, 42, 0.3) 0%, rgba(0, 0, 0, 0.8) 100%);
            z-index: -1;
        }
        
        .particles {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            overflow: hidden;
            z-index: -2;
        }
        
        .particle {
            position: absolute;
            background-color: var(--accent-color);
            border-radius: 50%;
            opacity: 0.5;
            animation: float 15s infinite linear;
        }
        
        @keyframes float {
            0% {
                transform: translateY(0) translateX(0) rotate(0deg);
                opacity: 0;
            }
            10% {
                opacity: 0.8;
            }
            90% {
                opacity: 0.8;
            }
            100% {
                transform: translateY(-1000px) translateX(100px) rotate(360deg);
                opacity: 0;
            }
        }
        
        .hero-content {
            max-width: 800px;
            animation: fadeInUp 1s ease-out;
        }
        
        h1 {
            font-size: 6rem;
            font-weight: 900;
            margin-bottom: 20px;
            letter-spacing: -2px;
            text-transform: uppercase;
            background: linear-gradient(90deg, #ffffff, var(--accent-color));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            transform: perspective(500px) rotateX(0deg);
            animation: pulse 5s infinite alternate;
        }
        
        @keyframes pulse {
            0% {
                text-shadow: 0 0 10px rgba(171, 0, 42, 0.3);
            }
            100% {
                text-shadow: 0 0 30px rgba(171, 0, 42, 0.7);
            }
        }
        
        .hero-subtitle {
            font-size: 1.8rem;
            font-weight: 300;
            margin-bottom: 40px;
            opacity: 0.9;
        }
        
        section {
            padding: 80px 0;
            position: relative;
        }
        
        .section-title {
            font-size: 3rem;
            margin-bottom: 60px;
            text-align: center;
            color: white;
            position: relative;
            display: inline-block;
            left: 50%;
            transform: translateX(-50%);
        }
        
        .section-title::after {
            content: '';
            position: absolute;
            left: 30%;
            bottom: -15px;
            width: 40%;
            height: 4px;
            background: var(--accent-color);
            border-radius: 2px;
        }
        
        .about-content {
            display: flex;
            flex-direction: column;
            align-items: center;
            max-width: 800px;
            margin: 0 auto;
            animation: fadeIn 1s ease-out;
        }
        
        .about-text {
            font-size: 1.2rem;
            line-height: 1.8;
            text-align: center;
            margin-bottom: 40px;
        }
        
        .featured-images {
            display: flex;
            justify-content: center;
            flex-wrap: wrap;
            gap: 30px;
            margin-top: 40px;
        }
        
        .featured-image {
            position: relative;
            border-radius: 12px;
            overflow: hidden;
            width: 100%;
            max-width: 500px;
            aspect-ratio: 16/9;
            background-color: var(--card-bg);
            transition: transform 0.5s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.5);
            opacity: 0;
            animation: fadeInUp 0.5s ease-out forwards;
        }
        
        .featured-image:hover {
            transform: translateY(-10px) scale(1.03);
            z-index: 2;
            box-shadow: 0 20px 40px rgba(171, 0, 42, 0.4);
        }
        
        .featured-image img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: transform 0.5s ease;
        }
        
        .featured-image:hover img {
            transform: scale(1.1);
        }
        
        .featured-overlay {
            position: absolute;
            bottom: 0;
            left: 0;
            right: 0;
            padding: 20px;
            background: linear-gradient(to top, rgba(0, 0, 0, 0.8) 0%, transparent 100%);
            color: white;
            opacity: 0;
            transition: opacity 0.3s ease;
        }
        
        .featured-image:hover .featured-overlay {
            opacity: 1;
        }
        
        .social-links {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            gap: 20px;
            margin-top: 60px;
        }
        
        .social-item {
            display: flex;
            flex-direction: column;
            align-items: center;
            text-decoration: none;
            color: white;
            padding: 20px;
            background-color: var(--card-bg);
            border-radius: 10px;
            width: 180px;
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
            opacity: 0;
            animation: fadeInUp 0.5s ease-out forwards;
        }
        
        .social-item:hover {
            transform: translateY(-10px);
            box-shadow: 0 15px 30px rgba(171, 0, 42, 0.4);
        }
        
        .social-item::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            height: 3px;
            background: linear-gradient(90deg, transparent, var(--accent-color), transparent);
            transform: translateX(-100%);
            transition: transform 0.5s ease;
        }
        
        .social-item:hover::before {
            transform: translateX(100%);
        }
        
        .social-icon {
            font-size: 2.5rem;
            margin-bottom: 15px;
            transition: transform 0.3s ease;
        }
        
        .social-item:hover .social-icon {
            transform: scale(1.2);
            color: var(--accent-color);
        }
        
        .social-name {
            font-weight: 600;
            margin-top: 5px;
        }
        
        footer {
            padding: 40px 0;
            text-align: center;
            border-top: 1px solid rgba(255, 255, 255, 0.1);
            margin-top: 40px;
        }
        
        .footer-text {
            font-size: 0.9rem;
            opacity: 0.7;
        }
        
        @keyframes fadeIn {
            from {
                opacity: 0;
            }
            to {
                opacity: 1;
            }
        }
        
        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(50px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }
        
        @media (max-width: 768px) {
            h1 {
                font-size: 3.5rem;
            }
            
            .hero-subtitle {
                font-size: 1.3rem;
            }
            
            .section-title {
                font-size: 2.5rem;
            }
            
            .social-links {
                gap: 10px;
            }
            
            .social-item {
                width: 130px;
                padding: 15px;
            }
        }
    </style>
</head>
<body>
    <header>
        <div class="bg-overlay"></div>
        <div class="particles" id="particles"></div>
        <div class="hero-content">
            <h1>Monkey</h1>
            <p class="hero-subtitle">Content Creator & Entertainer</p>
        </div>
    </header>
    
    <section id="about">
        <div class="container">
            <h2 class="section-title">About Monkey</h2>
            <div class="about-content">
                <p class="about-text">
                    Monkey is a dynamic content creator known for pushing boundaries and delivering 
                    high-energy entertainment. With an authentic and charismatic personality,
                    Monkey has built a dedicated community across multiple platforms.
                    From captivating livestreams to stunning visual content, Monkey continues
                    to innovate and connect with fans worldwide through creative expression
                    and unique perspectives.
                </p>
            </div>
        </div>
    </section>
    
    <section id="featured">
        <div class="container">
            <h2 class="section-title">Featured Content</h2>
            <div class="featured-images">
                <div class="featured-image" style="animation-delay: 0.1s;">
                    <img src="/api/placeholder/800/450" alt="Monkey Content">
                    <div class="featured-overlay">
                        <p>Latest content from Monkey's adventures</p>
                    </div>
                </div>
                <div class="featured-image" style="animation-delay: 0.3s;">
                    <img src="/api/placeholder/800/450" alt="Monkey Content">
                    <div class="featured-overlay">
                        <p>Creating moments that last</p>
                    </div>
                </div>
            </div>
        </div>
    </section>
    
    <section id="social">
        <div class="container">
            <h2 class="section-title">Connect With Monkey</h2>
            <div class="social-links">
                <a href="https://kick.com/imonkey_d" target="_blank" class="social-item" style="animation-delay: 0.1s;">
                    <span class="social-icon">🎥</span>
                    <span class="social-name">Kick</span>
                    <span>IMonkey Kick</span>
                </a>
                <a href="https://www.instagram.com/imonkey_d/" target="_blank" class="social-item" style="animation-delay: 0.2s;">
                    <span class="social-icon">📸</span>
                    <span class="social-name">Instagram</span>
                    <span>IMonkey Instagram</span>
                </a>
                <a href="https://www.snapchat.com/add/imonkey_d" target="_blank" class="social-item" style="animation-delay: 0.3s;">
                    <span class="social-icon">👻</span>
                    <span class="social-name">Snapchat</span>
                    <span>IMonkey Snap</span>
                </a>
                <a href="https://discord.gg/vDaKNT8Mg7" target="_blank" class="social-item" style="animation-delay: 0.4s;">
                    <span class="social-icon">🎮</span>
                    <span class="social-name">Discord</span>
                    <span>IMonkey Discord</span>
                </a>
                <a href="https://twitter.com/iiMonkey_D" target="_blank" class="social-item" style="animation-delay: 0.5s;">
                    <span class="social-icon">🐦</span>
                    <span class="social-name">X</span>
                    <span>IMonkey X</span>
                </a>
            </div>
        </div>
    </section>
    
    <footer>
        <div class="container">
            <p class="footer-text">© 2025 Monkey. All rights reserved.</p>
        </div>
    </footer>
    
    <script>
        // Create particles
        const particlesContainer = document.getElementById('particles');
        const particleCount = 20;
        
        for (let i = 0; i < particleCount; i++) {
            const particle = document.createElement('div');
            particle.classList.add('particle');
            
            // Random size between 5 and 25px
            const size = Math.random() * 20 + 5;
            particle.style.width = `${size}px`;
            particle.style.height = `${size}px`;
            
            // Random starting position
            const posX = Math.random() * 100;
            const posY = Math.random() * 100;
            particle.style.left = `${posX}%`;
            particle.style.top = `${posY}%`;
            
            // Random animation duration between 10 and 25 seconds
            const duration = Math.random() * 15 + 10;
            particle.style.animationDuration = `${duration}s`;
            
            // Random delay
            const delay = Math.random() * 5;
            particle.style.animationDelay = `${delay}s`;
            
            particlesContainer.appendChild(particle);
        }
        
        // Animation for elements on scroll
        const animateOnScroll = () => {
            const elements = document.querySelectorAll('.featured-image, .social-item');
            
            elements.forEach(item => {
                const position = item.getBoundingClientRect();
                
                // If element is in viewport
                if (position.top < window.innerHeight - 100) {
                    item.style.animationPlayState = 'running';
                }
            });
        };
        
        window.addEventListener('scroll', animateOnScroll);
        window.addEventListener('load', animateOnScroll);
    </script>
</body>
</html>