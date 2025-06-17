# MI-AMOR
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Código de Amor</title>
  <style>
    body {
      margin: 0;
      font-family: 'Georgia', serif;
      background-color: #1f1f1f;
      color: #ddd;
      overflow: hidden;
    }
    .center {
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      text-align: center;
    }
    #codeInput {
      padding: 10px;
      font-size: 20px;
      background: #333;
      color: #0f0;
      border: 2px solid #444;
    }
    #submitCode {
      margin-top: 10px;
      padding: 10px 20px;
      background: #444;
      color: #ddd;
      border: none;
      cursor: pointer;
    }
    #continueBtn {
      display: none;
      padding: 10px 20px;
      background: #444;
      color: #ddd;
      border: none;
      cursor: pointer;
      position: absolute;
    }
    .card {
      display: none;
      padding: 20px;
      max-width: 700px;
      margin: auto;
      background: rgba(255, 255, 255, 0.05);
      backdrop-filter: blur(10px);
      border-radius: 10px;
      border: 1px solid #999;
    }
    .poem {
      display: none;
      padding: 20px;
      text-align: center;
    }
    .video {
      display: none;
      text-align: center;
      padding: 20px;
    }
    .decor {
      position: absolute;
      width: 100px;
      height: auto;
    }
    .left { left: 10px; top: 100px; }
    .right { right: 10px; top: 100px; }
    button:hover {
      background-color: #666;
    }
  </style>
</head>
<body>
  <div class="center" id="intro">
    <input type="text" id="codeInput" placeholder="Introduce el código">
    <br>
    <button id="submitCode">Entrar</button>
  </div>

  <button id="continueBtn">Continuar</button>

  <div class="card" id="carta">
    <img src="https://pngimg.com/d/pompompurin_PNG10.png" class="decor left">
    <img src="https://pngimg.com/d/pompompurin_PNG10.png" class="decor right">
    <p>
      Hay un latido que nace cada vez que pienso en ti. No es cualquier latido...
      <!-- Aquí va el resto del texto de la carta completo, acortado aquí por brevedad -->
    </p>
    <br>
    <button onclick="guardarCarta()">GUARDAR</button>
    <button onclick="mostrarPoema()">SIGUIENTE</button>
  </div>

  <div class="poem" id="poema">
    <p>
      En tus ojos veo el brillo de mi vida,<br>
      y en tu sonrisa encuentro mi paz y razón,<br>
      quiero estar contigo, sin prisa ni huida,<br>
      disfrutar cada día, sentir tu corazón.  
      <br><br>
      Eres mi refugio, mi calma, mi alegría,<br>
      contigo todo es más fácil de llevar,<br>
      con confianza y palabras, sin duda ni mentira,<br>
      podemos construir un mundo sin parar.  
      <br><br>
      Sé que si hablamos y confiamos en verdad,<br>
      todo puede mejorar, crecer y florecer,<br>
      la vida a tu lado es felicidad.  
      <br><br>
      Juntos podemos todo, solo hay que creer,<br>
      que en nuestro amor seguirá en la eternidad,<br>
      y que en la sencillez se aprende a querer.
    </p>
    <button onclick="mostrarVideo()">SIGUIENTE</button>
  </div>

  <div class="video" id="musica">
    <iframe style="border-radius:12px" src="https://open.spotify.com/embed/track/0qOeE5c4nU5R5w4T5iDsH6?utm_source=generator" width="100%" height="152" frameBorder="0" allowfullscreen="" allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture" loading="lazy"></iframe>
  </div>

  <script>
    const codeCorrecto = "220924";
    const submitBtn = document.getElementById("submitCode");
    const continueBtn = document.getElementById("continueBtn");
    const codeInput = document.getElementById("codeInput");

    submitBtn.onclick = () => {
      if (codeInput.value === codeCorrecto) {
        document.body.style.backgroundColor = "#004400";
        setTimeout(() => {
          document.body.style.backgroundColor = "#1f1f1f";
          document.getElementById("intro").style.display = "none";
          showMovingButton();
        }, 500);
      } else {
        alert("Código incorrecto :(");
      }
    }

    function showMovingButton() {
      continueBtn.style.display = "block";
      let moves = 0;
      const maxMoves = 3;

      continueBtn.onclick = () => {
        if (moves < maxMoves) {
          continueBtn.style.left = Math.random() * (window.innerWidth - 200) + "px";
          continueBtn.style.top = Math.random() * (window.innerHeight - 50) + "px";
          moves++;
        } else {
          continueBtn.style.display = "none";
          document.getElementById("carta").style.display = "block";
        }
      }
    }

    function guardarCarta() {
      alert("(Simulación) Carta guardada como imagen.");
      // Puedes implementar html2canvas o similar para descargar como imagen real
    }

    function mostrarPoema() {
      document.getElementById("carta").style.display = "none";
      document.getElementById("poema").style.display = "block";
    }

    function mostrarVideo() {
      document.getElementById("poema").style.display = "none";
      document.getElementById("musica").style.display = "block";
    }
  </script>
</body>
</html>
