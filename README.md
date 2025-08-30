
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

    /* Botón del menú (3 rayitas) */
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

    /* Logo circular */
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

    /* Cerrar menú */
    .close-menu {
      position: absolute;
      top: 20px;
      right: 20px;
      font-size: 1.5rem;
      color: #e91e63;
      cursor: pointer;
    }

    /* Pantalla de propuesta */
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
    }

    .btn-no:hover {
      background: #ffe6f0;
      transform: scale(1.06);
    }

    /* Pantalla de aceptación (fondo blanco rosado sutil) */
    .accepted-screen {
      display: none;
      text-align: center;
      padding: 2.4rem;
      max-width: 440px;
      background: #fffaf0; /* Blanco con leve tono rosado */
      border-radius: 20px;
      box-shadow: 0 12px 35px rgba(255, 105, 180, 0.2);
      border: 3px solid transparent;
      position: relative;
      z-index: 2;
      animation: popIn 0.8s ease-out;
    }

    .accepted-screen::before {
      content: '';
      position: absolute;
      inset: -3px;
      background: linear-gradient(45deg, #ffb6c1, #ff80ab, #ffb6c1); /* Neón rosado muy suave */
      border-radius: 23px;
      z-index: -1;
      animation: borderPulse 3s ease-in-out infinite;
      opacity: 0.6;
    }

    @keyframes borderPulse {
      0%, 100% { opacity: 0.5; }
      50% { opacity: 0.8; }
    }

    @keyframes popIn {
      0% { transform: scale(0.8); opacity: 0; }
      100% { transform: scale(1); opacity: 1; }
    }

    .accepted-screen h1 {
      font-family: 'Playfair Display', serif;
      font-size: 2.5rem;
      color: #e91e63;
      margin-bottom: 1.1rem;
    }

    .accepted-screen p {
      color: #c41e6a; /* Rosa profundo, muy legible */
      font-size: 1.15rem;
      margin-bottom: 1.5rem;
      line-height: 1.6;
      font-weight: 500;
    }

    /* Marco animado para GIF */
    .gif-frame {
      border-radius: 18px;
      padding: 3px;
      margin: 1.5rem 0;
      background: linear-gradient(45deg, #ff80ab, #ba68c8, #ffcc80, #e91e63);
      background-size: 300% 300%;
      animation: rgbPulse 4s infinite alternate, backgroundShift 6s ease-in-out infinite;
      position: relative;
      display: inline-block;
    }

    .gif-frame img {
      border-radius: 15px;
      display: block;
      width: 200px;
      height: auto;
      border: 4px solid #fff;
      box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
    }

    @keyframes rgbPulse {
      0% { box-shadow: 0 0 20px rgba(255, 105, 180, 0.3); }
      33% { box-shadow: 0 0 20px rgba(140, 100, 255, 0.3); }
      66% { box-shadow: 0 0 20px rgba(255, 190, 100, 0.3); }
      100% { box-shadow: 0 0 20px rgba(255, 105, 180, 0.3); }
    }

    @keyframes backgroundShift {
      0%, 100% { background-position: 0% 50%; }
      50% { background-position: 100% 50%; }
    }

    /* Corazones flotando (lluvia desde arriba) */
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
      .proposal-container, .accepted-screen {
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

      .gif-frame img {
        width: 170px;
      }

      .proposal-container h2 {
        font-size: 2.1rem;
      }
    }
  </style>
</head>
<body>

  <!-- Botón del menú (3 rayitas) -->
  <div class="menu-btn" onclick="toggleMenu()">
    <span></span>
    <span></span>
    <span></span>
  </div>

  <!-- Menú desplegable -->
  <div id="menu" class="menu">
    <img src="https://i.postimg.cc/MThLTg2k/Screenshot-20250826-182522.jpg" alt="Logo de AnthZz Berrocal" class="menu-logo">
    <div class="close-menu" onclick="toggleMenu()">✕</div>
    <h3>✨ ¿Quieres tener tu proyecto personalizado o dedicar a una persona en especial?</h3>
    <p>Yo te ayudo a crear o personalizar cualquier proyecto romántico, divertido o especial 💖</p>
    <a href="https://wa.me/51937556459?text=Hola%20AnthZz%20Berrocal,%20vi%20uno%20de%20tus%20proyectos%20y%20me%20gustaría%20que%20me%20lo%20crees%20o%20personalices%20un%20proyecto." target="_blank" class="whatsapp-btn">
      💬 Contactar por WhatsApp
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
      <button class="btn btn-no" onclick="negar()">No quiero</button>
    </div>
  </div>

  <!-- Pantalla de aceptación -->
  <div id="acceptedScreen" class="accepted-screen">
    <h1>¡Sabía que dirías que sí! 💕</h1>
    <p>Sabía que me ibas  aceptar a que fueras mi novia… <br>Eres la persona más hermosa del mundo. <br>Te amo muchísimo y cada día será un regalo contigo. 💖</p>

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
      // Reproducir al hacer clic
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
      document.getElementById('acceptedScreen').style.display = 'block';
      createHearts();
    }

    // Botón "No" con insistencia
    function negar() {
      const mensajes = [
        "¿Estás segura? ❤️",
        "Piénsalo otra vez… 🥺",
        "Mi corazón solo late por ti… 😢",
        "¿No hay forma de que digas sí? 💔",
        "¡Por favor! Dime que sí… 🤍"
      ];
      
      if (!window.intentos) window.intentos = 0;

      if (window.intentos < mensajes.length) {
        alert(mensajes[window.intentos]);
        window.intentos++;
      } else {
        alert("Ya no pregunto más… pero mi corazón siempre será tuyo 💔");
      }
    }

    // Corazones cayendo (lluvia)
    function createHearts() {
      const hearts = ['❤️', '💖', '💕', '💓', '💗', '💞', '💘', '🦋']; // mariposita incluida 💖
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

    // Abrir/cerrar menú
    function toggleMenu() {
      document.getElementById('menu').classList.toggle('open');
    }
  </script>
</body>
</html>
