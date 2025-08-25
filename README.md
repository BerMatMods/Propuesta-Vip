
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Reloj Mundial América - by AnthZz Berrocal BerMatMods</title>
  <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@700&family=Share+Tech+Mono&display=swap" rel="stylesheet">
  <style>
    /* Fondo oscuro con efecto neón */
    body {
      margin: 0;
      padding: 0;
      background: #000;
      color: #0f0;
      font-family: 'Share Tech Mono', monospace;
      overflow: hidden;
      height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;
      background-image: 
        radial-gradient(circle at 10% 20%, rgba(0, 255, 255, 0.1), transparent 20%),
        radial-gradient(circle at 90% 80%, rgba(255, 0, 255, 0.1), transparent 20%);
      position: relative;
    }

    /* Patrón de fondo diagonal */
    body::before {
      content: '';
      position: absolute;
      top: 0; left: 0;
      width: 100%; height: 100%;
      background: repeating-linear-gradient(
        45deg,
        transparent,
        transparent 10px,
        rgba(0, 255, 255, 0.03) 10px,
        rgba(0, 255, 255, 0.03) 20px
      );
      z-index: 1;
      pointer-events: none;
      opacity: 0.3;
    }

    /* Partículas flotantes */
    .particles {
      position: absolute;
      top: 0; left: 0;
      width: 100%; height: 100%;
      z-index: 1;
      pointer-events: none;
    }

    .particle {
      position: absolute;
      width: 6px; height: 6px;
      background: #00ccff;
      border-radius: 50%;
      box-shadow: 0 0 10px #00ccff;
      opacity: 0.6;
      animation: float 6s infinite ease-in-out;
    }

    @keyframes float {
      0%, 100% { transform: translateY(0) translateX(0); opacity: 0.6; }
      50% { transform: translateY(-100px) translateX(50px); opacity: 1; }
    }

    /* Contenedor principal */
    .container {
      text-align: center;
      z-index: 2;
      padding: 20px;
      max-width: 900px;
      width: 90%;
    }

    /* Título con glitch */
    .title {
      font-family: 'Orbitron', sans-serif;
      font-size: 2.5em;
      color: #00ccff;
      text-shadow: 
        0 0 5px #00ccff,
        0 0 10px #00ccff,
        0 0 20px #00ccff;
      margin-bottom: 10px;
      letter-spacing: 2px;
    }

    .subtitle {
      font-size: 1.1em;
      color: #aaa;
      margin-bottom: 30px;
    }

    /* Reloj principal */
    .clock {
      font-family: 'Orbitron', sans-serif;
      font-size: 5em;
      color: #00ff00;
      text-shadow: 
        0 0 5px #00ff00,
        0 0 10px #00ff00,
        0 0 20px #00ff00,
        0 0 40px #00ff00;
      margin: 20px 0;
      letter-spacing: 3px;
      animation: pulse 2s infinite;
    }

    @keyframes pulse {
      0%, 100% { opacity: 1; }
      50% { opacity: 0.7; }
    }

    /* Fecha */
    .date {
      font-family: 'Share Tech Mono', monospace;
      font-size: 1.4em;
      color: #00ccff;
      margin-bottom: 20px;
      text-shadow: 0 0 10px rgba(0, 204, 255, 0.5);
    }

    /* Zona horaria actual */
    .timezone {
      font-size: 1.3em;
      color: #ff55ff;
      margin-bottom: 30px;
      font-weight: bold;
      text-shadow: 0 0 10px rgba(255, 85, 255, 0.5);
    }

    /* Botón RGB animado */
    .btn {
      padding: 15px 30px;
      background: linear-gradient(45deg, #ff0000, #ff7700, #ffff00, #00ff00, #00ffff, #0000ff, #8000ff);
      background-size: 400% 400%;
      color: white;
      font-family: 'Orbitron', sans-serif;
      font-weight: bold;
      font-size: 1.2em;
      border: none;
      border-radius: 50px;
      cursor: pointer;
      box-shadow: 0 0 20px rgba(255, 255, 255, 0.3);
      transition: all 0.3s;
      position: relative;
      overflow: hidden;
      letter-spacing: 1px;
      margin: 20px 0;
    }

    .btn::before {
      content: '';
      position: absolute;
      top: 0; left: -100%;
      width: 100%; height: 100%;
      background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.3), transparent);
      animation: shine 3s infinite;
    }

    @keyframes shine {
      0% { left: -100%; }
      50% { left: 100%; }
      100% { left: -100%; }
    }

    .btn:hover {
      transform: scale(1.05);
      box-shadow: 0 0 30px rgba(255, 255, 255, 0.6);
    }

    @keyframes rainbow {
      0% { filter: hue-rotate(0deg); }
      100% { filter: hue-rotate(360deg); }
    }

    .btn {
      animation: rainbow 8s linear infinite;
    }

    /* Lista de horarios */
    .time-list {
      display: none;
      margin-top: 30px;
      text-align: left;
      background: rgba(0, 0, 0, 0.7);
      border: 1px solid #00ccff;
      border-radius: 15px;
      padding: 20px;
      max-height: 300px;
      overflow-y: auto;
      box-shadow: 0 0 25px rgba(0, 204, 255, 0.3);
    }

    .time-item {
      font-family: 'Orbitron', sans-serif;
      font-size: 1.2em;
      padding: 10px;
      margin: 10px 0;
      background: rgba(0, 204, 255, 0.1);
      border-radius: 8px;
      border-left: 4px solid #00ccff;
      transition: transform 0.3s;
    }

    .time-item:hover {
      transform: translateX(10px);
      background: rgba(0, 204, 255, 0.2);
    }

    .time-item span.city {
      color: #ff55ff;
      font-weight: bold;
    }

    .time-item span.time {
      color: #00ff00;
    }

    /* Footer */
    .footer {
      margin-top: 40px;
      font-size: 0.9em;
      color: #555;
      font-family: 'Orbitron', sans-serif;
    }

    .footer strong {
      color: #00ccff;
    }

    /* Glitch effect en título */
    .glitch {
      position: relative;
    }

    .glitch::before, .glitch::after {
      content: attr(data-text);
      position: absolute;
      top: 0;
      width: 100%;
      background: black;
      clip: rect(0, 0, 0, 0);
    }

    .glitch::before {
      left: 2px;
      text-shadow: -1px 0 #ff00ff;
      animation: glitch-anim 2s infinite linear alternate-reverse;
    }

    .glitch::after {
      left: -2px;
      text-shadow: 1px 0 #00ffff;
      animation: glitch-anim 3s infinite linear alternate-reverse;
    }

    @keyframes glitch-anim {
      0% { clip: rect(44px, 999px, 11px, 0); }
      20% { clip: rect(2px, 999px, 88px, 0); }
      40% { clip: rect(88px, 999px, 33px, 0); }
      60% { clip: rect(22px, 999px, 77px, 0); }
      80% { clip: rect(66px, 999px, 11px, 0); }
      100% { clip: rect(55px, 999px, 22px, 0); }
    }

    /* Responsive para móviles */
    @media (max-width: 768px) {
      .clock {
        font-size: 3.5em;
      }
      .title {
        font-size: 2em;
      }
      .date {
        font-size: 1.2em;
      }
    }
  </style>
</head>
<body>

  <div class="particles" id="particles"></div>

  <div class="container">
    <h1 class="title glitch" data-text="Reloj Mundial América">Reloj Mundial América</h1>
    <p class="subtitle">Zonas Horarias de América en tiempo real</p>

    <div class="clock" id="peru-clock">00:00:00</div>
    <div class="date" id="peru-date">Lunes, 01 de Enero de 2025</div>
    <div class="timezone">🇵🇪 Hora de Perú (Lima)</div>

    <button class="btn" onclick="toggleTimes()">Ver Horas de América</button>

    <div class="time-list" id="time-list">
      <div class="time-item"><span class="city">🇵🇪 Lima (Perú):</span> <span id="lima" class="time">--:--:--</span></div>
      <div class="time-item"><span class="city">🇺🇸 Nueva York (EE.UU.):</span> <span id="ny" class="time">--:--:--</span></div>
      <div class="time-item"><span class="city">🇲🇽 Ciudad de México:</span> <span id="mexico" class="time">--:--:--</span></div>
      <div class="time-item"><span class="city">🇨🇱 Santiago (Chile):</span> <span id="santiago" class="time">--:--:--</span></div>
      <div class="time-item"><span class="city">🇦🇷 Buenos Aires (Argentina):</span> <span id="buenos" class="time">--:--:--</span></div>
      <div class="time-item"><span class="city">🇧🇷 São Paulo (Brasil):</span> <span id="sao" class="time">--:--:--</span></div>
      <div class="time-item"><span class="city">🇨🇴 Bogotá (Colombia):</span> <span id="bogota" class="time">--:--:--</span></div>
      <div class="time-item"><span class="city">🇻🇪 Caracas (Venezuela):</span> <span id="caracas" class="time">--:--:--</span></div>
    </div>

    <div class="footer">
      by <strong>AnthZz Berrocal BerMatMods</strong> | © 2025 | Reloj Mundial Animado
    </div>
  </div>

  <script>
    // Crear partículas
    function createParticles() {
      const container = document.getElementById('particles');
      for (let i = 0; i < 20; i++) {
        const p = document.createElement('div');
        p.classList.add('particle');
        p.style.top = `${Math.random() * 100}%`;
        p.style.left = `${Math.random() * 100}%`;
        p.style.animationDelay = `${Math.random() * 5}s`;
        p.style.opacity = Math.random() * 0.8 + 0.4;
        container.appendChild(p);
      }
    }

    // Formato de hora
    function formatTime(date) {
      return date.toLocaleTimeString('es-PE', {
        hour12: false,
        hour: '2-digit',
        minute: '2-digit',
        second: '2-digit'
      });
    }

    // Formato de fecha
    function formatDate(date) {
      return date.toLocaleDateString('es-PE', {
        weekday: 'long',
        year: 'numeric',
        month: 'long',
        day: 'numeric'
      });
    }

    // Actualizar reloj principal (Perú)
    function updatePeruClock() {
      const now = new Date();
      document.getElementById('peru-clock').textContent = formatTime(now);
      document.getElementById('peru-date').textContent = formatDate(now);
    }

    // Actualizar todas las zonas horarias
    function updateAllTimes() {
      const zones = {
        lima: 'America/Lima',
        ny: 'America/New_York',
        mexico: 'America/Mexico_City',
        santiago: 'America/Santiago',
        buenos: 'America/Argentina/Buenos_Aires',
        sao: 'America/Sao_Paulo',
        bogota: 'America/Bogota',
        caracas: 'America/Caracas'
      };

      for (const [id, zone] of Object.entries(zones)) {
        try {
          const date = new Date().toLocaleString('es-PE', { timeZone: zone });
          const time = formatTime(new Date(date));
          document.getElementById(id).textContent = time;
        } catch {
          document.getElementById(id).textContent = "Error";
        }
      }
    }

    // Mostrar/ocultar lista
    function toggleTimes() {
      const list = document.getElementById('time-list');
      if (list.style.display === 'block') {
        list.style.display = 'none';
      } else {
        updateAllTimes(); // Actualiza al abrir
        list.style.display = 'block';
      }
    }

    // Iniciar
    window.onload = () => {
      createParticles();
      updatePeruClock();
      setInterval(updatePeruClock, 1000);
      setInterval(updateAllTimes, 1000);
    };
  </script>

</body>
</html>
