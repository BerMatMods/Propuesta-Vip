
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=no" />
  <title>¿Quieres ser mi novia? 💖</title>

  <!-- Google Fonts -->
  <link href="https://fonts.googleapis.com/css2?family=Dancing+Script:wght@700&family=Playfair+Display:wght@700&family=Poppins:wght@400;500&display=swap" rel="stylesheet">

  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      font-family: 'Poppins', sans-serif;
      background: linear-gradient(135deg, #fff5f8, #f9e6ff, #ffe6f0);
      color: #444;
      min-height: 100vh;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      padding: 20px;
      overflow: hidden;
      position: relative;
    }

    /* Botón del menú */
    .menu-btn {
      position: absolute;
      top: 20px;
      left: 20px;
      width: 50px;
      height: 50px;
      background: rgba(233, 30, 99, 0.2);
      border-radius: 50%;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      cursor: pointer;
      z-index: 100;
      box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
      transition: all 0.3s;
    }

    .menu-btn span {
      display: block;
      width: 24px;
      height: 3px;
      background: #e91e63;
      margin: 3px 0;
      border-radius: 2px;
      transition: 0.3s;
    }

    .menu-btn:hover {
      transform: scale(1.1);
      background: rgba(233, 30, 99, 0.3);
    }

    /* Menú desplegable */
    .menu {
      position: fixed;
      top: 0;
      left: -300px;
      width: 280px;
      height: 100vh;
      background: rgba(255, 255, 255, 0.98);
      backdrop-filter: blur(10px);
      box-shadow: 0 0 30px rgba(0, 0, 0, 0.1);
      padding: 60px 20px 20px;
      transition: left 0.4s ease;
      z-index: 99;
      border-radius: 0 20px 20px 0;
      border-left: 3px solid #e91e63;
      overflow-y: auto;
    }

    .menu.open {
      left: 0;
    }

    .menu-logo {
      width: 100px;
      height: 100px;
      border-radius: 50%;
      object-fit: cover;
      border: 4px solid #e91e63;
      box-shadow: 0 4px 12px rgba(233, 30, 99, 0.3);
      margin: 0 auto 1.2rem;
      display: block;
    }

    .menu h3 {
      font-family: 'Playfair Display', serif;
      color: #e91e63;
      margin-bottom: 1.2rem;
      font-size: 1.4rem;
      border-bottom: 2px solid #ffb6c1;
      padding-bottom: 0.5rem;
    }

    .menu p {
      color: #555;
      font-size: 0.95rem;
      line-height: 1.5;
      margin-bottom: 1rem;
    }

    .whatsapp-btn {
      display: block;
      margin: 1.8rem 0 0;
      padding: 1.1rem 1.4rem;
      background: linear-gradient(45deg, #25D366, #128C7E);
      color: white;
      text-align: center;
      border-radius: 14px;
      text-decoration: none;
      font-weight: 500;
      font-size: 1.05rem;
      box-shadow: 0 6px 15px rgba(37, 211, 102, 0.4);
      transition: all 0.3s;
    }

    .whatsapp-btn:hover {
      transform: scale(1.05);
      box-shadow: 0 8px 20px rgba(37, 211, 102, 0.5);
    }

    .close-menu {
      position: absolute;
      top: 20px;
      right: 20px;
      font-size: 1.5rem;
      color: #e91e63;
      cursor: pointer;
    }

    /* Contenedor de propuesta */
    .proposal-container {
      text-align: center;
      max-width: 440px;
      padding: 2.6rem 2rem;
      background: rgba(255, 255, 255, 0.95);
      border-radius: 30px;
      box-shadow: 0 15px 40px rgba(255, 105, 180, 0.3);
      border: 4px solid transparent;
      background-clip: padding-box;
      position: relative;
      z-index: 2;
    }

    .proposal-container::before {
      content: '';
      position: absolute;
      inset: 0;
      border-radius: 30px;
      padding: 4px;
      background: linear-gradient(45deg, #ff80ab, #ba68c8);
      -webkit-mask: linear-gradient(#fff 0 0) content-box, linear-gradient(#fff 0 0);
      -webkit-mask-composite: destination-out;
      mask-composite: subtract;
      pointer-events: none;
    }

    .proposal-container h2 {
      font-family: 'Playfair Display', serif;
      font-size: 2.4rem;
      background: linear-gradient(45deg, #e91e63, #ba68c8);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      background-clip: text;
      margin-bottom: 1.3rem;
    }

    .proposal-container p {
      color: #d81b60;
      font-size: 1.18rem;
      margin-bottom: 1.6rem;
      line-height: 1.7;
      font-weight: 500;
    }

    /* Botones */
    .btn-group {
      display: flex;
      gap: 18px;
      justify-content: center;
      flex-wrap: wrap;
      margin-top: 1rem;
    }

    .btn {
      padding: 0.95rem 1.7rem;
      border: none;
      border-radius: 32px;
      font-size: 1.12rem;
      font-weight: 600;
      cursor: pointer;
      transition: all 0.3s;
      box-shadow: 0 6px 15px rgba(0, 0, 0, 0.1);
    }

    .btn-si {
      background: linear-gradient(45deg, #e91e63, #ba68c8);
      color: white;
    }

    .btn-si:hover {
      transform: scale(1.12);
      box-shadow: 0 8px 22px rgba(233, 30, 99, 0.45);
    }

    .btn-no {
      background: #fff;
      color: #e91e63;
      border: 2px solid #e91e63;
      position: absolute;
      transition: all 0.3s;
    }

    .btn-no:hover {
      background: #ffe6f0;
      transform: scale(1.06);
    }

    /* CUADROS DE INSISTENCIA (NEÓN) */
    .insist-box {
      position: fixed;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%) scale(0.8);
      max-width: 360px;
      background: #fffaf0;
      border-radius: 20px;
      padding: 1.8rem 1.6rem;
      text-align: center;
      z-index: 1000;
      box-shadow: 0 10px 30px rgba(255, 105, 180, 0.2);
      border: 3px solid transparent;
      background-clip: padding-box;
      animation: popIn 0.6s ease-out forwards, glowPulse 2s infinite alternate;
      opacity: 0;
    }

    .insist-box::before {
      content: '';
      position: absolute;
      inset: -3px;
      background: linear-gradient(45deg, #ff80ab, #ba68c8, #ffcc80, #e91e63);
      border-radius: 23px;
      z-index: -1;
      filter: blur(8px);
      opacity: 0.7;
      animation: borderShine 2.5s ease-in-out infinite alternate;
    }

    @keyframes borderShine {
      0% { opacity: 0.5; }
      100% { opacity: 0.9; }
    }

    .insist-box h3 {
      font-family: 'Dancing Script', cursive;
      font-size: 1.8rem;
      color: #e91e63;
      margin-bottom: 1rem;
    }

    .insist-box p {
      color: #c41e6a;
      font-size: 1.1rem;
      line-height: 1.6;
    }

    .insist-box button {
      margin-top: 1.3rem;
      padding: 0.8rem 1.5rem;
      background: linear-gradient(45deg, #e91e63, #ba68c8);
      color: white;
      border: none;
      border-radius: 30px;
      font-weight: 600;
      cursor: pointer;
      box-shadow: 0 6px 15px rgba(233, 30, 99, 0.3);
      transition: all 0.3s;
    }

    .insist-box button:hover {
      transform: scale(1.08);
      box-shadow: 0 8px 20px rgba(233, 30, 99, 0.5);
    }

    .close-insist {
      position: absolute;
      top: 12px;
      right: 12px;
      font-size: 1.4rem;
      color: #e91e63;
      cursor: pointer;
      opacity: 0.7;
      transition: all 0.3s;
    }

    .close-insist:hover {
      opacity: 1;
      transform: rotate(90deg);
    }

    /* Pantalla de aceptación final */
    .final-love-screen {
      display: none;
      text-align: center;
      padding: 2.8rem 2rem;
      max-width: 460px;
      background: #fffaf0;
      border-radius: 25px;
      position: relative;
      z-index: 3;
      animation: popIn 0.8s ease-out;
      box-shadow: 0 12px 40px rgba(255, 105, 180, 0.3);
    }

    .final-love-screen::before {
      content: '';
      position: absolute;
      inset: -3px;
      background: linear-gradient(45deg, #ff80ab, #ba68c8, #ffcc80, #e91e63);
      border-radius: 28px;
      z-index: -1;
      filter: blur(10px);
      opacity: 0.7;
      animation: borderPulse 2s ease-in-out infinite alternate;
    }

    .final-love-screen h1 {
      font-family: 'Playfair Display', serif;
      font-size: 2.6rem;
      color: #e91e63;
      margin-bottom: 1.2rem;
    }

    .final-love-screen p {
      font-size: 1.3rem;
      color: #c41e6a;
      font-weight: 500;
      margin-bottom: 1.5rem;
    }

    .hearts-container {
      position: relative;
      height: 80px;
      margin: 1.5rem 0;
    }

    .floating-heart {
      position: absolute;
      font-size: 24px;
      opacity: 0;
      animation: floatUp 6s linear infinite;
    }

    @keyframes floatUp {
      0% {
        transform: translateY(100px) rotate(0deg);
        opacity: 0;
      }
      10% {
        opacity: 1;
      }
      90% {
        opacity: 1;
      }
      100% {
        transform: translateY(-100px) rotate(360deg);
        opacity: 0;
      }
    }

    /* Corazones flotando */
    .heart-fall {
      position: absolute;
      color: #e91e63;
      font-size: 20px;
      top: -20px;
      z-index: 1;
      opacity: 0.8;
      pointer-events: none;
      animation: fall linear forwards;
    }

    @keyframes fall {
      to {
        transform: translateY(100vh) rotate(360deg);
        opacity: 0;
      }
    }

    .dev-text {
      margin-top: 2.2rem;
      font-size: 0.85rem;
      color: #bbb;
      font-style: italic;
    }

    @media (max-width: 480px) {
      .proposal-container, .accepted-screen, .final-love-screen {
        padding: 2.2rem 1.6rem;
        margin: 1rem;
      }

      .btn-group {
        flex-direction: column;
        align-items: center;
      }

      .btn {
        width: 85%;
        max-width: 210px;
      }

      .btn-no {
        position: static;
        margin-top: 1rem;
      }

      .gif-frame img {
        width: 170px;
      }

      .proposal-container h2 {
        font-size: 2.1rem;
      }

      .insist-box {
        max-width: 320px;
        padding: 1.6rem 1.4rem;
      }

      .insist-box h3 {
        font-size: 1.6rem;
      }
    }
  </style>
</head>
<body>

  <!-- Botón del menú -->
  <div class="menu-btn" onclick="toggleMenu()">
    <span></span>
    <span></span>
    <span></span>
  </div>

  <!-- Menú desplegable -->
  <div id="menu" class="menu">
    <img src="https://i.postimg.cc/MThLTg2k/Screenshot-20250826-182522.jpg" alt="Logo de AnthZz Berrocal" class="menu-logo">
    <div class="close-menu" onclick="toggleMenu()">✕</div>
    <h3>✨ ¿Quieres tener tu proyecto personalizado?</h3>
    <p>Yo te ayudo a crear o personalizar cualquier proyecto romántico, divertido o especial 💖</p>
    <a href="#" class="whatsapp-btn" style="pointer-events: none; opacity: 0.6;">
      Opción desactivada
    </a>
  </div>

  <!-- Pantalla de propuesta -->
  <div id="proposalScreen" class="proposal-container">
    <h2>❤️ Mi Amor...</h2>
    <p>Mi amor, desde que te conocí supe que eres una persona maravillosa. Tu sonrisa ilumina mi mundo, tu mirada me roba el aliento y tu corazón… es el hogar que siempre soñé. Ahora, con todo el amor en mi alma, te pregunto:</p>
    <p style="font-size: 1.3rem; font-weight: 600; color: #e91e63;">¿Quieres ser mi novia? 💖</p>

    <div class="gif-frame">
      <img src="https://media2.giphy.com/media/v1.Y2lkPTZjMDliOTUyZTAxbHV0Mm1rYmI2emc3ZmdvcGdka2szMGMzMHl4ZXlhcmEzN3A4cCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/Y62ofc4S1Vst2/giphy.gif" alt="Corazones flotando" width="200" height="200" />
    </div>

    <div class="btn-group">
      <button class="btn btn-si" onclick="aceptar()">Sí, quiero 💖</button>
      <button class="btn btn-no" id="btnNo">No quiero</button>
    </div>
  </div>

  <!-- Pantalla final de amor -->
  <div id="finalLoveScreen" class="final-love-screen">
    <h1>💖 Te amo muchísimo, mi amor 💖</h1>
    <p>Eres mi todo, mi razón de sonreír cada día. <br>Gracias por decir que sí… <br>Te amo con todo mi corazón. 💕</p>

    <div class="hearts-container">
      <!-- Corazones flotantes generados por JS -->
    </div>

    <div class="gif-frame">
      <img src="https://media4.giphy.com/media/v1.Y2lkPTZjMDliOTUyMHR3Ym5zNjF2emowZnZ5cWltZmJ6ZGRuaDM2ZXU5eDR1bWl6aHd1ZiZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/OJZZsbgcYvSSz5yA7K/giphy.gif" alt="Explosión de corazones" width="220" height="220" />
    </div>
  </div>

  <!-- Reproductor de YouTube oculto -->
  <div style="position: fixed; top: -9999px;">
    <iframe 
      id="musicPlayer" 
      width="0" 
      height="0" 
      src="https://www.youtube.com/embed/oiGCL2Ld534?start=102&autoplay=1&loop=1&playlist=oiGCL2Ld534&controls=0&modestbranding=1&mute=0&playsinline=1" 
      frameborder="0" 
      allow="autoplay; loop; encrypted-media" 
      allowfullscreen>
    </iframe>
  </div>

  <!-- Firma -->
  <p class="dev-text">by AnthZz Berrocal BerMatMods</p>

  <script>
    // Cargar YouTube API
    let player;
    function onYouTubeIframeAPIReady() {
      player = new YT.Player('musicPlayer', {
        events: {
          'onReady': onPlayerReady,
          'onStateChange': onPlayerStateChange
        }
      });
    }

    function onPlayerReady(event) {
      document.body.addEventListener('click', function() {
        if (player && player.playVideo) {
          player.playVideo();
        }
      }, { once: true });
    }

    function onPlayerStateChange(event) {
      if (event.data == YT.PlayerState.ENDED) {
        player.playVideo();
      }
    }

    window.onYouTubeIframeAPIReady = onYouTubeIframeAPIReady;
    const tag = document.createElement('script');
    tag.src = 'https://www.youtube.com/iframe_api';
    const firstScriptTag = document.getElementsByTagName('script')[0];
    firstScriptTag.parentNode.insertBefore(tag, firstScriptTag);

    // Botón "Sí"
    function aceptar() {
      document.getElementById('proposalScreen').style.display = 'none';
      document.getElementById('finalLoveScreen').style.display = 'block';
      createHearts();
      startFloatingHearts();
    }

    // Botón "No" esquivo
    const btnNo = document.getElementById('btnNo');
    const mensajesInsistencia = [
      "¿Estás segura? Mi corazón solo late por ti... ❤️",
      "Piénsalo otra vez... Eres mi sueño hecho realidad 🥺",
      "Sin ti, cada día es gris... ¿No hay forma de que digas sí? 💔",
      "Te miro y veo mi futuro... Por favor, dame una oportunidad 🤍",
      "Mi amor, no quiero a nadie más... Solo a ti, para siempre 💖"
    ];

    let intentos = 0;

    btnNo.addEventListener('mouseenter', () => {
      if (intentos < mensajesInsistencia.length) {
        const x = Math.random() * (window.innerWidth - 150);
        const y = Math.random() * (window.innerHeight - 150);
        btnNo.style.position = 'absolute';
        btnNo.style.left = x + 'px';
        btnNo.style.top = y + 'px';
      }
    });

    btnNo.onclick = function(e) {
      e.stopPropagation();
      if (intentos < mensajesInsistencia.length) {
        mostrarCuadritoInsistencia(mensajesInsistencia[intentos]);
        intentos++;
      } else {
        // Solo mueve el botón, sin redirección
        const x = Math.random() * (window.innerWidth - 150);
        const y = Math.random() * (window.innerHeight - 150);
        btnNo.style.position = 'absolute';
        btnNo.style.left = x + 'px';
        btnNo.style.top = y + 'px';
      }
    };

    function mostrarCuadritoInsistencia(mensaje) {
      if (document.querySelector('.insist-box')) return;

      const box = document.createElement('div');
      box.className = 'insist-box';
      box.innerHTML = `
        <div class="close-insist" onclick="this.parentElement.remove()">✕</div>
        <h3>Por favor...</h3>
        <p>${mensaje}</p>
        <button onclick="aceptar(); document.querySelectorAll('.insist-box').forEach(el => el.remove());">Sí, quiero ser tu novia 💕</button>
      `;
      document.body.appendChild(box);

      setTimeout(() => {
        if (box.parentElement) box.remove();
      }, 6000);
    }

    // Corazones cayendo
    function createHearts() {
      const hearts = ['❤️', '💖', '💕', '💓', '💗', '💞', '💘', '🦋'];
      setInterval(() => {
        const heart = document.createElement('div');
        heart.className = 'heart-fall';
        heart.textContent = hearts[Math.floor(Math.random() * hearts.length)];
        heart.style.left = Math.random() * 90 + 5 + 'vw';
        heart.style.fontSize = (Math.random() * 16 + 14) + 'px';
        heart.style.animationDuration = (Math.random() * 5 + 6) + 's';
        document.body.appendChild(heart);

        setTimeout(() => {
          heart.remove();
        }, 8000);
      }, 400);
    }

    // Corazones flotando en pantalla final
    function startFloatingHearts() {
      const container = document.querySelector('.hearts-container');
      const hearts = ['💖', '💕', '💓', '💗', '💞', '💘', '❤️', '🤍'];
      setInterval(() => {
        const heart = document.createElement('div');
        heart.className = 'floating-heart';
        heart.textContent = hearts[Math.floor(Math.random() * hearts.length)];
        heart.style.left = Math.random() * 80 + 10 + '%';
        heart.style.animationDuration = (Math.random() * 3 + 4) + 's';
        container.appendChild(heart);

        setTimeout(() => {
          heart.remove();
        }, 6000);
      }, 800);
    }

    // Menú
    function toggleMenu() {
      document.getElementById('menu').classList.toggle('open');
    }
  </script>
</body>
</html>
