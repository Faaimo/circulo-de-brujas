<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Círculo de Brujas</title>
  <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600&display=swap" rel="stylesheet">
  <style>
    body {
      margin: 0;
      font-family: 'Poppins', sans-serif;
      background: url('assets/images/bg_inicio.jpg') no-repeat center center/cover;
      color: white;
      overflow-x: hidden;
    }

    header {
      display: flex;
      align-items: center;
      justify-content: space-between;
      padding: 20px;
      position: absolute;
      width: 100%;
      top: 0;
      z-index: 100;
    }

    .logo-container {
      display: flex;
      align-items: center;
    }

    .logo-container img {
      margin-right: 10px;
    }

    nav {
      display: flex;
      gap: 30px;
    }

    nav a {
      color: white;
      text-decoration: none;
      font-weight: 400;
    }

    .register-button {
      background-color: #c33ed9;
      border: none;
      padding: 10px 20px;
      border-radius: 5px;
      color: white;
      font-weight: 600;
      cursor: pointer;
    }

    .carrusel-container {
      position: relative;
      top: 150px;
      display: flex;
      flex-direction: column;
      align-items: center;
    }

    .carrusel {
      display: flex;
      align-items: center;
      justify-content: center;
      position: relative;
      width: 100%;
      max-width: 1000px;
    }

    .carta {
      width: 150px;
      height: auto;
      margin: 0 10px;
      transition: transform 0.5s, opacity 0.5s;
      cursor: pointer;
      opacity: 0.6;
      z-index: 1;
      position: absolute;
    }

    .carta.activa {
      transform: scale(1.2);
      opacity: 1;
      z-index: 5;
    }

    .flechas {
      margin-top: 30px;
    }

    .flechas button {
      background: white;
      color: black;
      border: none;
      padding: 10px;
      border-radius: 50%;
      font-size: 20px;
      margin: 0 10px;
      cursor: pointer;
    }
  </style>
</head>
<body>
  <header>
    <div class="logo-container">
      <img src="assets/images/iniciale_cb.svg" width="40" alt="Iniciales CB">
      <img src="assets/images/logo_principal.svg" width="150" alt="Logo Círculo de Brujas">
    </div>
    <nav>
      <a href="#">CALDERO DE CONOCIMIENTO</a>
      <a href="#">ÚNETE A UNA CASA</a>
      <a href="#">EXPLORA EL LIBRERO MÁGICO</a>
      <button class="register-button">Regístrate</button>
    </nav>
  </header>

  <div class="carrusel-container">
    <div class="carrusel" id="carrusel">
      <a href="grimorio.html"><img src="assets/images/Grimorio_de_historias.jpg" class="carta activa" /></a>
      <a href="hechizos.html"><img src="assets/images/Hechizos_para_conocer.jpg" class="carta" /></a>
      <a href="cronicas.html"><img src="assets/images/Crónicas_sobre_amate.jpg" class="carta" /></a>
      <a href="ojo.html"><img src="assets/images/Ojo_de_loca.jpg" class="carta" /></a>
      <a href="septimoarte.html"><img src="assets/images/Brujas_de_septimo_arte.jpg" class="carta" /></a>
    </div>
    <div class="flechas">
      <button onclick="moverCarrusel(-1)">⟨</button>
      <button onclick="moverCarrusel(1)">⟩</button>
    </div>
  </div>

  <script>
    const cartas = document.querySelectorAll('.carta');
    let index = 0;

    function updateCarrusel() {
      cartas.forEach((carta, i) => {
        carta.classList.remove('activa');
        carta.style.transform = `translateX(${(i - index) * 180}px) scale(${i === index ? 1.2 : 0.9})`;
        carta.style.opacity = i === index ? 1 : 0.6;
        carta.style.zIndex = i === index ? 10 : 1;
      });
      cartas[index].classList.add('activa');
    }

    function moverCarrusel(direccion) {
      index = (index + direccion + cartas.length) % cartas.length;
      updateCarrusel();
    }

    updateCarrusel();
  </script>
</body>
</html>
