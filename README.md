
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>CyberNet - By AnthZz Berrocal</title>
  <link href="https://fonts.googleapis.com/css2?family=Roboto+Mono:wght@400;500;700&family=Helvetica+Neue:wght@400;500;700&display=swap" rel="stylesheet">
  <style>
    /* ==========================================
       CYBERNET - By AnthZz Berrocal
       Red Social Educativa | Tecnología & Hacking Ético
       Todo en uno: HTML, CSS, JS
       ========================================== */

    :root {
      --bg-light: #f0f2f5;
      --bg-dark: #121212;
      --card-light: #ffffff;
      --card-dark: #1e1e1e;
      --text-light: #000000;
      --text-dark: #e0e0e0;
      --primary: #1877f2;
      --primary-dark: #1a69fe;
      --accent: #00ff88; /* Verde hacker */
      --gray: #65676b;
      --border-light: #dddfe2;
      --border-dark: #333333;
      --hover-light: #f2f2f2;
      --hover-dark: #2d2d2d;
    }

    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      font-family: 'Helvetica Neue', Arial, sans-serif;
      background: var(--bg-light);
      color: var(--text-light);
      transition: background 0.4s, color 0.4s;
      min-height: 100vh;
    }

    body.dark-mode {
      background: var(--bg-dark);
      color: var(--text-dark);
    }

    body.dark-mode .sidebar, 
    body.dark-mode .post, 
    body.dark-mode .modal-content,
    body.dark-mode .settings-panel {
      background: var(--card-dark);
      color: var(--text-dark);
    }

    body.dark-mode .post, 
    body.dark-mode .create-post,
    body.dark-mode .tabs,
    body.dark-mode .tab-content {
      border: 1px solid var(--border-dark);
    }

    body.dark-mode .stat-label,
    body.dark-mode .post-footer,
    body.dark-mode label {
      color: #aaa;
    }

    .container {
      display: flex;
      max-width: 1200px;
      margin: 0 auto;
      padding: 10px;
      gap: 16px;
      min-height: 100vh;
    }

    /* ==========================================
       HEADER
       ========================================== */
    header {
      position: sticky;
      top: 0;
      z-index: 100;
      background: var(--card-light);
      box-shadow: 0 1px 3px rgba(0,0,0,0.1);
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 10px 16px;
      border-bottom: 1px solid var(--border-light);
    }

    body.dark-mode header {
      background: var(--card-dark);
      border-bottom: 1px solid var(--border-dark);
    }

    .logo {
      font-weight: bold;
      font-size: 24px;
      color: var(--primary);
      text-decoration: none;
    }

    .logo span {
      color: var(--accent);
    }

    .search-box input {
      width: 300px;
      padding: 10px 14px;
      border: 1px solid var(--border-light);
      background: var(--bg-light);
      border-radius: 20px;
      outline: none;
      font-size: 14px;
    }

    body.dark-mode .search-box input {
      background: #2d2d2d;
      border-color: var(--border-dark);
      color: var(--text-dark);
    }

    .user-nav {
      display: flex;
      gap: 16px;
      align-items: center;
    }

    .icon {
      font-size: 20px;
      cursor: pointer;
      color: var(--gray);
    }

    body.dark-mode .icon {
      color: #bbb;
    }

    .avatar {
      width: 36px;
      height: 36px;
      border-radius: 50%;
      object-fit: cover;
      cursor: pointer;
    }

    /* ==========================================
       SIDEBAR
       ========================================== */
    .sidebar {
      width: 260px;
      background: var(--card-light);
      border-radius: 10px;
      padding: 16px 0;
      box-shadow: 0 1px 3px rgba(0,0,0,0.1);
      position: sticky;
      top: 60px;
      height: calc(100vh - 70px);
      border: 1px solid var(--border-light);
    }

    body.dark-mode .sidebar {
      border-color: var(--border-dark);
    }

    .sidebar nav a {
      display: flex;
      align-items: center;
      gap: 12px;
      padding: 12px 16px;
      text-decoration: none;
      color: var(--gray);
      font-size: 15px;
      border-radius: 8px;
      margin: 4px 8px;
      transition: all 0.2s;
    }

    .sidebar nav a:hover {
      background: var(--hover-light);
      color: var(--primary);
    }

    body.dark-mode .sidebar nav a:hover {
      background: var(--hover-dark);
      color: var(--primary);
    }

    .sidebar nav a.active {
      background: rgba(24, 119, 242, 0.1);
      color: var(--primary);
      font-weight: 500;
    }

    .sidebar nav a i {
      font-size: 18px;
      min-width: 24px;
      text-align: center;
    }

    /* ==========================================
       MAIN CONTENT
       ========================================== */
    main {
      flex: 1;
      display: none;
    }

    main.active {
      display: block;
    }

    /* ==========================================
       CREATE POST
       ========================================== */
    .create-post {
      background: var(--card-light);
      border: 1px solid var(--border-light);
      border-radius: 8px;
      padding: 12px;
      margin-bottom: 16px;
    }

    body.dark-mode .create-post {
      border-color: var(--border-dark);
    }

    .create-post .post-creator {
      display: flex;
      align-items: center;
      gap: 10px;
      margin-bottom: 10px;
    }

    .create-post input {
      flex: 1;
      padding: 10px;
      border: 1px solid var(--border-light);
      border-radius: 20px;
      outline: none;
      font-size: 15px;
    }

    body.dark-mode .create-post input {
      background: #2d2d2d;
      border-color: var(--border-dark);
      color: var(--text-dark);
    }

    .post-actions {
      display: flex;
      justify-content: space-around;
      margin-top: 8px;
      font-size: 14px;
    }

    .post-actions button {
      display: flex;
      align-items: center;
      gap: 6px;
      background: none;
      border: none;
      padding: 8px 12px;
      color: var(--gray);
      cursor: pointer;
      border-radius: 6px;
      flex: 1;
      justify-content: center;
    }

    .post-actions button:hover {
      background: var(--hover-light);
    }

    body.dark-mode .post-actions button:hover {
      background: var(--hover-dark);
    }

    /* ==========================================
       POST
       ========================================== */
    .post {
      background: var(--card-light);
      border: 1px solid var(--border-light);
      border-radius: 8px;
      overflow: hidden;
      margin-bottom: 16px;
    }

    body.dark-mode .post {
      border-color: var(--border-dark);
    }

    .post-header {
      display: flex;
      align-items: center;
      gap: 10px;
      padding: 12px;
    }

    .post-info strong {
      color: var(--text-light);
    }

    body.dark-mode .post-info strong {
      color: var(--text-dark);
    }

    .post-info span {
      font-size: 13px;
      color: var(--gray);
    }

    .post-content {
      padding: 0 12px 12px;
    }

    .post-content p {
      margin-bottom: 8px;
      color: var(--text-light);
    }

    body.dark-mode .post-content p {
      color: var(--text-dark);
    }

    .post-image {
      width: 100%;
      border-radius: 8px;
      margin-top: 8px;
    }

    .post-footer {
      padding: 8px 12px;
      font-size: 13px;
      color: var(--gray);
    }

    .post-interactions {
      display: flex;
      justify-content: space-around;
      padding: 10px 0;
      border-top: 1px solid var(--border-light);
    }

    body.dark-mode .post-interactions {
      border-top: 1px solid var(--border-dark);
    }

    .post-interactions button {
      display: flex;
      align-items: center;
      gap: 6px;
      background: none;
      border: none;
      padding: 8px 12px;
      color: var(--gray);
      cursor: pointer;
      border-radius: 6px;
      flex: 1;
      justify-content: center;
    }

    .post-interactions button.liked {
      color: var(--primary);
    }

    .post-interactions button:hover {
      background: var(--hover-light);
    }

    body.dark-mode .post-interactions button:hover {
      background: var(--hover-dark);
    }

    /* ==========================================
       PROFILE HEADER
       ========================================== */
    .profile-header {
      background: var(--card-light);
      border: 1px solid var(--border-light);
      border-radius: 8px;
      overflow: hidden;
      margin-bottom: 16px;
    }

    body.dark-mode .profile-header {
      border-color: var(--border-dark);
    }

    .cover-photo {
      height: 200px;
      background: url('https://via.placeholder.com/800x200/0d1b2a/ffffff?text=Cyber+Security') no-repeat center;
      background-size: cover;
      position: relative;
      cursor: pointer;
    }

    .cover-photo:hover::after {
      content: "Cambiar portada";
      position: absolute;
      bottom: 10px;
      left: 20px;
      background: rgba(0,0,0,0.6);
      color: white;
      padding: 6px 12px;
      border-radius: 4px;
      font-size: 14px;
    }

    .profile-info {
      padding: 60px 20px 20px;
      text-align: center;
      position: relative;
    }

    .profile-pic-container {
      position: relative;
      display: inline-block;
      margin-top: -80px;
    }

    .profile-pic {
      width: 140px;
      height: 140px;
      border-radius: 50%;
      border: 5px solid var(--card-light);
      object-fit: cover;
      cursor: pointer;
      box-shadow: 0 2px 10px rgba(0,0,0,0.2);
    }

    body.dark-mode .profile-pic {
      border-color: var(--card-dark);
    }

    .profile-pic:hover::after {
      content: "Editar foto";
      position: absolute;
      bottom: 0;
      left: 0;
      width: 100%;
      background: rgba(0,0,0,0.6);
      color: white;
      padding: 8px 0;
      border-radius: 0 0 50% 50%;
      font-size: 14px;
    }

    .profile-name {
      font-size: 28px;
      font-weight: bold;
      margin: 12px 0 6px;
    }

    .profile-bio {
      color: var(--gray);
      font-size: 16px;
      margin-bottom: 16px;
    }

    .stats {
      display: flex;
      justify-content: center;
      gap: 30px;
      margin: 20px 0;
      padding: 12px 0;
      border-top: 1px solid var(--border-light);
    }

    body.dark-mode .stats {
      border-top: 1px solid var(--border-dark);
    }

    .stat-item {
      text-align: center;
      cursor: pointer;
    }

    .stat-number {
      font-size: 20px;
      font-weight: bold;
      color: var(--primary);
    }

    body.dark-mode .stat-number {
      color: var(--accent);
    }

    .stat-label {
      font-size: 14px;
      color: var(--gray);
    }

    /* ==========================================
       TABS
       ========================================== */
    .tabs {
      background: var(--card-light);
      border-bottom: 1px solid var(--border-light);
      display: flex;
      border-radius: 8px 8px 0 0;
      overflow: hidden;
    }

    body.dark-mode .tabs {
      border-color: var(--border-dark);
    }

    .tab {
      flex: 1;
      text-align: center;
      padding: 14px;
      font-weight: 500;
      color: var(--gray);
      cursor: pointer;
    }

    .tab.active {
      color: var(--primary);
      border-bottom: 3px solid var(--primary);
    }

    body.dark-mode .tab.active {
      color: var(--accent);
      border-bottom: 3px solid var(--accent);
    }

    .tab-content {
      background: var(--card-light);
      border: 1px solid var(--border-light);
      border-top: none;
      border-radius: 0 0 8px 8px;
      padding: 20px;
      min-height: 200px;
    }

    body.dark-mode .tab-content {
      border-color: var(--border-dark);
    }

    /* ==========================================
       SETTINGS
       ========================================== */
    .settings-panel {
      padding: 20px;
    }

    .settings-panel h3 {
      margin-bottom: 16px;
      color: var(--primary);
    }

    body.dark-mode .settings-panel h3 {
      color: var(--accent);
    }

    .setting-item {
      margin-bottom: 16px;
    }

    .setting-item label {
      display: block;
      margin-bottom: 6px;
      color: var(--gray);
    }

    .setting-item input, 
    .setting-item textarea, 
    .setting-item select {
      width: 100%;
      padding: 10px;
      border: 1px solid var(--border-light);
      border-radius: 6px;
      background: var(--bg-light);
      color: var(--text-light);
      font-size: 15px;
    }

    body.dark-mode .setting-item input,
    body.dark-mode .setting-item textarea,
    body.dark-mode .setting-item select {
      background: #2d2d2d;
      border-color: var(--border-dark);
      color: var(--text-dark);
    }

    .btn {
      padding: 12px 20px;
      border: none;
      border-radius: 6px;
      cursor: pointer;
      font-size: 15px;
      margin-top: 10px;
    }

    .btn-primary {
      background: var(--primary);
      color: white;
    }

    .btn-dark {
      background: #111;
      color: var(--accent);
    }

    /* ==========================================
       MODAL
       ========================================== */
    .modal {
      display: none;
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: rgba(0,0,0,0.6);
      z-index: 1000;
      justify-content: center;
      align-items: center;
    }

    .modal-content {
      background: var(--card-light);
      border-radius: 10px;
      width: 90%;
      max-width: 500px;
      padding: 20px;
      box-shadow: 0 4px 30px rgba(0,0,0,0.3);
    }

    .modal-header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 16px;
    }

    .modal-title {
      font-size: 18px;
      font-weight: bold;
    }

    .close-btn {
      background: none;
      border: none;
      font-size: 24px;
      cursor: pointer;
      color: var(--gray);
    }

    /* ==========================================
       FOOTER
       ========================================== */
    .app-footer {
      grid-column: 1 / -1;
      text-align: center;
      padding: 20px;
      color: var(--gray);
      font-size: 13px;
      border-top: 1px solid var(--border-light);
      margin-top: 20px;
    }

    body.dark-mode .app-footer {
      border-color: var(--border-dark);
    }

    /* ==========================================
       RESPONSIVE
       ========================================== */
    @media (max-width: 768px) {
      .container {
        flex-direction: column;
      }

      .sidebar {
        width: 100%;
        position: static;
        height: auto;
        margin-bottom: 16px;
      }

      .search-box input {
        width: 100%;
      }

      .post-actions, .post-interactions {
        font-size: 13px;
      }
    }
  </style>
</head>
<body class="light-mode">

  <!-- HEADER -->
  <header>
    <div class="logo">Cyber<span>Net</span></div>
    <div class="search-box">
      <input type="text" placeholder="Buscar en CyberNet...">
    </div>
    <div class="user-nav">
      <span class="icon">🔔</span>
      <span class="icon">💬</span>
      <img src="https://via.placeholder.com/36" alt="Tu foto" class="avatar" id="user-avatar">
    </div>
  </header>

  <div class="container">

    <!-- SIDEBAR -->
    <aside class="sidebar">
      <nav>
        <a href="#home" class="active" onclick="showSection('home')"><i>🏠</i> Inicio</a>
        <a href="#profile" onclick="showSection('profile')"><i>👤</i> Mi Perfil</a>
        <a href="#hacking" onclick="showSection('hacking')"><i>🔐</i> Hacking Ético</a>
        <a href="#courses" onclick="showSection('courses')"><i>📚</i> Cursos</a>
        <a href="#settings" onclick="showSection('settings')"><i>⚙️</i> Ajustes</a>
        <a href="#theme" onclick="toggleTheme()"><i>🌙</i> Modo Oscuro</a>
      </nav>
    </aside>

    <!-- INICIO -->
    <main id="home" class="active">
      <div class="create-post">
        <div class="post-creator">
          <img src="https://via.placeholder.com/40" alt="Tú" class="avatar">
          <input type="text" placeholder="¿Qué estás investigando, AnthZz?">
        </div>
        <div class="post-actions">
          <button><span>🎥</span> Live</button>
          <button><span>🖼️</span> Imagen</button>
          <button><span>💾</span> Código</button>
        </div>
      </div>

      <div class="post">
        <div class="post-header">
          <img src="https://via.placeholder.com/40" alt="Hacker" class="avatar">
          <div class="post-info">
            <strong>Carlos Dev</strong>
            <span>hace 1h</span>
          </div>
        </div>
        <div class="post-content">
          <p>Acabo de descubrir una vulnerabilidad XSS en un sistema educativo. Reportado éticamente. #BugBounty</p>
        </div>
        <div class="post-interactions">
          <button onclick="like(this)"><span>👍</span> Me gusta</button>
          <button><span>💬</span> Comentar</button>
          <button><span>↪️</span> Compartir</button>
        </div>
      </div>
    </main>

    <!-- PERFIL -->
    <main id="profile">
      <div class="profile-header">
        <div class="cover-photo" onclick="openModal('cover')"></div>
        <div class="profile-info">
          <div class="profile-pic-container">
            <img src="https://via.placeholder.com/140" alt="Perfil" class="profile-pic" id="profile-pic" onclick="openModal('photo')">
          </div>
          <h1 class="profile-name" id="profile-name">AnthZz Berrocal</h1>
          <p class="profile-bio" id="profile-bio">Hacker Ético | Desarrollador FullStack</p>
          <div class="stats">
            <div class="stat-item" onclick="openModal('posts')">
              <div class="stat-number" id="post-count">89</div>
              <div class="stat-label">Publicaciones</div>
            </div>
            <div class="stat-item" onclick="openModal('followers')">
              <div class="stat-number" id="follower-count">5,230</div>
              <div class="stat-label">Seguidores</div>
            </div>
            <div class="stat-item" onclick="openModal('following')">
              <div class="stat-number" id="following-count">840</div>
              <div class="stat-label">Siguiendo</div>
            </div>
          </div>
        </div>
      </div>

      <div class="tabs">
        <div class="tab active">Publicaciones</div>
        <div class="tab">Sobre Mí</div>
        <div class="tab">Proyectos</div>
        <div class="tab">Certificados</div>
      </div>

      <div class="tab-content">
        <p>Explora mis últimas investigaciones en seguridad informática.</p>
      </div>
    </main>

    <!-- HACKING -->
    <main id="hacking">
      <div class="post">
        <div class="post-header">
          <img src="https://via.placeholder.com/40/1877f2/fff?text=N" alt="News">
          <div class="post-info">
            <strong>Noticias de Seguridad</strong>
            <span>hace 30 min</span>
          </div>
        </div>
        <div class="post-content">
          <p>Un nuevo ransomware está atacando hospitales. Uso de técnicas de ofuscación avanzada. Analizando en entorno aislado.</p>
        </div>
      </div>
    </main>

    <!-- CURSOS -->
    <main id="courses">
      <h3>Cursos Recomendados</h3>
      <ul style="margin: 10px 0; padding-left: 20px;">
        <li>Introducción al Pentesting (2025)</li>
        <li>Desarrollo Seguro en JavaScript</li>
        <li>Análisis de Malware Básico</li>
      </ul>
    </main>

    <!-- AJUSTES -->
    <main id="settings">
      <div class="settings-panel">
        <h3>Información Personal</h3>
        <div class="setting-item">
          <label>Nombre</label>
          <input type="text" value="AnthZz Berrocal">
        </div>
        <div class="setting-item">
          <label>Correo</label>
          <input type="email" value="anthzz@cybernet.dev">
        </div>
        <div class="setting-item">
          <label>Bio</label>
          <textarea rows="2">Experto en seguridad informática y desarrollo ético.</textarea>
        </div>
        <button class="btn btn-primary">Guardar</button>

        <h3>Seguridad</h3>
        <div class="setting-item">
          <label>2FA</label>
          <select>
            <option>Desactivado</option>
            <option>Google Authenticator</option>
            <option>YubiKey</option>
          </select>
        </div>
        <button class="btn btn-dark">Activar 2FA</button>
      </div>
    </main>

  </div>

  <!-- MODAL -->
  <div class="modal" id="edit-modal">
    <div class="modal-content">
      <div class="modal-header">
        <div class="modal-title" id="modal-title">Editar</div>
        <button class="close-btn" onclick="closeModal()">&times;</button>
      </div>
      <div id="modal-body">
        <input type="text" id="modal-input" class="form-control" style="width:100%; padding:10px; margin:10px 0;">
      </div>
      <div class="btn-group">
        <button class="btn btn-primary" onclick="saveModal()">Guardar</button>
        <button class="btn btn-secondary" onclick="closeModal()">Cancelar</button>
      </div>
    </div>
  </div>

  <footer class="app-footer">
    <p>CyberNet © 2025 | By <strong>AnthZz Berrocal</strong> | Simulación Educativa de Red Social Tecnológica</p>
  </footer>

  <script>
    // ==========================================
    // SCRIPT PRINCIPAL - By AnthZz Berrocal
    // Navegación, edición, tema oscuro, localStorage
    // ==========================================

    const sections = document.querySelectorAll('main');
    const modal = document.getElementById('edit-modal');
    const modalTitle = document.getElementById('modal-title');
    const modalInput = document.getElementById('modal-input');
    let currentField = '';

    // Navegación
    function showSection(id) {
      sections.forEach(s => s.classList.remove('active'));
      document.getElementById(id).classList.add('active');
    }

    // Modal
    function openModal(field) {
      currentField = field;
      modal.style.display = 'flex';

      switch(field) {
        case 'photo':
          modalTitle.textContent = 'Cambiar Foto de Perfil';
          modalInput.value = document.getElementById('profile-pic').src;
          modalInput.placeholder = 'https://ejemplo.com/foto.jpg';
          break;
        case 'cover':
          modalTitle.textContent = 'Cambiar Portada';
          modalInput.value = document.querySelector('.cover-photo').style.backgroundImage.replace(/url\(|"|\)/g, '');
          modalInput.placeholder = 'https://ejemplo.com/portada.jpg';
          break;
        default:
          const element = document.getElementById(field + '-count');
          modalTitle.textContent = 'Editar ' + field.charAt(0).toUpperCase() + field.slice(1);
          modalInput.value = element.textContent.replace(/,/g, '');
          modalInput.type = 'number';
      }
    }

    function saveModal() {
      const value = modalInput.value;

      if (currentField === 'photo') {
        document.getElementById('profile-pic').src = value;
      } else if (currentField === 'cover') {
        document.querySelector('.cover-photo').style.backgroundImage = `url(${value})`;
      } else {
        const element = document.getElementById(currentField + '-count');
        element.textContent = Number(value).toLocaleString();
      }

      localStorage.setItem(`cybernet_${currentField}`, value);
      closeModal();
    }

    function closeModal() {
      modal.style.display = 'none';
    }

    // Tema oscuro
    function toggleTheme() {
      document.body.classList.toggle('dark-mode');
      const isDark = document.body.classList.contains('dark-mode');
      localStorage.setItem('cybernet_dark_mode', isDark);
    }

    // Cargar datos
    window.onload = function() {
      // Tema
      if (localStorage.getItem('cybernet_dark_mode') === 'true') {
        document.body.classList.add('dark-mode');
      }

      // Datos
      const fields = ['photo', 'cover', 'posts', 'followers', 'following'];
      fields.forEach(f => {
        const saved = localStorage.getItem(`cybernet_${f}`);
        if (saved) {
          if (f === 'photo') document.getElementById('profile-pic').src = saved;
          if (f === 'cover') document.querySelector('.cover-photo').style.backgroundImage = `url(${saved})`;
          if (['posts','followers','following'].includes(f)) {
            document.getElementById(f + '-count').textContent = Number(saved).toLocaleString();
          }
        }
      });
    };

    // Me gusta
    function like(btn) {
      btn.classList.toggle('liked');
    }

    // ESC para cerrar modal
    document.addEventListener('keydown', e => {
      if (e.key === 'Escape') closeModal();
    });
  </script>

</body>
</html>
