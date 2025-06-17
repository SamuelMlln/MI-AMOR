<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>MI AMOR</title>
  <style>
    * {
      box-sizing: border-box;
    }
    body {
      margin: 0;
      font-family: 'Segoe UI', sans-serif;
      background-color: #1e1e1e;
      color: #fff;
      overflow: hidden;
    }
    .center {
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      flex-direction: column;
      text-align: center;
    }
    input[type="password"] {
      padding: 10px;
      font-size: 18px;
      border-radius: 8px;
      border: none;
      outline: none;
      margin-bottom: 20px;
    }
    button {
      padding: 10px 20px;
      font-size: 18px;
      border: none;
      border-radius: 8px;
      background-color: #444;
      color: white;
      cursor: pointer;
      transition: 0.3s;
    }
    button:hover {
      background-color: #666;
    }
    .hidden {
      display: none;
    }
    .card-page {
      display: none;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      padding: 30px;
      height: 100vh;
      background: linear-gradient(to right, #2c2c2c, #1a1a1a);
      overflow-y: auto;
    }
    .card {
      background-color: #333;
      padding: 20px;
      border-radius: 20px;
      max-width: 800px;
      box-shadow: 0 0 20px rgba(0,255,0,0.2);
      font-size: 18px;
      line-height: 1.6;
      position: relative;
    }
    .decor {
      position: absolute;
      top: -40px;
      width: 80px;
    }
    .left-decor {
      left: -100px;
    }
    .right-decor {
      right: -100px;
    }
    .next-page {
      margin-top: 30px;
      display: flex;
      gap: 20px;
    }
    .poem-page {
      display: none;
      text-align: center;
      padding: 40px;
      background-color: #121212;
      height: 100vh;
      color: #eee;
      overflow-y: auto;
    }
    .poem {
      font-size: 20px;
      max-width: 700px;
      margin: 0 auto;
    }
    .music-page {
      display: none;
      justify-content: center;
      align-items: center;
      height: 100vh;
      background: #000;
      color: white;
      flex-direction: column;
      text-align: center;
    }
  </style>
</head>
<body>

<div id="codePage" class="center">
  <h1>Ingresa el código</h1>
  <input type="password" id="codeInput" placeholder="######" />
  <button onclick="verifyCode()">Continuar</button>
</div>

<div id="cardPage" class="card-page">
  <div class="card">
    <img class="decor left-decor" src="https://i.imgur.com/JgkIGyo.png" alt="Pompompurin">
    <img class="decor right-decor" src="https://i.imgur.com/JgkIGyo.png" alt="Pompompurin">
    <p>
      Hay un latido que nace cada vez que pienso en ti...<br/><br/>
      (Aquí iría toda la carta que me diste)
    </p>
    <div class="next-page">
      <button onclick="saveCard()">GUARDAR</button>
      <button onclick="goToPoem()">SIGUIENTE</button>
    </div>
  </div>
</div>

<div id="poemPage" class="poem-page">
  <div class="poem">
    <p>En tus ojos veo el brillo de mi vida,<br/>
    y en tu sonrisa encuentro mi paz y razón,<br/>
    quiero estar contigo, sin prisa ni huida,<br/>
    disfrutar cada día, sentir tu corazón.</p>

    <p>Eres mi refugio, mi calma, mi alegría,<br/>
    contigo todo es más fácil de llevar,<br/>
    con confianza y palabras, sin duda ni mentira,<br/>
    podemos construir un mundo sin parar.</p>

    <p>Sé que si hablamos y confiamos en verdad,<br/>
    todo puede mejorar, crecer y florecer,<br/>
    la vida a tu lado es felicidad.</p>

    <p>Juntos podemos todo, solo hay que creer,<br/>
    que en nuestro amor seguirá en la eternidad,<br/>
    y que en la sencillez se aprende a querer.</p>
  </div>
  <br/>
  <button onclick="goToMusic()">SIGUIENTE</button>
</div>

<div id="musicPage" class="music-page">
  <h2>🎵 Tú y Yo – La Misma Gente 🎵</h2>
  <iframe style="border-radius:12px" src="https://open.spotify.com/embed/track/5FV6f1UBrkPzXkEb6hddol?utm_source=generator" width="80%" height="152" frameBorder="0" allowfullscreen="" allow="autoplay; clipboard-write; encrypted-media; picture-in-picture"></iframe>
</div>

<script>
  const code = "220924";

  function verifyCode() {
    const input = document.getElementById("codeInput").value;
    if (input === code) {
      document.body.style.backgroundColor = "#006400";
      setTimeout(() => {
        document.body.style.backgroundColor = "#1e1e1e";
        moveButtonEffect();
      }, 300);
    } else {
      alert("Código incorrecto 😢");
    }
  }

  function moveButtonEffect() {
    const button = document.querySelector("#codePage button");
    let count = 0;
    const positions = ["translateX(100px)", "translateX(-100px)", "translateY(-50px)", "translateY(50px)", "translateX(0px)"];
    const interval = setInterval(() => {
      button.style.transform = positions[count % positions.length];
      count++;
      if (count > 5) {
        clearInterval(interval);
        setTimeout(() => {
          document.getElementById("codePage").style.display = "none";
          document.getElementById("cardPage").style.display = "flex";
        }, 500);
      }
    }, 300);
  }

  function saveCard() {
    alert("Esta función guardará la carta como imagen pronto 💖 (Simulado)");
  }

  function goToPoem() {
    document.getElementById("cardPage").style.display = "none";
    document.getElementById("poemPage").style.display = "block";
  }

  function goToMusic() {
    document.getElementById("poemPage").style.display = "none";
    document.getElementById("musicPage").style.display = "flex";
  }
</script>

</body>
</html>

