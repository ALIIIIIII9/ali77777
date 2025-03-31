<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>IMonkey Social Hub</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Poppins', sans-serif;
        }
        
        body {
            background-color: #0a0a0a;
            color: #ffffff;
            overflow-x: hidden;
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }
        
        /* Hero Section */
        .hero {
            position: relative;
            height: 100vh;
            width: 100%;
            display: flex;
            justify-content: center;
            align-items: center;
            overflow: hidden;
        }
        
        .hero::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: url('/api/placeholder/573/322') no-repeat center center;
            background-size: cover;
            filter: brightness(0.7);
            z-index: -1;
        }
        
        .hero-content {
            text-align: center;
            z-index: 1;
            opacity: 0;
            transform: translateY(20px);
            animation: fadeInUp 1s ease forwards;
        }
        
        .hero-content h1 {
            font-size: 5rem;
            font-weight: 700;
            margin-bottom: 1rem;
            text-shadow: 0 0 10px rgba(0, 0, 0, 0.5);
            background: linear-gradient(45deg, #ff7e5f, #feb47b);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
        }
        
        .hero-content p {
            font-size: 1.5rem;
            margin-bottom: 2rem;
            text-shadow: 0 0 5px rgba(0, 0, 0, 0.8);
        }
        
        /* Social Media Section */
        .social-section {
            padding: 80px 0;
            background-color: #0a0a0a;
            position: relative;
        }
        
        .social-section::before {
            content: '';
            position: absolute;
            top: -50px;
            left: 0;
            width: 100%;
            height: 100px;
            background: linear-gradient(to bottom, transparent, #0a0a0a);
        }
        
        .section-title {
            text-align: center;
            margin-bottom: 50px;
            font-size: 2.5rem;
            background: linear-gradient(45deg, #ff7e5f, #feb47b);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            opacity: 0;
            transform: translateY(20px);
            animation: fadeInUp 1s ease forwards 0.3s;
        }
        
        .social-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
            gap: 30px;
        }
        
        .social-card {
            background: rgba(255, 255, 255, 0.05);
            border-radius: 15px;
            overflow: hidden;
            box-shadow: 0 10px 25px rgba(0, 0, 0, 0.1);
            transition: all 0.3s ease;
            position: relative;
            backdrop-filter: blur(10px);
            opacity: 0;
            transform: translateY(30px);
        }
        
        .social-card:nth-child(1) { animation: fadeInUp 0.6s ease forwards 0.4s; }
        .social-card:nth-child(2) { animation: fadeInUp 0.6s ease forwards 0.6s; }
        .social-card:nth-child(3) { animation: fadeInUp 0.6s ease forwards 0.8s; }
        .social-card:nth-child(4) { animation: fadeInUp 0.6s ease forwards 1s; }
        .social-card:nth-child(5) { animation: fadeInUp 0.6s ease forwards 1.2s; }
        
        .social-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 15px 30px rgba(0, 0, 0, 0.2);
        }
        
        .social-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(45deg, rgba(255,126,95,0.15), rgba(254,180,123,0.15));
            opacity: 0;
            transition: opacity 0.3s ease;
        }
        
        .social-card:hover::before {
            opacity: 1;
        }
        
        .card-content {
            padding: 30px;
            position: relative;
            z-index: 1;
        }
        
        .platform-icon {
            font-size: 2.5rem;
            margin-bottom: 20px;
        }
        
        .kick-icon { color: #53FC18; }
        .instagram-icon { color: #E1306C; }
        .snapchat-icon { color: #FFFC00; }
        .discord-icon { color: #5865F2; }
        .twitter-icon { color: #1DA1F2; }
        
        .card-content h3 {
            font-size: 1.8rem;
            margin-bottom: 15px;
        }
        
        .card-content p {
            color: #b8b8b8;
            margin-bottom: 25px;
            line-height: 1.6;
        }
        
        .social-btn {
            display: inline-block;
            padding: 12px 25px;
            border-radius: 30px;
            text-decoration: none;
            font-weight: 600;
            letter-spacing: 1px;
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
            z-index: 1;
        }
        
        .social-btn::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 0;
            height: 100%;
            transition: all 0.3s ease;
            z-index: -1;
        }
        
        .social-btn:hover::before {
            width: 100%;
        }
        
        .kick-btn {
            background-color: #53FC18;
            color: #000000;
        }
        
        .kick-btn::before {
            background-color: #45d614;
        }
        
        .instagram-btn {
            background-color: #E1306C;
            color: #ffffff;
        }
        
        .instagram-btn::before {
            background-color: #c62b5f;
        }
        
        .snapchat-btn {
            background-color: #FFFC00;
            color: #000000;
        }
        
        .snapchat-btn::before {
            background-color: #e0dd00;
        }
        
        .discord-btn {
            background-color: #5865F2;
            color: #ffffff;
        }
        
        .discord-btn::before {
            background-color: #4752c4;
        }
        
        .twitter-btn {
            background-color: #1DA1F2;
            color: #ffffff;
        }
        
        .twitter-btn::before {
            background-color: #1a91da;
        }
        
        /* Footer */
        .footer {
            background-color:rgb(93, 25, 40);
            padding: 30px 0;
            text-align: center;
            border-top: 1px solid rgba(255, 255, 255, 0.1);
        }
        
        .footer p {
            color: #b8b8b8;
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
        
        /* Responsive Design */
        @media (max-width: 768px) {
            .hero-content h1 {
                font-size: 3rem;
            }
            
            .hero-content p {
                font-size: 1.2rem;
            }
            
            .section-title {
                font-size: 2rem;
            }
            
            .social-grid {
                grid-template-columns: 1fr;
            }
        }
    </style>
</head>
<body>
    <!-- Hero Section -->
    <section class="hero">
        <div class="hero-content">
            <h1>IMonkey_D</h1>
            <p>Connect with me across all platforms</p>
        </div>
    </section>
    
    <!-- Social Media Section -->
    <section class="social-section">
        <div class="container">
            <h2 class="section-title">Follow Me</h2>
            
            <div class="social-grid">
                <!-- Kick -->
                <div class="social-card">
                    <div class="card-content">
                        <i class="fa-solid fa-gamepad platform-icon kick-icon"></i>
                        <h3>Kick</h3>
                        <p>Watch my live streams and gaming content. Join me for exciting gameplay and entertainment!</p>
                        <a href="https://kick.com/imonkey_d" class="social-btn kick-btn" target="_blank">Follow on Kick</a>
                    </div>
                </div>
                
                <!-- Instagram -->
                <div class="social-card">
                    <div class="card-content">
                        <i class="fa-brands fa-instagram platform-icon instagram-icon"></i>
                        <h3>Instagram</h3>
                        <p>Check out my photos, stories, and daily updates. Get a glimpse into my world!</p>
                        <a href="https://www.instagram.com/imonkey_d/" class="social-btn instagram-btn" target="_blank">Follow on Instagram</a>
                    </div>
                </div>
                
                <!-- Snapchat -->
                <div class="social-card">
                    <div class="card-content">
                        <i class="fa-brands fa-snapchat platform-icon snapchat-icon"></i>
                        <h3>Snapchat</h3>
                        <p>Daily stories and behind-the-scenes content. Experience my day-to-day life!</p>
                        <a href="https://www.snapchat.com/add/imonkey_d" class="social-btn snapchat-btn" target="_blank">Add on Snapchat</a>
                    </div>
                </div>
                
                <!-- Discord -->
                <div class="social-card">
                    <div class="card-content">
                        <i class="fa-brands fa-discord platform-icon discord-icon"></i>
                        <h3>Discord</h3>
                        <p>Join my community and chat with other fans. Be part of an amazing community!</p>
                        <a href="https://discord.gg/vDaKNT8Mg7" class="social-btn discord-btn" target="_blank">Join Discord Server</a>
                    </div>
                </div>
                
                <!-- Twitter/X -->
                <div class="social-card">
                    <div class="card-content">
                        <i class="fa-brands fa-x-twitter platform-icon twitter-icon"></i>
                        <h3>X / Twitter</h3>
                        <p>Stay updated with my latest tweets and thoughts. Follow for real-time updates!</p>
                        <a href="https://twitter.com/iiMonkey_D" class="social-btn twitter-btn" target="_blank">Follow on X</a>
                    </div>
                </div>
            </div>
        </div>
    </section>
    
    <!-- Footer -->
    <footer class="footer">
        <div class="container">
            <p>&copy; 2025 IMonkey_D. All Rights Reserved.</p>
        </div>
    </footer>

    <script>
        // Intersection Observer for revealing elements on scroll
        document.addEventListener('DOMContentLoaded', function() {
            const observer = new IntersectionObserver((entries) => {
                entries.forEach(entry => {
                    if (entry.isIntersecting) {
                        entry.target.style.opacity = '1';
                        entry.target.style.transform = 'translateY(0)';
                    }
                });
            }, {
                threshold: 0.1
            });
            
            // Observe social cards
            document.querySelectorAll('.social-card').forEach(card => {
                observer.observe(card);
            });
        });
    </script>
</body>
</html>