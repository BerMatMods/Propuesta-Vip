
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>BerMatVPN - BerMatMods</title>
  <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@500;700&family=Roboto:wght@400;700&display=swap" rel="stylesheet">
  <style>
    /* Fondo del móvil */
    body {
      margin: 0;
      background-image: url('https://i.imgur.com/3QJkLqB.jpg');
      background-size: cover;
      background-position: center;
      font-family: 'Roboto', sans-serif;
      color: white;
      overflow: hidden;
      height: 100vh;
      position: relative;
      background-attachment: fixed;
    }

    /* Barra superior (simulada) */
    .status-bar {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 40px;
      background: rgba(0, 0, 0, 0.8);
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 0 10px;
      color: white;
      font-size: 14px;
      z-index: 10;
    }

    .time {
      font-weight: bold;
      font-family: 'Orbitron', sans-serif;
    }

    .battery {
      font-size: 12px;
      margin-left: 5px;
    }

    /* Header principal */
    .header {
      position: absolute;
      top: 50px;
      left: 0;
      right: 0;
      text-align: center;
      z-index: 5;
      padding: 0 20px;
    }

    .mobile-ip {
      font-size: 18px;
      color: #fff;
      text-shadow: 0 0 5px rgba(0, 0, 0, 0.7);
      margin-bottom: 10px;
    }

    .whatsapp-container {
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 10px;
      margin-top: 10px;
    }

    .whatsapp-icon {
      width: 60px;
      height: 60px;
      background: #25D366;
      border-radius: 50%;
      display: flex;
      justify-content: center;
      align-items: center;
      color: white;
      font-size: 24px;
      box-shadow: 0 0 15px rgba(37, 211, 99, 0.5);
    }

    .whatsapp-text {
      font-size: 24px;
      font-weight: bold;
      color: #ff0000;
      text-shadow: 0 0 5px rgba(0, 0, 0, 0.7);
    }

    .connected {
      font-size: 20px;
      color: #00ff00;
      text-shadow: 0 0 5px #00ff00;
      margin-top: 10px;
      text-align: center;
      font-weight: bold;
      animation: pulse 2s infinite;
    }

    /* Servicios */
    .services {
      display: flex;
      flex-direction: column;
      gap: 15px;
      margin-top: 30px;
      padding: 0 20px;
      z-index: 5;
    }

    .service {
      display: flex;
      align-items: center;
      gap: 10px;
      background: rgba(0, 0, 0, 0.6);
      padding: 10px;
      border-radius: 10px;
      box-shadow: 0 0 10px rgba(0, 0, 0, 0.3);
      transition: transform 0.3s;
    }

    .service:hover {
      transform: scale(1.05);
    }

    .service-icon {
      width: 40px;
      height: 40px;
      border-radius: 8px;
      background: #000;
      display: flex;
      justify-content: center;
      align-items: center;
    }

    .service-name {
      font-weight: bold;
      color: #fff;
      font-family: 'Orbitron', sans-serif;
    }

    /* Credenciales */
    .credentials {
      display: flex;
      gap: 10px;
      margin-top: 15px;
      padding: 0 20px;
      z-index: 5;
    }

    .cred-item {
      flex: 1;
      background: rgba(0, 0, 0, 0.7);
      padding: 10px;
      border-radius: 10px;
      display: flex;
      align-items: center;
      gap: 10px;
      box-shadow: 0 0 10px rgba(0, 0, 0, 0.3);
      transition: transform 0.3s;
    }

    .cred-item:hover {
      transform: scale(1.05);
    }

    .cred-icon {
      width: 20px;
      height: 20px;
    }

    .cred-value {
      font-weight: bold;
      color: #fff;
      font-family: 'Orbitron', sans-serif;
    }

    /* Botones principales */
    .main-buttons {
      display: flex;
      gap: 10px;
      margin-top: 15px;
      padding: 0 20px;
      z-index: 5;
    }

    .btn-primary {
      flex: 1;
      padding: 15px;
      background: linear-gradient(135deg, #5a3eff, #3c1dff);
      color: white;
      border: none;
      border-radius: 10px;
      font-size: 18px;
      font-weight: bold;
      cursor: pointer;
      box-shadow: 0 0 15px rgba(90, 58, 255, 0.5);
      transition: all 0.3s;
    }

    .btn-primary:hover {
      transform: scale(1.05);
      box-shadow: 0 0 20px rgba(90, 58, 255, 0.7);
    }

    .btn-refresh {
      width: 60px;
      height: 60px;
      background: linear-gradient(135deg, #5a3eff, #3c1dff);
      color: white;
      border: none;
      border-radius: 50%;
      font-size: 20px;
      cursor: pointer;
      box-shadow: 0 0 15px rgba(90, 58, 255, 0.5);
      transition: all 0.3s;
    }

    .btn-refresh:hover {
      transform: scale(1.1);
      box-shadow: 0 0 20px rgba(90, 58, 255, 0.7);
    }

    /* Botones inferiores */
    .bottom-buttons {
      display: flex;
      justify-content: center;
      gap: 20px;
      margin-top: 20px;
      padding: 0 20px;
      z-index: 5;
    }

    .bottom-btn {
      width: 60px;
      height: 60px;
      background: rgba(0, 0, 0, 0.7);
      border-radius: 50%;
      display: flex;
      justify-content: center;
      align-items: center;
      cursor: pointer;
      transition: all 0.3s;
      box-shadow: 0 0 10px rgba(0, 0, 0, 0.5);
    }

    .bottom-btn:hover {
      transform: scale(1.1);
      box-shadow: 0 0 15px rgba(0, 0, 0, 0.8);
    }

    .bottom-label {
      font-size: 12px;
      margin-top: 5px;
      text-align: center;
      color: #aaa;
    }

    /* Log */
    .log {
      margin-top: 20px;
      padding: 15px;
      background: rgba(0, 0, 0, 0.8);
      border-radius: 10px;
      max-height: 200px;
      overflow-y: auto;
      font-family: 'Consolas', monospace;
      color: #0f0;
      text-shadow: 0 0 2px #0f0;
      z-index: 5;
      box-shadow: 0 0 15px rgba(0, 255, 0, 0.3);
    }

    /* Footer */
    .footer {
      position: absolute;
      bottom: 20px;
      left: 0;
      right: 0;
      text-align: center;
      color: #aaa;
      font-size: 10px;
      z-index: 5;
      font-family: 'Orbitron', sans-serif;
    }

    /* Animaciones */
    @keyframes pulse {
      0%, 100% { opacity: 1; }
      50% { opacity: 0.7; }
    }

    .pulse {
      animation: pulse 2s infinite;
    }

    @keyframes float {
      0%, 100% { transform: translateY(0); }
      50% { transform: translateY(-10px); }
    }

    .float {
      animation: float 3s ease-in-out infinite;
    }

    /* Efecto de brillo en texto */
    .glow {
      text-shadow: 0 0 5px rgba(0, 255, 0, 0.8);
    }
  </style>
</head>
<body>

  <!-- Barra de estado -->
  <div class="status-bar">
    <span class="time">7:42 p.m.</span>
    <span class="battery">[96]</span>
  </div>

  <!-- Header -->
  <div class="header">
    <div class="mobile-ip">MOBILE: 100.105.208.200</div>
    <div class="whatsapp-container">
      <div class="whatsapp-icon">💬</div>
      <div class="whatsapp-text">BerMatMods<br><span style="font-size: 32px;">937556459</span></div>
    </div>
    <div class="connected">CONECTADO</div>
  </div>

  <!-- Servicios -->
  <div class="services">
    <div class="service">
      <div class="service-icon" style="background: #000; color: #00ccff;">
        🌐
      </div>
      <div class="service-name">BERMATMODS VPS</div>
    </div>
    <div class="service">
      <div class="service-icon" style="background: #000; color: #00ccff;">
        e
      </div>
      <div class="service-name">ENTEL SIN REDES 5GB-1GB</div>
    </div>
  </div>

  <!-- Credenciales -->
  <div class="credentials">
    <div class="cred-item">
      <div class="cred-icon">👤</div>
      <div class="cred-value">BerMatMods</div>
    </div>
    <div class="cred-item">
      <div class="cred-icon">🔒</div>
      <div class="cred-value">peru2</div>
    </div>
  </div>

  <!-- Botones principales -->
  <div class="main-buttons">
    <button class="btn-primary">DESCONECTAR</button>
    <button class="btn-refresh">🔄</button>
  </div>

  <!-- Botones inferiores -->
  <div class="bottom-buttons">
    <div class="bottom-btn">🔄<div class="bottom-label">ATUALIZAR</div></div>
    <div class="bottom-btn">💬<div class="bottom-label">WHATSAPP</div></div>
    <div class="bottom-btn">📱<div class="bottom-label">APN</div></div>
    <div class="bottom-btn">📶<div class="bottom-label">ROTEADOR</div></div>
    <div class="bottom-btn">⚙️<div class="bottom-label">CONFIGURAÇÃO</div></div>
  </div>

  <!-- Log -->
  <div class="log" id="log">
    [7:42 p.m.] Routes Excluded: 10.0.0.0/8, 104.18.1.9/32, 169.254.1.0/24, 192.168.42.0/23, 192.168.44.0/24, 192.168.49.0/24<br>
    [7:42 p.m.] INTERNET ESTABELECIDA<br>
    [7:42 p.m.] INTERNET CONECTADA
  </div>

  <!-- Footer -->
  <div class="footer">
    by AnthZz Berrocal BerMatMods | © 2025
  </div>

  <script>
    // Simular conexión
    const log = document.getElementById('log');
    let connected = true;

    // Botón desconectar
    document.querySelector('.btn-primary').addEventListener('click', () => {
      if (connected) {
        log.innerHTML += '<br>[7:43 p.m.] DESCONECTANDO...';
        setTimeout(() => {
          log.innerHTML += '<br>[7:43 p.m.] DESCONECTADO';
          document.querySelector('.btn-primary').textContent = 'CONECTAR';
        }, 1000);
        connected = false;
      } else {
        log.innerHTML += '<br>[7:43 p.m.] CONECTANDO...';
        setTimeout(() => {
          log.innerHTML += '<br>[7:43 p.m.] CONECTADO';
          document.querySelector('.btn-primary').textContent = 'DESCONECTAR';
        }, 1000);
        connected = true;
      }
    });

    // Refrescar
    document.querySelector('.btn-refresh').addEventListener('click', () => {
      log.innerHTML += '<br>[7:43 p.m.] RECARGANDO CONFIGURACIÓN...';
      setTimeout(() => {
        log.innerHTML += '<br>[7:43 p.m.] CONFIGURACIÓN ACTUALIZADA';
      }, 1000);
    });

    // Botones inferiores
    document.querySelectorAll('.bottom-btn').forEach(btn => {
      btn.addEventListener('click', () => {
        const label = btn.querySelector('.bottom-label').textContent;
        log.innerHTML += `<br>[7:43 p.m.] ${label} activado`;
      });
    });
  </script>

</body>
</html>
