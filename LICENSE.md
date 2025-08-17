<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>La Magia del Barbero - Barber Shop Andahuaylas</title>
  <meta name="description" content="Barbería de estilo clásico y moderno en Andahuaylas. 4 cortes y el 5to ¡GRATIS! Reserva ya.">
  
  <!-- Google Fonts -->
  <link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@400;600;700&family=Playfair+Display:wght@700&display=swap" rel="stylesheet">
  
  <!-- Font Awesome (iconos) -->
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css"/>

  <style>
    :root {
      --primary: #c72121; /* Rojo barbería */
      --secondary: #000;   /* Negro */
      --accent: #d4af37;   /* Dorado */
      --light: #f8f8f8;
      --dark: #222;
    }

    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      font-family: 'Montserrat', sans-serif;
      color: var(--dark);
      background-color: var(--light);
      line-height: 1.7;
    }

    h1, h2, h3, h4 {
      font-family: 'Playfair Display', serif;
      color: var(--secondary);
      font-weight: 700;
    }

    a {
      text-decoration: none;
      color: inherit;
    }

    /* Header */
    header {
      background: linear-gradient(rgba(0, 0, 0, 0.8), rgba(0, 0, 0, 0.8)), url('https://images.unsplash.com/photo-1560253414-bca15891aef3?ixlib=rb-4.0.3&auto=format&fit=crop&w=1200&q=80') no-repeat center center/cover;
      color: white;
      text-align: center;
      padding: 120px 20px;
    }

    header h1 {
      font-size: 3.5rem;
      margin-bottom: 15px;
      color: white;
      letter-spacing: 2px;
    }

    header p {
      font-size: 1.3rem;
      max-width: 700px;
      margin: 0 auto;
    }

    /* Botones */
    .btn {
      display: inline-block;
      background: var(--primary);
      color: white;
      padding: 12px 30px;
      border: none;
      margin-top: 20px;
      border-radius: 30px;
      font-weight: 600;
      transition: all 0.3s ease;
    }

    .btn:hover {
      background: var(--accent);
      transform: translateY(-3px);
    }

    /* Secciones */
    section {
      padding: 80px 20px;
      max-width: 1200px;
      margin: 0 auto;
    }

    .section-title {
      text-align: center;
      margin-bottom: 50px;
      font-size: 2.5rem;
      position: relative;
    }

    .section-title::after {
      content: '';
      display: block;
      width: 80px;
      height: 4px;
      background: var(--primary);
      margin: 15px auto;
    }

    /* Servicios */
    .services {
      background-color: white;
    }

    .service-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
      gap: 30px;
    }

    .service-card {
      background: #fff;
      border-radius: 10px;
      overflow: hidden;
      box-shadow: 0 5px 15px rgba(0,0,0,0.1);
      transition: transform 0.3s ease;
    }

    .service-card:hover {
      transform: translateY(-10px);
    }

    .service-img {
      height: 200px;
      overflow: hidden;
    }

    .service-img img {
      width: 100%;
      height: 100%;
      object-fit: cover;
      transition: transform 0.5s ease;
    }

    .service-card:hover .service-img img {
      transform: scale(1.1);
    }

    .service-content {
      padding: 20px;
      text-align: center;
    }

    .service-content h3 {
      font-size: 1.4rem;
      margin-bottom: 10px;
      color: var(--primary);
    }

    /* Promoción */
    .promo {
      background: linear-gradient(135deg, var(--primary), var(--secondary));
      color: white;
      text-align: center;
      border-radius: 15px;
      padding: 40px;
      margin: 0 auto;
      max-width: 900px;
      box-shadow: 0 10px 30px rgba(0,0,0,0.3);
    }

    .promo h2 {
      color: white;
    }

    .promo p {
      font-size: 1.2rem;
      margin: 15px 0;
    }

    .stamp-card {
      display: flex;
      justify-content: center;
      gap: 15px;
      margin: 30px 0;
      flex-wrap: wrap;
    }

    .stamp {
      width: 80px;
      height: 80px;
      background: white;
      border-radius: 50%;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 1.5rem;
      font-weight: bold;
      color: var(--primary);
      box-shadow: 0 4px 10px rgba(0,0,0,0.2);
    }

    .stamp.filled {
      background: var(--primary);
      color: white;
    }

    /* Galería */
    .gallery-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
      gap: 15px;
    }

    .gallery-item {
      border-radius: 10px;
      overflow: hidden;
      height: 200px;
      box-shadow: 0 5px 15px rgba(0,0,0,0.1);
    }

    .gallery-item img {
      width: 100%;
      height: 100%;
      object-fit: cover;
      transition: transform 0.4s ease;
    }

    .gallery-item:hover img {
      transform: scale(1.1);
    }

    /* Contacto */
    .contact {
      background-color: #f0f0f0;
    }

    .contact-info {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
      gap: 30px;
      margin-top: 30px;
    }

    .info-box {
      background: white;
      padding: 25px;
      border-radius: 10px;
      text-align: center;
      box-shadow: 0 5px 15px rgba(0,0,0,0.05);
    }

    .info-box i {
      font-size: 2.5rem;
      color: var(--primary);
      margin-bottom: 15px;
    }

    .info-box h3 {
      margin-bottom: 10px;
    }

    .info-box p {
      margin-bottom: 10px;
      color: #555;
    }

    .whatsapp-link {
      display: inline-block;
      background: #25D366;
      color: white;
      padding: 12px 25px;
      border-radius: 30px;
      margin-top: 10px;
      font-weight: 600;
    }

    .whatsapp-link i {
      margin-right: 8px;
    }

    .map {
      margin-top: 40px;
      border-radius: 10px;
      overflow: hidden;
      box-shadow: 0 5px 15px rgba(0,0,0,0.1);
      height: 400px;
    }

    .map iframe {
      width: 100%;
      height: 100%;
      border: 0;
    }

    /* Footer */
    footer {
      background: var(--secondary);
      color: white;
      text-align: center;
      padding: 30px 20px;
      font-size: 0.9rem;
    }

    .social-icons {
      margin: 20px 0;
    }

    .social-icons a {
      color: white;
      font-size: 1.5rem;
      margin: 0 10px;
      transition: color 0.3s ease;
    }

    .social-icons a:hover {
      color: var(--accent);
    }
  </style>
</head>
<body>

  <!-- Header -->
  <header id="inicio">
    <h1>LA MAGIA DEL BARBERO</h1>
    <p>Donde el estilo se convierte en tradición.</p>
    <a href="#contacto" class="btn">Reserva tu corte</a>
  </header>

  <!-- Servicios -->
  <section class="services" id="servicios">
    <h2 class="section-title">Nuestros Servicios</h2>
    <div class="service-grid">
      <div class="service-card">
        <div class="service-img">
          <img src="https://images.unsplash.com/photo-1580480018889-87a23656842a?ixlib=rb-4.0.3&auto=format&fit=crop&w=600&q=80" alt="Corte Clásico">
        </div>
        <div class="service-content">
          <h3>Corte Clásico</h3>
          <p>Estilo tradicional con precisión y elegancia. Ideal para hombres que buscan un look atemporal.</p>
        </div>
      </div>

      <div class="service-card">
        <div class="service-img">
          <img src="https://images.unsplash.com/photo-1605497788044-5a32c7078486?ixlib=rb-4.0.3&auto=format&fit=crop&w=600&q=80" alt="Corte Moderno">
        </div>
        <div class="service-content">
          <h3>Corte Moderno</h3>
          <p>Tendencias actuales, fades, diseños y líneas. Para los que siempre van a la moda.</p>
        </div>
      </div>

      <div class="service-card">
        <div class="service-img">
          <img src="https://images.unsplash.com/photo-1567581935880-9c282a882f7c?ixlib=rb-4.0.3&auto=format&fit=crop&w=600&q=80" alt="Barba">
        </div>
        <div class="service-content">
          <h3>Diseño de Barba</h3>
          <p>Recorte, forma y cuidado profesional. Deja que tu barba hable por ti.</p>
        </div>
      </div>

      <div class="service-card">
        <div class="service-img">
          <img src="https://images.unsplash.com/photo-1608231387581-c3c7e1a10db0?ixlib=rb-4.0.3&auto=format&fit=crop&w=600&q=80" alt="Afeitado">
        </div>
        <div class="service-content">
          <h3>Afeitado Clásico</h3>
          <p>Con navaja caliente y espuma premium. Sensación de piel renovada.</p>
        </div>
      </div>
    </div>
  </section>

  <!-- Promoción -->
  <section id="promocion">
    <h2 class="section-title">Promoción Especial</h2>
    <div class="promo">
      <h2>¡4 Cortes y el 5º es GRATIS!</h2>
      <p>Acumula tus visitas y disfruta de tu corte número 5 completamente gratis.</p>
      <div class="stamp-card">
        <div class="stamp filled">1</div>
        <div class="stamp filled">2</div>
        <div class="stamp filled">3</div>
        <div class="stamp filled">4</div>
        <div class="stamp">5</div>
      </div>
      <p><strong>¡Tu estilo merece recompensa!</strong></p>
    </div>
  </section>

  <!-- Galería -->
  <section id="galeria">
    <h2 class="section-title">Galería de Estilos</h2>
    <div class="gallery-grid">
      <div class="gallery-item">
        <img src="https://images.unsplash.com/photo-1503951914875-452162b0f3f1?ixlib=rb-4.0.3&auto=format&fit=crop&w=600&q=80" alt="Estilo 1">
      </div>
      <div class="gallery-item">
        <img src="https://images.unsplash.com/photo-1587628605077-0124e738e73b?ixlib=rb-4.0.3&auto=format&fit=crop&w=600&q=80" alt="Estilo 2">
      </div>
      <div class="gallery-item">
        <img src="https://images.unsplash.com/photo-1562322140-8baeececf3df?ixlib=rb-4.0.3&auto=format&fit=crop&w=600&q=80" alt="Estilo 3">
      </div>
      <div class="gallery-item">
        <img src="https://images.unsplash.com/photo-1542976479-2c289cd2e58f?ixlib=rb-4.0.3&auto=format&fit=crop&w=600&q=80" alt="Estilo 4">
      </div>
      <div class="gallery-item">
        <img src="https://images.unsplash.com/photo-1544005313-94ddf0286df2?ixlib=rb-4.0.3&auto=format&fit=crop&w=600&q=80" alt="Estilo 5">
      </div>
      <div class="gallery-item">
        <img src="https://images.unsplash.com/photo-1575669929136-3235999e781d?ixlib=rb-4.0.3&auto=format&fit=crop&w=600&q=80" alt="Estilo 6">
      </div>
    </div>
  </section>

  <!-- Contacto -->
  <section class="contact" id="contacto">
    <h2 class="section-title">Contáctanos</h2>
    <div class="contact-info">
      <div class="info-box">
        <i class="fas fa-phone"></i>
        <h3>Teléfonos</h3>
        <p>977 355 999</p>
        <p>931 538 059</p>
        <a href="https://wa.me/51977355999" target="_blank" class="whatsapp-link">
          <i class="fab fa-whatsapp"></i> WhatsApp 1
        </a><br><br>
        <a href="https://wa.me/51931538059" target="_blank" class="whatsapp-link">
          <i class="fab fa-whatsapp"></i> WhatsApp 2
        </a>
      </div>

      <div class="info-box">
        <i class="fas fa-map-marker-alt"></i>
        <h3>Ubicación</h3>
        <p><strong>Dirección:</strong></p>
        <p>Jirón Alfonso Ugarte</p>
        <p>3er piso, Andahuaylas</p>
        <p>Provincia de Andahuaylas, Apurímac</p>
      </div>

      <div class="info-box">
        <i class="fas fa-clock"></i>
        <h3>Horario</h3>
        <p>Lunes a Sábado</p>
        <p>9:00 AM - 7:00 PM</p>
        <p>Domingo: 10:00 AM - 4:00 PM</p>
      </div>
    </div>

    <!-- Mapa de Google Maps -->
    <div class="map">
      <iframe src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3871.676951533876!2d-73.4457649851484!3d-13.627076990324878!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x916dfe12c415224d%3A0x4c27c9f718341925!2sAndahuaylas%2C%20Per%C3%BA!5e0!3m2!1ses!2ses!4v1698729001234!5m2!1ses!2ses" 
        allowfullscreen="" loading="lazy" referrerpolicy="no-referrer-when-downgrade">
      </iframe>
    </div>
  </section>

  <!-- Footer -->
  <footer>
    <p>&copy; 2025 La Magia del Barbero - Todos los derechos reservados</p>
    <p>Diseñado con estilo y precisión.</p>
    <div class="social-icons">
      <a href="#"><i class="fab fa-facebook"></i></a>
      <a href="#"><i class="fab fa-instagram"></i></a>
    </div>
  </footer>

</body>
</html>
