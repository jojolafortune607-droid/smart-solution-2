<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Smart Solution | Divertissement Premium à Brazzaville</title>
  
  <!-- Fonts -->
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@300;400;500;600;700&family=Playfair+Display:ital,wght@0,400;0,600;0,700;1,400;1,600&display=swap" rel="stylesheet">
  
  <!-- Font Awesome -->
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
  
  <!-- Swiper CSS -->
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/swiper@10/swiper-bundle.min.css" />

  <style>
    /* ============================================================
       🎨 CHARTE GRAPHIQUE (THÈME BLANC & DORÉ)
       ============================================================ */
    :root {
      --noir:          #FFFFFF;
      --noir-surface:  #F8F9FA;
      --blanc:         #1A1A1A;
      --blanc-soft:    #555555;
      --or:            #C9A84C;
      --or-bright:     #B89530;
      --or-pale:       rgba(201,168,76,0.15);
      --surface-card:  #FFFFFF;
      --border-subtle: rgba(201,168,76,0.4);
      --vert-whatsapp: #25D366;
      --rouge-dispo:   #E53E3E;
      --font-title:    'Playfair Display', serif;
      --font-body:     'Montserrat', sans-serif;
    }

    /* RESET & BASE */
    * { margin: 0; padding: 0; box-sizing: border-box; }
    body {
      background-color: var(--noir);
      color: var(--blanc-soft);
      font-family: var(--font-body);
      overflow-x: hidden;
      line-height: 1.6;
      font-size: 16px;
    }
    h1, h2, h3, h4 { font-family: var(--font-title); color: var(--blanc); font-weight: 600; }
    a { color: inherit; text-decoration: none; transition: 0.3s ease; }
    ul { list-style: none; }
    button { cursor: pointer; border: none; font-family: inherit; transition: 0.3s ease; }
    
    /* UTILS */
    .container { width: 100%; max-width: 1200px; margin: 0 auto; padding: 0 20px; }
    .text-center { text-align: center; }
    .gold-text { color: var(--or); }
    .section-padding { padding: 80px 0; }

    /* ============================================================
       🌀 LOADER (ADAPTÉ)
       ============================================================ */
    #loader {
      position: fixed; inset: 0; background: var(--noir); z-index: 9999;
      display: flex; flex-direction: column; justify-content: center; align-items: center;
    }
    .loader-logo { width: 80px; height: 80px; margin-bottom: 20px; animation: pulse 1.5s infinite alternate; }
    .loader-text { font-family: var(--font-title); font-size: 24px; color: var(--or); opacity: 0; animation: fadeIn 1s 0.5s forwards; }
    @keyframes pulse { 0% { transform: scale(0.8); opacity: 0.7; } 100% { transform: scale(1.2); opacity: 1; filter: drop-shadow(0 0 15px var(--or)); } }
    @keyframes fadeIn { to { opacity: 1; } }

    /* ============================================================
       🍔 NAVBAR
       ============================================================ */
    .navbar {
      position: fixed; top: 0; width: 100%; z-index: 1000;
      padding: 20px 0; transition: all 0.4s ease;
      background: transparent;
    }
    .navbar.scrolled { background: rgba(255,255,255,0.95); backdrop-filter: blur(20px); padding: 15px 0; border-bottom: 1px solid var(--border-subtle); box-shadow: 0 2px 10px rgba(0,0,0,0.05); }
    .nav-container { display: flex; justify-content: space-between; align-items: center; max-width: 1400px; margin: 0 auto; padding: 0 20px; }
    .nav-brand { display: flex; align-items: center; gap: 12px; font-family: var(--font-title); font-size: 24px; color: var(--or); cursor: pointer; }
    .nav-brand svg { width: 40px; height: 40px; transition: 0.3s; }
    .nav-brand:hover svg { transform: rotate(5deg); filter: drop-shadow(0 0 10px var(--or-pale)); }
    .nav-links { display: flex; gap: 30px; align-items: center; }
    .nav-links a { position: relative; font-weight: 500; font-size: 15px; color: var(--blanc); }
    .nav-links a::after {
      content: ''; position: absolute; width: 100%; height: 2px; bottom: -5px; left: 0;
      background-color: var(--or); transform: scaleX(0); transform-origin: right; transition: transform 0.3s ease;
    }
    .nav-links a:hover::after, .nav-links a.active::after { transform: scaleX(1); transform-origin: left; }
    
    .nav-actions { display: flex; gap: 20px; align-items: center; }
    .cart-btn { position: relative; background: transparent; color: var(--blanc); font-size: 20px; }
    .cart-btn:hover { color: var(--or); }
    .cart-badge {
      position: absolute; top: -8px; right: -10px; background: var(--or); color: #fff;
      font-size: 11px; font-weight: bold; width: 18px; height: 18px; border-radius: 50%;
      display: flex; justify-content: center; align-items: center; display: none;
    }
    .mobile-menu-btn { display: none; font-size: 24px; background: transparent; color: var(--blanc); }

    @media (max-width: 768px) {
      .nav-links {
        position: absolute; top: 100%; left: 0; width: 100%; background: #fff;
        flex-direction: column; padding: 20px 0; gap: 20px; backdrop-filter: blur(20px);
        box-shadow: 0 10px 10px rgba(0,0,0,0.05);
        clip-path: polygon(0 0, 100% 0, 100% 0, 0 0); transition: 0.4s ease-in-out;
      }
      .nav-links a { color: var(--blanc); }
      .nav-links.active { clip-path: polygon(0 0, 100% 0, 100% 100%, 0 100%); }
      .mobile-menu-btn { display: block; }
    }

    /* ============================================================
       🎬 SECTION HERO (Contraste maintenu)
       ============================================================ */
    .hero { position: relative; height: 100vh; display: flex; align-items: center; justify-content: center; overflow: hidden; }
    .bg-video { position: absolute; inset: 0; width: 100%; height: 100%; object-fit: cover; z-index: 0; }
    .hero-overlay { position: absolute; inset: 0; background: rgba(0,0,0,0.75); z-index: 1; }
    #particles-js { position: absolute; inset: 0; z-index: 2; pointer-events: none; }
    .hero-content { position: relative; z-index: 3; text-align: center; max-width: 800px; padding: 0 20px; }
    
    .hero-line { width: 60px; height: 2px; background: var(--or); margin: 0 auto 20px; }
    .hero h1 { font-size: clamp(36px, 6vw, 72px); margin-bottom: 10px; text-transform: uppercase; letter-spacing: 2px; }
    .hero .subtitle { color: var(--or); font-size: clamp(14px, 2vw, 18px); letter-spacing: 4px; text-transform: uppercase; margin-bottom: 30px; }
    .typewriter-container { font-size: clamp(20px, 4vw, 32px); font-family: var(--font-title); height: 40px; margin-bottom: 40px; }
    .typewriter-text { color: var(--blanc); }
    .cursor { color: var(--or); animation: blink 1s infinite; }
    @keyframes blink { 50% { opacity: 0; } }

    .btn-primary {
      background: var(--or); color: var(--noir); padding: 15px 32px; border-radius: 8px;
      font-weight: 600; font-size: 16px; text-transform: uppercase; letter-spacing: 1px;
      display: inline-flex; align-items: center; gap: 10px; position: relative; overflow: hidden;
    }
    .btn-primary:hover { background: var(--or-bright); box-shadow: 0 0 20px rgba(201,168,76,0.4); transform: translateY(-2px); }
    .btn-whatsapp { background: var(--vert-whatsapp); color: var(--blanc); }
    .btn-whatsapp:hover { background: #1ebe57; box-shadow: 0 0 20px rgba(37,211,102,0.4); }
    .btn-disabled { background: #333 !important; color: #666 !important; cursor: not-allowed; box-shadow: none !important; }
    
    .scroll-indicator { position: absolute; bottom: 30px; left: 50%; transform: translateX(-50%); z-index: 3; color: var(--blanc); font-size: 24px; animation: bounce 2s infinite; }
    @keyframes bounce { 0%, 20%, 50%, 80%, 100% { transform: translateY(0) translateX(-50%); } 40% { transform: translateY(-15px) translateX(-50%); } 60% { transform: translateY(-7px) translateX(-50%); } }

    /* ============================================================
       📦 PRODUITS (CARTES) - Look Epuré
       ============================================================ */
    .section-title { font-size: 42px; margin-bottom: 10px; }
    .section-subtitle { color: var(--or); font-size: 14px; text-transform: uppercase; letter-spacing: 3px; margin-bottom: 50px; display: block; }
    
    .products-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(320px, 1fr)); gap: 24px; }
    .product-card {
      background: #fff; border: 1px solid rgba(0,0,0,0.1);
      border-radius: 16px; overflow: hidden; transition: 0.4s ease; display: flex; flex-direction: column;
      opacity: 0; transform: translateY(30px);
      box-shadow: 0 4px 20px rgba(0,0,0,0.03);
    }
    .product-card:hover { transform: translateY(-8px); border-color: var(--or); box-shadow: 0 20px 40px rgba(201,168,76,0.1); }
    
    .card-img-wrapper { position: relative; height: 200px; overflow: hidden; }
    .card-img { width: 100%; height: 100%; object-fit: cover; transition: 0.5s ease; }
    .product-card:hover .card-img { transform: scale(1.05); }
    .card-badge { position: absolute; top: 15px; right: 15px; background: var(--or); color: var(--noir); padding: 5px 12px; border-radius: 20px; font-size: 12px; font-weight: 700; letter-spacing: 1px; z-index: 2; }
    .btn-preview { position: absolute; bottom: 15px; right: 15px; background: rgba(0,0,0,0.6); color: var(--blanc); width: 40px; height: 40px; border-radius: 50%; display: flex; align-items: center; justify-content: center; backdrop-filter: blur(5px); z-index: 2; font-size: 18px; border: 1px solid rgba(255,255,255,0.2); }
    .btn-preview:hover { background: var(--or); color: var(--noir); border-color: var(--or); }
    
    .card-content { padding: 25px; flex-grow: 1; display: flex; flex-direction: column; }
    .card-title { font-size: 22px; margin-bottom: 5px; color: var(--blanc); }
    .card-subtitle { color: var(--or-bright); font-size: 14px; font-weight: 600; margin-bottom: 15px; text-transform: uppercase; }
    .card-desc { font-size: 14px; color: var(--blanc-soft); margin-bottom: 20px; flex-grow: 1; }
    
    .duration-pills { display: flex; gap: 10px; margin-bottom: 20px; background: #f4f4f4; padding: 5px; border-radius: 8px; }
    .pill { flex: 1; text-align: center; padding: 8px 0; font-size: 13px; font-weight: 600; cursor: pointer; border-radius: 6px; transition: 0.3s; color: var(--blanc-soft); }
    .pill.active { background: var(--or); color: #fff; }
    
    .card-price { font-size: 28px; font-family: var(--font-title); font-weight: 700; color: var(--blanc); margin-bottom: 20px; text-align: center; }
    .card-price span { font-size: 16px; font-family: var(--font-body); font-weight: 400; color: var(--or); }
    
    .card-actions { display: flex; flex-direction: column; gap: 10px; }
    .btn-text { background: transparent; color: var(--blanc-soft); text-decoration: underline; font-size: 14px; padding: 10px; text-align: center; }
    .btn-text:hover { color: var(--or); }

    /* ============================================================
       🌟 POURQUOI NOUS ? (FEATURES) - Fond clair
       ============================================================ */
    .features-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(250px, 1fr)); gap: 30px; }
    .feature-card { text-align: center; padding: 30px; background: #fff; border-radius: 16px; border: 1px solid rgba(0,0,0,0.05); transition: 0.3s; box-shadow: 0 4px 15px rgba(0,0,0,0.02); }
    .feature-card:hover { border-color: var(--or); transform: translateY(-5px); }
    .feature-icon { width: 70px; height: 70px; background: var(--or-pale); border-radius: 50%; display: flex; align-items: center; justify-content: center; margin: 0 auto 20px; font-size: 30px; color: var(--or); transition: 0.5s; }
    .feature-card:hover .feature-icon { transform: rotateY(180deg); background: var(--or); color: var(--noir); box-shadow: 0 0 20px var(--or-pale); }
    .feature-card h3 { font-size: 18px; margin-bottom: 15px; }
    .feature-card p { font-size: 14px; color: var(--blanc-soft); }

    /* ============================================================
       📱 FOOTER (Adapté au thème clair)
       ============================================================ */
    footer { background: #F8F9FA; padding: 60px 0 30px; border-top: 1px solid rgba(0,0,0,0.05); margin-top: 60px; color: var(--blanc); }
    .footer-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(250px, 1fr)); gap: 40px; margin-bottom: 40px; }
    .footer-col h4 { color: var(--or); font-family: var(--font-body); font-size: 16px; text-transform: uppercase; margin-bottom: 20px; letter-spacing: 1px; }
    .footer-links li { margin-bottom: 10px; }
    .footer-links a { color: var(--blanc-soft); font-size: 14px; }
    .footer-links a:hover { color: var(--or); padding-left: 5px; }
    .footer-bottom { text-align: center; padding-top: 30px; border-top: 1px solid rgba(0,0,0,0.05); font-size: 14px; color: #888; }

    /* ============================================================
       🔍 LIGHTBOX PLEIN ÉCRAN
       ============================================================ */
    #lightbox { position: fixed; inset: 0; background: rgba(0,0,0,0.95); z-index: 10000; display: flex; align-items: center; justify-content: center; opacity: 0; pointer-events: none; transition: 0.3s ease; }
    #lightbox.active { opacity: 1; pointer-events: auto; }
    .lb-close { position: absolute; top: 30px; right: 30px; font-size: 40px; color: var(--blanc); background: transparent; z-index: 2; }
    .lb-close:hover { color: var(--or); }
    .lb-img { max-width: 90vw; max-height: 90vh; object-fit: contain; opacity: 0; transition: opacity 0.3s; }
    .lb-img.loaded { opacity: 1; }
    .lb-nav { position: absolute; top: 50%; transform: translateY(-50%); font-size: 50px; color: rgba(255,255,255,0.5); background: transparent; padding: 20px; }
    .lb-nav:hover { color: var(--or); }
    .lb-prev { left: 20px; } .lb-next { right: 20px; }
    .lb-counter { position: absolute; bottom: 30px; left: 50%; transform: translateX(-50%); font-size: 18px; color: var(--or); font-weight: 600; letter-spacing: 2px; }

    /* ============================================================
       📋 MODAL CONTENU (CHAÎNES / JEUX)
       ============================================================ */
    #content-modal { position: fixed; inset: 0; background: rgba(10,10,10,0.97); backdrop-filter: blur(20px); z-index: 9999; display: flex; flex-direction: column; transform: translateY(100%); transition: transform 0.4s cubic-bezier(0.16, 1, 0.3, 1); }
    #content-modal.active { transform: translateY(0); }
    .modal-header { padding: 20px 40px; border-bottom: 1px solid var(--surface-card); display: flex; justify-content: space-between; align-items: center; }
    .modal-title { display: flex; align-items: center; gap: 15px; }
    .modal-title h2 { font-size: 24px; }
    .modal-title span { color: var(--or); font-size: 14px; text-transform: uppercase; }
    .modal-body { flex-grow: 1; overflow-y: auto; padding: 40px; }
    .modal-tools { display: flex; justify-content: space-between; align-items: center; margin-bottom: 30px; flex-wrap: wrap; gap: 20px; }
    .content-search { background: var(--surface-card); border: 1px solid var(--border-subtle); padding: 12px 20px; border-radius: 30px; color: var(--blanc); width: 300px; outline: none; }
    .content-search:focus { border-color: var(--or); }
    .chips-grid { display: flex; flex-wrap: wrap; gap: 12px; }
    .chip { background: rgba(255,255,255,0.05); padding: 10px 18px; border-radius: 30px; font-size: 14px; border: 1px solid transparent; transition: 0.2s; opacity: 0; transform: translateY(10px); }
    .chip:hover { background: var(--or); color: var(--noir); border-color: var(--or); }
    .modal-footer { padding: 20px 40px; border-top: 1px solid var(--surface-card); display: flex; justify-content: flex-end; gap: 20px; background: var(--noir); }

    /* ============================================================
       🛒 DRAWER PANIER
       ============================================================ */
    .cart-overlay { position: fixed; inset: 0; background: rgba(0,0,0,0.7); z-index: 10001; opacity: 0; pointer-events: none; transition: 0.3s; }
    .cart-overlay.active { opacity: 1; pointer-events: auto; }
    #cart-drawer { position: fixed; top: 0; right: 0; width: 400px; max-width: 100vw; height: 100vh; background: var(--noir-surface); border-left: 1px solid var(--border-subtle); z-index: 10002; transform: translateX(100%); transition: transform 0.4s cubic-bezier(0.16, 1, 0.3, 1); display: flex; flex-direction: column; }
    #cart-drawer.active { transform: translateX(0); }
    .cart-header { padding: 25px; border-bottom: 1px solid var(--surface-card); display: flex; justify-content: space-between; align-items: center; }
    .cart-header h3 { font-size: 20px; }
    .cart-items { flex-grow: 1; overflow-y: auto; padding: 20px; display: flex; flex-direction: column; gap: 15px; }
    .cart-item { background: var(--surface-card); padding: 15px; border-radius: 12px; display: flex; justify-content: space-between; align-items: center; border: 1px solid transparent; }
    .cart-item:hover { border-color: var(--border-subtle); }
    .cart-item-info h4 { font-size: 16px; margin-bottom: 5px; font-family: var(--font-body); }
    .cart-item-info p { color: var(--or); font-size: 13px; font-weight: 600; margin-bottom: 5px; }
    .cart-item-info span { color: var(--blanc-soft); font-size: 14px; }
    .btn-remove { background: transparent; color: #ff4d4d; font-size: 18px; padding: 5px; }
    .btn-remove:hover { color: #ff1a1a; filter: drop-shadow(0 0 5px rgba(255,0,0,0.5)); }
    .cart-footer { padding: 25px; border-top: 1px solid var(--surface-card); background: #0d0d0d; }
    .cart-total { display: flex; justify-content: space-between; font-size: 20px; font-weight: bold; margin-bottom: 20px; color: var(--blanc); }
    .cart-total span:last-child { color: var(--or); }
    .empty-cart { text-align: center; padding: 50px 20px; color: #666; }
    .empty-cart i { font-size: 60px; margin-bottom: 20px; opacity: 0.5; }

    /* ============================================================
       🍞 TOAST NOTIFICATION
       ============================================================ */
    #toast { position: fixed; bottom: 30px; right: 30px; background: var(--or); color: var(--noir); padding: 15px 25px; border-radius: 8px; font-weight: 600; font-size: 15px; box-shadow: 0 10px 30px rgba(201,168,76,0.3); z-index: 10005; transform: translateY(100px); opacity: 0; transition: 0.3s cubic-bezier(0.16, 1, 0.3, 1); display: flex; align-items: center; gap: 10px; }
    #toast.show { transform: translateY(0); opacity: 1; }

    /* ============================================================
       💬 BOUTON WHATSAPP FLOTTANT
       ============================================================ */
    .wa-float { position: fixed; bottom: 30px; right: 30px; background: var(--vert-whatsapp); width: 60px; height: 60px; border-radius: 50%; display: flex; justify-content: center; align-items: center; color: var(--blanc); font-size: 35px; z-index: 999; box-shadow: 0 5px 20px rgba(37,211,102,0.4); animation: wa-pulse 3s infinite; }
    .wa-float:hover { background: #1ebe57; color: var(--blanc); }
    @keyframes wa-pulse { 0% { transform: scale(1); box-shadow: 0 0 0 0 rgba(37,211,102,0.7); } 50% { transform: scale(1.1); box-shadow: 0 0 0 15px rgba(37,211,102,0); } 100% { transform: scale(1); box-shadow: 0 0 0 0 rgba(37,211,102,0); } }

    /* ============================================================
       📄 VUES DYNAMIQUES (SPA)
       ============================================================ */
    .view-section { display: none; animation: fadeIn 0.5s ease; }
    .view-section.active { display: block; }
    
    .category-hero { height: 60vh; position: relative; display: flex; align-items: center; justify-content: center; text-align: center; }
    .btn-back { position: absolute; top: 100px; left: 5%; z-index: 10; color: var(--or); font-weight: 600; display: flex; align-items: center; gap: 8px; background: rgba(0,0,0,0.5); padding: 10px 20px; border-radius: 30px; backdrop-filter: blur(5px); }
    .btn-back:hover { background: var(--or); color: var(--noir); }

    /* Swiper Styles */
    .swiper-container { width: 100%; padding-top: 50px; padding-bottom: 50px; overflow: hidden;}
    .swiper-slide { background-position: center; background-size: cover; width: 300px; height: 200px; border-radius: 12px; overflow: hidden; border: 1px solid var(--border-subtle); cursor: pointer; position: relative;}
    .swiper-slide::after { content:'🔍'; position:absolute; inset:0; background:rgba(0,0,0,0.5); display:flex; align-items:center; justify-content:center; font-size:30px; opacity:0; transition:0.3s; }
    .swiper-slide:hover::after { opacity:1; }
    .swiper-slide img { width: 100%; height: 100%; object-fit: cover; }
    .swiper-pagination-bullet { background: var(--blanc-soft); }
    .swiper-pagination-bullet-active { background: var(--or); }

    @media (max-width: 768px) {
      .modal-header, .modal-body, .modal-footer { padding: 20px; }
      .content-search { width: 100%; }
      .modal-tools { flex-direction: column; align-items: stretch; }
      .wa-float { bottom: 20px; right: 20px; width: 50px; height: 50px; font-size: 28px; }
      #toast { bottom: 85px; right: 20px; left: 20px; text-align: center; justify-content: center; }
    }
  </style>
</head>
<body>

  <!-- ==========================================
       🌀 LOADER
       ========================================== -->
  <div id="loader">
    <svg class="loader-logo" viewBox="0 0 100 100" fill="none" xmlns="http://www.w3.org/2000/svg">
      <circle cx="50" cy="50" r="48" stroke="#C9A84C" stroke-width="2" fill="#0a0a0a"/>
      <text x="50" y="65" font-family="'Playfair Display', serif" font-size="40" font-weight="bold" fill="#C9A84C" text-anchor="middle">SS</text>
    </svg>
    <div class="loader-text">Smart Solution</div>
  </div>

  <!-- ==========================================
       🍔 NAVBAR
       ========================================== -->
  <nav class="navbar" id="navbar">
    <div class="nav-container">
      <div class="nav-brand" onclick="app.navigate('home')">
        <svg viewBox="0 0 100 100" fill="none" xmlns="http://www.w3.org/2000/svg">
          <circle cx="50" cy="50" r="48" stroke="#C9A84C" stroke-width="2" fill="#0a0a0a"/>
          <text x="50" y="65" font-family="'Playfair Display', serif" font-size="40" font-weight="bold" fill="#C9A84C" text-anchor="middle">SS</text>
        </svg>
        <span>Smart Solution</span>
      </div>
      
      <div class="nav-links" id="nav-links">
        <a href="#home" onclick="app.navigate('home')" class="active">Accueil</a>
        <a href="#mycanal" onclick="app.navigate('mycanal')">MyCanal</a>
        <a href="#iptv" onclick="app.navigate('iptv')">IPTV</a>
        <a href="#gaming" onclick="app.navigate('gaming')">Gaming</a>
        <a href="#contact" onclick="app.navigate('home'); setTimeout(()=>document.getElementById('contact').scrollIntoView({behavior:'smooth'}), 100)">Contact</a>
      </div>

      <div class="nav-actions">
        <button class="cart-btn" onclick="app.toggleCart()">
          <i class="fa-solid fa-cart-shopping"></i>
          <span class="cart-badge" id="cart-badge">0</span>
        </button>
        <button class="mobile-menu-btn" onclick="document.getElementById('nav-links').classList.toggle('active')">
          <i class="fa-solid fa-bars"></i>
        </button>
      </div>
    </div>
  </nav>

  <!-- ==========================================
       🏠 VUE : ACCUEIL
       ========================================== -->
  <main id="view-home" class="view-section active">
    
    <!-- Hero -->
    <section class="hero">
      <!-- Fallback image/video using external sources for demo -->
      <video autoplay loop muted playsinline class="bg-video">
        <source src="https://cdn.pixabay.com/video/2020/05/25/40140-424835824_large.mp4" type="video/mp4">
      </video>
      <div class="hero-overlay"></div>
      <canvas id="particles-js"></canvas>
      
      <div class="hero-content">
        <div class="hero-line"></div>
        <h1 id="hero-title">Smart Solution</h1>
        <div class="subtitle">Brazzaville · Streaming · Gaming · IPTV</div>
        
        <div class="typewriter-container">
          <span class="typewriter-text" id="typewriter"></span><span class="cursor">|</span>
        </div>
        
        <button class="btn-primary" onclick="document.getElementById('produits').scrollIntoView({behavior:'smooth'})">
          Découvrir nos offres <i class="fa-solid fa-arrow-down"></i>
        </button>
      </div>
      
      <div class="scroll-indicator"><i class="fa-solid fa-chevron-down"></i></div>
    </section>

    <!-- Ticker -->
    <div class="ticker-wrap">
      <div class="ticker" id="ticker-content">
        <!-- Rempli par JS -->
      </div>
    </div>

    <!-- Produits -->
    <section id="produits" class="section-padding">
      <div class="container">
        <div class="text-center">
          <h2 class="section-title">Nos Abonnements</h2>
          <span class="section-subtitle">Qualité premium · Prix Congo Brazzaville</span>
        </div>
        <div class="products-grid" id="home-products-grid">
          <!-- Cartes générées par JS -->
        </div>
      </div>
    </section>

    <!-- Pourquoi Nous -->
    <section class="section-padding" style="background: var(--noir-surface);">
      <div class="container">
        <div class="text-center">
          <h2 class="section-title">Pourquoi Smart Solution ?</h2>
          <span class="section-subtitle">L'excellence à votre service</span>
        </div>
        <div class="features-grid">
          <div class="feature-card">
            <div class="feature-icon"><i class="fa-solid fa-bolt"></i></div>
            <h3>Activation Instantanée</h3>
            <p>Votre abonnement livré rapidement après confirmation du paiement.</p>
          </div>
          <div class="feature-card">
            <div class="feature-icon"><i class="fa-solid fa-shield-halved"></i></div>
            <h3>Paiement Sécurisé</h3>
            <p>Transactions fiables via les moyens de paiement locaux au Congo.</p>
          </div>
          <div class="feature-card">
            <div class="feature-icon"><i class="fa-solid fa-globe"></i></div>
            <h3>Pour tout le Congo</h3>
            <p>Disponible depuis Brazzaville, Pointe-Noire et toutes les villes.</p>
          </div>
          <div class="feature-card">
            <div class="feature-icon"><i class="fa-brands fa-whatsapp"></i></div>
            <h3>Support 7j/7</h3>
            <p>Notre équipe vous accompagne sur WhatsApp en cas de besoin.</p>
          </div>
        </div>
      </div>
    </section>
  </main>

  <!-- ==========================================
       📺 VUE : CATÉGORIE (MyCanal, IPTV, Gaming)
       ========================================== -->
  <main id="view-category" class="view-section">
    <button class="btn-back" onclick="app.navigate('home')"><i class="fa-solid fa-arrow-left"></i> Retour à l'accueil</button>
    
    <section class="category-hero" id="cat-hero">
      <video autoplay loop muted playsinline class="bg-video" id="cat-video"></video>
      <div class="hero-overlay" style="background: rgba(0,0,0,0.85);"></div>
      <div class="hero-content">
        <h1 id="cat-title" style="font-size: clamp(40px, 8vw, 80px);">Titre</h1>
        <div class="subtitle" id="cat-subtitle">Sous-titre</div>
      </div>
    </section>

    <section class="section-padding">
      <div class="container">
        <div class="products-grid" id="cat-products-grid">
          <!-- Cartes de la catégorie générées par JS -->
        </div>
      </div>
    </section>

    <section class="section-padding" style="background: var(--noir-surface); overflow: hidden;">
      <div class="container text-center">
        <h2 class="section-title">Aperçus de l'offre</h2>
        <span class="section-subtitle">Plongez dans l'expérience</span>
        
        <!-- Slider main container -->
        <div class="swiper-container mySwiper">
          <div class="swiper-wrapper" id="cat-swiper-wrapper">
            <!-- Slides générés par JS -->
          </div>
          <div class="swiper-pagination"></div>
        </div>
      </div>
    </section>
  </main>

  <!-- ==========================================
       FOOTER (Commun)
       ========================================== -->
  <footer id="contact">
    <div class="container">
      <div class="footer-grid">
        <div class="footer-col">
          <div class="nav-brand" style="margin-bottom: 20px;">
            <svg viewBox="0 0 100 100" fill="none" xmlns="http://www.w3.org/2000/svg" style="width: 30px; height: 30px;">
              <circle cx="50" cy="50" r="48" stroke="#C9A84C" stroke-width="2" fill="#0a0a0a"/>
              <text x="50" y="65" font-family="'Playfair Display', serif" font-size="40" font-weight="bold" fill="#C9A84C" text-anchor="middle">SS</text>
            </svg>
            <span style="font-size: 20px;">Smart Solution</span>
          </div>
          <p style="color: #aaa; font-size: 14px;">Votre divertissement premium, à Brazzaville. Le meilleur du streaming et du gaming, sans compromis.</p>
        </div>
        <div class="footer-col">
          <h4>Liens Rapides</h4>
          <ul class="footer-links">
            <li><a href="#home" onclick="app.navigate('home')">Accueil</a></li>
            <li><a href="#mycanal" onclick="app.navigate('mycanal')">MyCanal</a></li>
            <li><a href="#iptv" onclick="app.navigate('iptv')">IPTV Premium</a></li>
            <li><a href="#gaming" onclick="app.navigate('gaming')">Gaming (Xbox / PS)</a></li>
          </ul>
        </div>
        <div class="footer-col">
          <h4>Contact & Support</h4>
          <ul class="footer-links">
            <li><a href="https://wa.me/24206087924" target="_blank"><i class="fa-brands fa-whatsapp" style="color: var(--vert-whatsapp); margin-right: 8px;"></i> +242 06 087 92 4</a></li>
            <li><i class="fa-solid fa-location-dot" style="margin-right: 8px; color: var(--or);"></i> Brazzaville, Congo</li>
            <li><i class="fa-solid fa-clock" style="margin-right: 8px; color: var(--or);"></i> Support 7j/7</li>
          </ul>
        </div>
      </div>
      <div class="footer-bottom">
        &copy; <span id="year"></span> Smart Solution — Brazzaville, Congo. Tous droits réservés.
      </div>
    </div>
  </footer>

  <!-- ==========================================
       🛒 DRAWER PANIER
       ========================================== -->
  <div class="cart-overlay" id="cart-overlay" onclick="app.toggleCart()"></div>
  <aside id="cart-drawer">
    <div class="cart-header">
      <h3>Mon Panier 🛒</h3>
      <div style="display: flex; gap: 15px; align-items: center;">
        <button onclick="app.clearCart()" style="background:none; color:#ff4d4d; font-size: 14px; text-decoration:underline;">Vider</button>
        <button onclick="app.toggleCart()" style="background:none; color:var(--blanc); font-size:24px;">&times;</button>
      </div>
    </div>
    
    <div class="cart-items" id="cart-items-container">
      <!-- Items du panier injectés par JS -->
    </div>
    
    <div class="cart-footer">
      <div class="cart-total">
        <span>Total :</span>
        <span id="cart-total-price">0 FCFA</span>
      </div>
      <button class="btn-primary" style="width: 100%; justify-content: center; background: var(--vert-whatsapp); color: white;" onclick="app.checkoutWhatsApp()">
        <i class="fa-brands fa-whatsapp"></i> Commander sur WhatsApp
      </button>
      <button class="btn-primary" style="width: 100%; justify-content: center; margin-top: 10px; background: transparent; border: 1px solid var(--or); color: var(--or);" onclick="app.toggleCart()">
        Continuer mes achats
      </button>
    </div>
  </aside>

  <!-- ==========================================
       🔍 LIGHTBOX PLEIN ÉCRAN
       ========================================== -->
  <div id="lightbox">
    <button class="lb-close" onclick="app.closeLightbox()">&times;</button>
    <button class="lb-nav lb-prev" onclick="app.navigateLightbox(-1)"><i class="fa-solid fa-chevron-left"></i></button>
    <img src="" alt="Aperçu" class="lb-img" id="lb-image">
    <button class="lb-nav lb-next" onclick="app.navigateLightbox(1)"><i class="fa-solid fa-chevron-right"></i></button>
    <div class="lb-counter" id="lb-counter">1 / 3</div>
  </div>

  <!-- ==========================================
       📋 MODAL CONTENU (Chaînes / Jeux)
       ========================================== -->
  <div id="content-modal">
    <div class="modal-header">
      <div class="modal-title">
        <svg viewBox="0 0 100 100" fill="none" style="width: 30px;">
          <circle cx="50" cy="50" r="48" stroke="#C9A84C" stroke-width="2" fill="#0a0a0a"/>
          <text x="50" y="65" font-family="'Playfair Display', serif" font-size="40" font-weight="bold" fill="#C9A84C" text-anchor="middle">SS</text>
        </svg>
        <div>
          <h2 id="modal-product-name">Nom Produit</h2>
          <span id="modal-product-sub">Sous-titre</span>
        </div>
      </div>
      <button onclick="app.closeModal()" style="background:none; color:white; font-size:30px;">&times;</button>
    </div>
    
    <div class="modal-body">
      <div class="modal-tools">
        <h3 style="font-family: var(--font-body);"><span id="modal-count" class="gold-text">0</span> <span id="modal-type-label">chaînes</span> disponibles</h3>
        <input type="text" class="content-search" id="modal-search" placeholder="Rechercher..." onkeyup="app.filterModalContent()">
      </div>
      <div class="chips-grid" id="modal-chips-grid">
        <!-- Chips générés par JS -->
      </div>
    </div>
    
    <div class="modal-footer">
      <button class="btn-primary" style="background: transparent; border: 1px solid var(--blanc); color: var(--blanc);" onclick="app.closeModal()">Fermer</button>
      <button class="btn-primary btn-whatsapp" id="modal-btn-wa"><i class="fa-brands fa-whatsapp"></i> WhatsApp</button>
    </div>
  </div>

  <!-- ==========================================
       🍞 TOAST & BOUTON FLOTTANT
       ========================================== -->
  <div id="toast"><i class="fa-solid fa-check-circle"></i> <span>Ajouté au panier !</span></div>
  
  <a href="https://wa.me/24206087924" target="_blank" class="wa-float" title="Nous contacter">
    <i class="fa-brands fa-whatsapp"></i>
  </a>

  <!-- ============================================================
       SCRIPT JAVASCRIPT (Config + Logique)
       ============================================================ -->
  <!-- Librairies externes -->
  <script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.2/gsap.min.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/swiper@10/swiper-bundle.min.js"></script>
  
  <script>
    // ============================================================
    // ⚙️  CONFIG.JS — Smart Solution, Brazzaville
    // ============================================================
    // (J'ai remplacé les chemins locaux par des images Unsplash gratuites 
    // pour un rendu immédiat premium sans fichiers manquants. 
    // Tu pourras remettre tes liens "assets/images/..." ici).
    
    const CONFIG = {
      site: {
        nom:      "Smart Solution",
        slogan:   "Votre divertissement premium, à Brazzaville",
        whatsapp: "+24206087924",
        ville:    "Brazzaville, Congo",
      },

      videos: {
        // Utilisation de vidéos libres de droits pour la démo
        hero:    "https://cdn.pixabay.com/video/2020/05/25/40140-424835824_large.mp4",
        mycanal: "https://cdn.pixabay.com/video/2016/09/14/5217-181585258_large.mp4",
        iptv:    "https://cdn.pixabay.com/video/2022/08/17/128169-740590393_large.mp4",
        gaming:  "https://cdn.pixabay.com/video/2021/08/10/84518-587289569_large.mp4",
      },

      produits: [
        // ══════════════════════════════ MYCANAL — BASE
        {
          id:          "mycanal-base",
          page:        "mycanal",
          nom:         "MyCanal",
          sous_titre:  "Offre de Base",
          categorie:   "mycanal",
          description: "L'essentiel de Canal+ pour toute la famille. Films, séries et sport en HD.",
          badge:       null,
          carte_image: "https://images.unsplash.com/photo-1522869635100-9f4c5e86aa37?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80",
          en_stock:    true,
          tarifs: { "1 mois": 5000, "3 mois": 13000 },
          apercu_images: [
            "https://images.unsplash.com/photo-1593784991095-a205069470b6?ixlib=rb-4.0.3&auto=format&fit=crop&w=1280&q=80",
            "https://images.unsplash.com/photo-1600861194942-f883de0dfe96?ixlib=rb-4.0.3&auto=format&fit=crop&w=1280&q=80",
            "https://images.unsplash.com/photo-1560169897-fc0cdbdfa4d5?ixlib=rb-4.0.3&auto=format&fit=crop&w=1280&q=80",
          ],
          type_contenu: "chaînes",
          contenu: ["Canal+ Family", "Canal+ Series", "Canal+ Sport", "CNews", "BFM TV", "Disney Channel", "Cartoon Network", "MCM", "MTV", "Eurosport 1", "TV5 Monde", "RFI"],
        },

        // ══════════════════════════════ MYCANAL — PREMIUM
        {
          id:          "mycanal-premium",
          page:        "mycanal",
          nom:         "MyCanal",
          sous_titre:  "Premium",
          categorie:   "mycanal",
          description: "Plus de chaînes, plus de sport, plus de cinéma. L'expérience Canal+ complète.",
          badge:       "POPULAIRE",
          carte_image: "https://images.unsplash.com/photo-1585647347384-2593bc35786b?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80",
          en_stock:    true,
          tarifs: { "1 mois": 8000, "3 mois": 21000 },
          apercu_images: [
            "https://images.unsplash.com/photo-1626814026160-2237a95fc5a0?ixlib=rb-4.0.3&auto=format&fit=crop&w=1280&q=80",
            "https://images.unsplash.com/photo-1536440136628-849c177e76a1?ixlib=rb-4.0.3&auto=format&fit=crop&w=1280&q=80",
            "https://images.unsplash.com/photo-1518609878373-06d740f60d8b?ixlib=rb-4.0.3&auto=format&fit=crop&w=1280&q=80",
          ],
          type_contenu: "chaînes",
          contenu: ["Canal+ Family", "Canal+ Series", "Canal+ Sport", "Canal+ Cinéma", "BeIN Sports 1", "BeIN Sports 2", "OCS Max", "OCS City", "Paramount+", "SyFy", "National Geographic", "Discovery Channel", "Canal+ Kids", "Disney Channel", "Arte", "Eurosport 1-2"],
        },

        // ══════════════════════════════ MYCANAL — ULTRA
        {
          id:          "mycanal-ultra",
          page:        "mycanal",
          nom:         "MyCanal",
          sous_titre:  "Ultra Premium — Tout Canal",
          categorie:   "mycanal",
          description: "L'intégralité de l'univers Canal+ sans restriction. Aucun compromis.",
          badge:       "BEST VALUE",
          carte_image: "https://images.unsplash.com/photo-1595769816263-9b910be24d5f?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80",
          en_stock:    true,
          tarifs: { "1 mois": 12000, "3 mois": 32000 },
          apercu_images: [
            "https://images.unsplash.com/photo-1574375927938-d5a98e8ffe85?ixlib=rb-4.0.3&auto=format&fit=crop&w=1280&q=80",
            "https://images.unsplash.com/photo-1616469829581-73993eb86b02?ixlib=rb-4.0.3&auto=format&fit=crop&w=1280&q=80",
            "https://images.unsplash.com/photo-1605810230434-7631ac76ec81?ixlib=rb-4.0.3&auto=format&fit=crop&w=1280&q=80",
          ],
          type_contenu: "chaînes",
          contenu: ["Canal+ Family", "Canal+ Series", "Canal+ Sport", "Canal+ Cinéma", "Canal+ Kids", "Canal+ Docs", "Canal+ Décalé", "Canal+ Grand Écran", "BeIN Sports 1", "BeIN Sports 2", "BeIN Sports 3", "RMC Sport 1", "RMC Sport 2", "Eurosport 1", "Eurosport 2", "L'Équipe TV", "OCS Max", "OCS City", "OCS Choc", "OCS Géants", "Paramount+", "Disney+", "Apple TV+", "Netflix", "National Geographic", "Discovery", "SyFy", "MTV", "MCM", "Arte", "TV5 Monde", "CNews", "BFM TV", "LCI"],
        },

        // ══════════════════════════════ IPTV
        {
          id:          "iptv",
          page:        "iptv",
          nom:         "IPTV Premium",
          sous_titre:  "+10 000 Chaînes",
          categorie:   "iptv",
          description: "Le monde entier dans ton écran. Sport, cinéma, actualités, séries... Sans limite.",
          badge:       "+10 000 CHAÎNES",
          carte_image: "https://images.unsplash.com/photo-1560169897-fc0cdbdfa4d5?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80",
          en_stock:    true,
          tarifs: { "1 mois": 6000, "3 mois": 16000 },
          apercu_images: [
            "https://images.unsplash.com/photo-1540224871915-bc8ffb782bdf?ixlib=rb-4.0.3&auto=format&fit=crop&w=1280&q=80",
            "https://images.unsplash.com/photo-1489599849927-2ee91cede3ba?ixlib=rb-4.0.3&auto=format&fit=crop&w=1280&q=80",
            "https://images.unsplash.com/photo-1580202313707-b2e118f6c4be?ixlib=rb-4.0.3&auto=format&fit=crop&w=1280&q=80",
            "https://images.unsplash.com/photo-1498736297812-3a08021f206f?ixlib=rb-4.0.3&auto=format&fit=crop&w=1280&q=80",
          ],
          type_contenu: "chaînes",
          contenu: ["🌍 Afrique — Africa 24, TV5 Monde Afrique, NTA, ORTB, RTI, RTS, RTNC, DRTV", "🇫🇷 France — TF1, France 2, M6, Canal+, BFM TV, CNews, Arte, TMC, W9", "🇧🇪 Belgique — RTBF La Une, RTBF La Deux, RTL-TVI, Club RTL", "🇨🇭 Suisse — RTS Un, RTS Deux, SRF 1", "🇬🇧 UK — BBC One, BBC Two, ITV, Channel 4, Sky News", "🏆 Sport — BeIN Sports, ESPN, Sky Sports, RMC Sport, Eurosport, DAZN", "🎬 Cinéma — HBO, Showtime, Starz, Canal+ Cinéma, TCM Cinéma", "🎮 Gaming — G4, ESPN Esports, Twitch Top Streams", "🌐 International — CNN, BBC World, Al Jazeera, Fox News, DW, France 24", "🧒 Enfants — Disney Channel, Cartoon Network, Nickelodeon, Gulli, TiJi", "📚 Documentaires — National Geographic, Discovery, History Channel, RMC Découverte", "🎵 Musique — MTV, MCM, M6 Music, MTV Base Africa"],
        },

        // ══════════════════════════════ GAME PASS
        {
          id:          "gamepass",
          page:        "gaming",
          nom:         "Xbox Game Pass",
          sous_titre:  "Ultimate",
          categorie:   "gaming",
          description: "Accès illimité à +100 jeux Xbox et PC, dont les sorties Day One.",
          badge:       "DAY ONE",
          carte_image: "https://images.unsplash.com/photo-1621259182978-fbf93132d53d?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80",
          en_stock:    true,
          tarifs: { "1 mois": 5500, "3 mois": 14500 },
          apercu_images: [
            "https://images.unsplash.com/photo-1542751371-adc38448a05e?ixlib=rb-4.0.3&auto=format&fit=crop&w=1280&q=80",
            "https://images.unsplash.com/photo-1605901309584-818e25960b8f?ixlib=rb-4.0.3&auto=format&fit=crop&w=1280&q=80",
            "https://images.unsplash.com/photo-1511512578047-dfb367046420?ixlib=rb-4.0.3&auto=format&fit=crop&w=1280&q=80",
          ],
          type_contenu: "jeux",
          contenu: ["Halo Infinite", "Forza Horizon 5", "Forza Motorsport", "Starfield", "Diablo IV", "Sea of Thieves", "Minecraft", "Minecraft Legends", "Age of Empires IV", "GTA V", "Cyberpunk 2077", "The Witcher 3", "FIFA 24", "Assassin's Creed Valhalla", "Redfall", "Lies of P", "Mortal Kombat 11", "EA Sports FC 24", "Hollow Knight", "Vampire Survivors", "Ori and the Will of the Wisps"],
        },

        // ══════════════════════════════ PS PLUS
        {
          id:          "psplus",
          page:        "gaming",
          nom:         "PlayStation Plus",
          sous_titre:  "Premium",
          categorie:   "gaming",
          description: "Le meilleur du gaming PlayStation. Multijoueur en ligne + jeux offerts chaque mois.",
          badge:       "PS5 OPTIMISÉ",
          carte_image: "https://images.unsplash.com/photo-1606144042614-b2417e99c4e3?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80",
          en_stock:    false, // Exemple hors stock !
          tarifs: { "1 mois": 5500, "3 mois": 14500 },
          apercu_images: [
            "https://images.unsplash.com/photo-1580234797602-22c37b4a6217?ixlib=rb-4.0.3&auto=format&fit=crop&w=1280&q=80",
            "https://images.unsplash.com/photo-1600861194942-f883de0dfe96?ixlib=rb-4.0.3&auto=format&fit=crop&w=1280&q=80",
            "https://images.unsplash.com/photo-1550745165-9bc0b252726f?ixlib=rb-4.0.3&auto=format&fit=crop&w=1280&q=80",
          ],
          type_contenu: "jeux",
          contenu: ["Spider-Man 2", "Spider-Man: Miles Morales", "God of War Ragnarök", "God of War (2018)", "The Last of Us Part I", "The Last of Us Part II", "Horizon Forbidden West", "Horizon Zero Dawn", "Gran Turismo 7", "Ghost of Tsushima", "Ratchet & Clank: Rift Apart", "Returnal", "Demon's Souls", "Astro's Playroom", "Sackboy: A Big Adventure", "FIFA 24", "EA Sports FC 24", "Mortal Kombat 11", "Resident Evil Village", "Resident Evil 4 Remake", "Final Fantasy XVI", "Hogwarts Legacy"],
        },
      ]
    };

    // ============================================================
    // 🧠 LOGIQUE DE L'APPLICATION (MAIN.JS intégré)
    // ============================================================
    
    const app = {
      cart: JSON.parse(localStorage.getItem('smartsolution_cart')) || [],
      currentLightboxImages: [],
      currentLightboxIndex: 0,
      activeDurations: {}, // Stocke la durée sélectionnée par produit
      swiperInstance: null,

      init() {
        // Init UI
        document.getElementById('year').textContent = new Date().getFullYear();
        this.setupTicker();
        this.initTypewriter();
        this.initParticles();
        this.renderCart();
        
        // Loader logic
        setTimeout(() => {
          gsap.to('#loader', { opacity: 0, y: '-100%', duration: 0.8, ease: 'power3.inOut', onComplete: () => {
            document.getElementById('loader').style.display = 'none';
            // Start hero animations
            gsap.from('.hero h1', {y: 50, opacity: 0, duration: 1, ease: 'power3.out'});
            gsap.from('.hero .subtitle', {y: 30, opacity: 0, duration: 1, delay: 0.2, ease: 'power3.out'});
          }});
        }, 1500);

        // Scroll events
        window.addEventListener('scroll', () => {
          const nav = document.getElementById('navbar');
          if (window.scrollY > 50) nav.classList.add('scrolled');
          else nav.classList.remove('scrolled');
        });

        // Initialize Home view
        this.renderProductsGrid(CONFIG.produits, 'home-products-grid');
        
        // Handle Routing
        window.addEventListener('hashchange', () => this.handleRoute());
        this.handleRoute(); // Call on init
      },

      // --- ROUTER (SPA) ---
      navigate(route) {
        window.location.hash = route;
        if(window.innerWidth <= 768) document.getElementById('nav-links').classList.remove('active');
      },

      handleRoute() {
        const hash = window.location.hash.replace('#', '') || 'home';
        document.querySelectorAll('.view-section').forEach(el => el.classList.remove('active'));
        document.querySelectorAll('.nav-links a').forEach(a => a.classList.remove('active'));
        
        // Activer le lien nav
        const activeLink = document.querySelector(`.nav-links a[href="#${hash}"]`);
        if(activeLink) activeLink.classList.add('active');

        if (hash === 'home') {
          document.getElementById('view-home').classList.add('active');
          window.scrollTo(0, 0);
          this.animateCards('#home-products-grid');
        } else {
          document.getElementById('view-category').classList.add('active');
          window.scrollTo(0, 0);
          this.setupCategoryView(hash);
        }
      },

      setupCategoryView(catKey) {
        // Titres & Vidéo Hero de catégorie
        const titles = {
          'mycanal': { t: 'MyCanal', s: 'Tout le divertissement Canal+', v: CONFIG.videos.mycanal },
          'iptv': { t: 'IPTV Premium', s: 'Le monde entier dans ton écran', v: CONFIG.videos.iptv },
          'gaming': { t: 'Gaming', s: 'Xbox Game Pass & PlayStation Plus', v: CONFIG.videos.gaming },
        };
        const info = titles[catKey] || titles['mycanal'];
        
        document.getElementById('cat-title').textContent = info.t;
        document.getElementById('cat-subtitle').textContent = info.s;
        document.getElementById('cat-video').src = info.v;

        // Filtrer les produits
        const catProducts = CONFIG.produits.filter(p => p.page === catKey);
        this.renderProductsGrid(catProducts, 'cat-products-grid');
        this.animateCards('#cat-products-grid');

        // Récupérer toutes les images d'aperçu de cette catégorie
        const allPreviews = catProducts.flatMap(p => p.apercu_images);
        const swiperWrapper = document.getElementById('cat-swiper-wrapper');
        swiperWrapper.innerHTML = allPreviews.map((img, index) => `
          <div class="swiper-slide" onclick="app.openLightboxCategory(${index}, '${catKey}')">
            <img src="${img}" alt="Preview" loading="lazy">
          </div>
        `).join('');

        // Init Swiper
        if (this.swiperInstance) this.swiperInstance.destroy();
        this.swiperInstance = new Swiper('.mySwiper', {
          slidesPerView: 1,
          spaceBetween: 20,
          pagination: { el: '.swiper-pagination', clickable: true },
          breakpoints: { 640: { slidesPerView: 2 }, 1024: { slidesPerView: 3 } }
        });
      },

      // --- RENDERING CARDS ---
      renderProductsGrid(products, containerId) {
        const container = document.getElementById(containerId);
        container.innerHTML = products.map(prod => {
          // Set default duration if not set
          if (!this.activeDurations[prod.id]) {
            this.activeDurations[prod.id] = Object.keys(prod.tarifs)[0];
          }
          const activeDur = this.activeDurations[prod.id];
          const price = prod.tarifs[activeDur];

          // Générer les pills de durée
          const pillsHtml = Object.keys(prod.tarifs).map(dur => `
            <div class="pill ${dur === activeDur ? 'active' : ''}" 
                 onclick="app.changeDuration('${prod.id}', '${dur}', '${containerId}')">${dur}</div>
          `).join('');

          const btnAddCart = prod.en_stock 
            ? `<button class="btn-primary" style="width:100%; justify-content:center;" onclick="app.addToCart('${prod.id}')"><i class="fa-solid fa-cart-shopping"></i> Ajouter au panier</button>`
            : `<button class="btn-primary btn-disabled" style="width:100%; justify-content:center;" disabled>Indisponible</button>`;

          return `
            <div class="product-card" id="card-${prod.id}">
              <div class="card-img-wrapper">
                <img src="${prod.carte_image}" alt="${prod.nom}" class="card-img" loading="lazy">
                ${prod.badge ? `<div class="card-badge">${prod.badge}</div>` : ''}
                <button class="btn-preview" onclick="app.openLightboxProduct('${prod.id}')"><i class="fa-solid fa-magnifying-glass"></i></button>
              </div>
              <div class="card-content">
                <h3 class="card-title">${prod.nom}</h3>
                <div class="card-subtitle">${prod.sous_titre}</div>
                <p class="card-desc">${prod.description}</p>
                
                <div class="duration-pills">${pillsHtml}</div>
                
                <div class="card-price" id="price-${prod.id}">
                  ${price.toLocaleString('fr-FR')} <span>FCFA</span>
                </div>
                
                <div class="card-actions">
                  ${btnAddCart}
                  <button class="btn-text" onclick="app.openModal('${prod.id}')">
                    <i class="fa-solid fa-list"></i> Voir les ${prod.type_contenu}
                  </button>
                </div>
              </div>
            </div>
          `;
        }).join('');
      },

      animateCards(containerSelector) {
        gsap.to(`${containerSelector} .product-card`, {
          y: 0, opacity: 1, duration: 0.6, stagger: 0.1, ease: 'back.out(1.7)',
          scrollTrigger: { trigger: containerSelector, start: 'top 80%' }
        });
      },

      changeDuration(productId, duration, containerId) {
        this.activeDurations[productId] = duration;
        // Re-render only the specific container to avoid heavy DOM wipes
        this.renderProductsGrid(
          containerId === 'home-products-grid' ? CONFIG.produits : CONFIG.produits.filter(p => p.page === window.location.hash.replace('#','')),
          containerId
        );
        // Force opacity to 1 because re-render removes GSAP inline styles
        document.querySelectorAll(`#${containerId} .product-card`).forEach(el => {
          el.style.opacity = '1'; el.style.transform = 'translateY(0)';
        });
      },

      // --- CART SYSTEM ---
      addToCart(productId) {
        const prod = CONFIG.produits.find(p => p.id === productId);
        const duree = this.activeDurations[productId];
        const prix = prod.tarifs[duree];
        
        this.cart.push({ id: Date.now().toString(), productId, nom: prod.nom, sous_titre: prod.sous_titre, duree, prix });
        this.saveCart();
        
        // Animate icon
        gsap.fromTo('.cart-btn', {rotation: -20}, {rotation: 20, duration: 0.1, yoyo: true, repeat: 3});
        this.showToast(`Ajouté : ${prod.nom} (${duree})`);
      },

      removeFromCart(cartItemId) {
        this.cart = this.cart.filter(item => item.id !== cartItemId);
        this.saveCart();
      },

      clearCart() {
        if(confirm('Voulez-vous vider votre panier ?')) {
          this.cart = [];
          this.saveCart();
        }
      },

      saveCart() {
        localStorage.setItem('smartsolution_cart', JSON.stringify(this.cart));
        this.renderCart();
      },

      renderCart() {
        const badge = document.getElementById('cart-badge');
        badge.textContent = this.cart.length;
        badge.style.display = this.cart.length > 0 ? 'flex' : 'none';

        const container = document.getElementById('cart-items-container');
        if (this.cart.length === 0) {
          container.innerHTML = `
            <div class="empty-cart">
              <i class="fa-solid fa-basket-shopping"></i>
              <p>Votre panier est vide.</p>
            </div>
          `;
          document.getElementById('cart-total-price').textContent = '0 FCFA';
          return;
        }

        let total = 0;
        container.innerHTML = this.cart.map(item => {
          total += item.prix;
          return `
            <div class="cart-item">
              <div class="cart-item-info">
                <h4>${item.nom}</h4>
                <p>${item.sous_titre} — ${item.duree}</p>
                <span>${item.prix.toLocaleString('fr-FR')} FCFA</span>
              </div>
              <button class="btn-remove" onclick="app.removeFromCart('${item.id}')"><i class="fa-solid fa-trash"></i></button>
            </div>
          `;
        }).join('');

        document.getElementById('cart-total-price').textContent = `${total.toLocaleString('fr-FR')} FCFA`;
      },

      toggleCart() {
        document.getElementById('cart-drawer').classList.toggle('active');
        document.getElementById('cart-overlay').classList.toggle('active');
      },

      checkoutWhatsApp() {
        if (this.cart.length === 0) return this.showToast("Votre panier est vide.");
        
        let text = `Bonjour Smart Solution 👋\n\nJe souhaite commander :\n`;
        let total = 0;
        
        this.cart.forEach(item => {
          text += `✦ ${item.nom} ${item.sous_titre} — ${item.duree} : ${item.prix.toLocaleString('fr-FR')} FCFA\n`;
          total += item.prix;
        });
        
        text += `\nTotal : ${total.toLocaleString('fr-FR')} FCFA\n\nMerci !`;
        
        const url = `https://wa.me/${CONFIG.site.whatsapp.replace('+', '')}?text=${encodeURIComponent(text)}`;
        window.open(url, '_blank');
      },

      // --- MODALS & LIGHTBOX ---
      openLightboxProduct(productId) {
        const prod = CONFIG.produits.find(p => p.id === productId);
        this.currentLightboxImages = prod.apercu_images;
        this.showLightbox(0);
      },

      openLightboxCategory(index, catKey) {
        const catProducts = CONFIG.produits.filter(p => p.page === catKey);
        this.currentLightboxImages = catProducts.flatMap(p => p.apercu_images);
        this.showLightbox(index);
      },

      showLightbox(index) {
        this.currentLightboxIndex = index;
        const lb = document.getElementById('lightbox');
        const img = document.getElementById('lb-image');
        
        img.classList.remove('loaded');
        setTimeout(() => {
          img.src = this.currentLightboxImages[index];
          img.onload = () => img.classList.add('loaded');
          document.getElementById('lb-counter').textContent = `${index + 1} / ${this.currentLightboxImages.length}`;
        }, 300);

        lb.classList.add('active');
      },

      navigateLightbox(dir) {
        let newIndex = this.currentLightboxIndex + dir;
        if (newIndex < 0) newIndex = this.currentLightboxImages.length - 1;
        if (newIndex >= this.currentLightboxImages.length) newIndex = 0;
        this.showLightbox(newIndex);
      },

      closeLightbox() {
        document.getElementById('lightbox').classList.remove('active');
      },

      // Modal Contenu (Chaînes/Jeux)
      openModal(productId) {
        const prod = CONFIG.produits.find(p => p.id === productId);
        document.getElementById('modal-product-name').textContent = prod.nom;
        document.getElementById('modal-product-sub').textContent = prod.sous_titre;
        document.getElementById('modal-type-label').textContent = prod.type_contenu;
        
        this.currentModalContent = prod.contenu;
        this.renderModalChips(this.currentModalContent);
        
        // Counter animation
        const countEl = document.getElementById('modal-count');
        countEl.textContent = '0';
        gsap.to(countEl, { innerHTML: prod.contenu.length, duration: 1.5, snap: "innerHTML", ease: "power1.out" });

        // Bouton WhatsApp direct pour ce produit
        document.getElementById('modal-btn-wa').onclick = () => {
          const text = `Bonjour Smart Solution 👋\nJe suis intéressé par : ${prod.nom} ${prod.sous_titre}.\nMerci !`;
          window.open(`https://wa.me/${CONFIG.site.whatsapp.replace('+','')}?text=${encodeURIComponent(text)}`, '_blank');
        };

        document.getElementById('modal-search').value = '';
        document.getElementById('content-modal').classList.add('active');
      },

      renderModalChips(items) {
        const grid = document.getElementById('modal-chips-grid');
        grid.innerHTML = items.map(item => `<div class="chip">${item}</div>`).join('');
        gsap.to('.chip', { y: 0, opacity: 1, duration: 0.3, stagger: 0.02, ease: "power2.out" });
      },

      filterModalContent() {
        const query = document.getElementById('modal-search').value.toLowerCase();
        const filtered = this.currentModalContent.filter(item => item.toLowerCase().includes(query));
        this.renderModalChips(filtered);
        document.getElementById('modal-count').textContent = filtered.length;
      },

      closeModal() {
        document.getElementById('content-modal').classList.remove('active');
      },

      showToast(msg) {
        const toast = document.getElementById('toast');
        toast.querySelector('span').textContent = msg;
        toast.classList.add('show');
        setTimeout(() => toast.classList.remove('show'), 2500);
      },

      // --- EFFETS VISUELS ---
      setupTicker() {
        const items = [
          "✦ MyCanal Premium", "✦ MyCanal Ultra — Tout Canal", "✦ IPTV +10 000 Chaînes",
          "✦ Xbox GamePass Ultimate", "✦ PlayStation Plus", "✦ Activation Instantanée", "✦ Brazzaville, Congo"
        ];
        // Répéter pour l'effet infini
        document.getElementById('ticker-content').innerHTML = [...items, ...items, ...items, ...items].map(i => `<span class="ticker-item">${i}</span>`).join('');
      },

      initTypewriter() {
        const words = ["MyCanal Premium & Ultra", "+10 000 Chaînes IPTV", "Xbox GamePass Ultimate", "PlayStation Plus Premium"];
        let i = 0;
        let timer;
        const el = document.getElementById('typewriter');
        
        function typingEffect() {
          let word = words[i].split('');
          var loopTyping = function() {
            if (word.length > 0) {
              el.innerHTML += word.shift();
            } else {
              setTimeout(deletingEffect, 2000);
              return false;
            }
            timer = setTimeout(loopTyping, 80);
          };
          loopTyping();
        }

        function deletingEffect() {
          let word = words[i].split('');
          var loopDeleting = function() {
            if (word.length > 0) {
              word.pop();
              el.innerHTML = word.join('');
            } else {
              if (words.length > (i + 1)) i++; else i = 0;
              typingEffect();
              return false;
            }
            timer = setTimeout(loopDeleting, 40);
          };
          loopDeleting();
        }
        typingEffect();
      },

      initParticles() {
        const canvas = document.getElementById('particles-js');
        const ctx = canvas.getContext('2d');
        canvas.width = window.innerWidth;
        canvas.height = window.innerHeight;

        const particlesArray = [];
        class Particle {
          constructor() {
            this.x = Math.random() * canvas.width;
            this.y = Math.random() * canvas.height;
            this.size = Math.random() * 2 + 1;
            this.speedX = Math.random() * 0.5 - 0.25;
            this.speedY = Math.random() * 0.5 - 0.25;
          }
          update() {
            this.x += this.speedX;
            this.y += this.speedY;
            if(this.x > canvas.width) this.x = 0;
            if(this.x < 0) this.x = canvas.width;
            if(this.y > canvas.height) this.y = 0;
            if(this.y < 0) this.y = canvas.height;
          }
          draw() {
            ctx.fillStyle = 'rgba(201, 168, 76, 0.5)';
            ctx.beginPath();
            ctx.arc(this.x, this.y, this.size, 0, Math.PI * 2);
            ctx.fill();
          }
        }

        for (let i = 0; i < 30; i++) particlesArray.push(new Particle());

        function animate() {
          ctx.clearRect(0, 0, canvas.width, canvas.height);
          particlesArray.forEach(p => { p.update(); p.draw(); });
          requestAnimationFrame(animate);
        }
        animate();

        window.addEventListener('resize', () => {
          canvas.width = window.innerWidth;
          canvas.height = window.innerHeight;
        });
      }
    };

    // Keyboard events pour lightbox/modal
    window.addEventListener('keydown', (e) => {
      if (e.key === 'Escape') {
        app.closeLightbox();
        app.closeModal();
        document.getElementById('cart-drawer').classList.remove('active');
        document.getElementById('cart-overlay').classList.remove('active');
      }
      if (e.key === 'ArrowRight' && document.getElementById('lightbox').classList.contains('active')) app.navigateLightbox(1);
      if (e.key === 'ArrowLeft' && document.getElementById('lightbox').classList.contains('active')) app.navigateLightbox(-1);
    });

    // Démarrage de l'app
    document.addEventListener('DOMContentLoaded', () => app.init());

  </script>
</body>
</html>
