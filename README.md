
<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<meta name="theme-color" content="#08040d">
<title>Tom y el Cementerio Maldito</title>

<style>
*{box-sizing:border-box}

html,body{
  margin:0;width:100%;height:100%;
  overflow:hidden;background:#08040d;color:white;
  font-family:Georgia,serif;
}

button,a{-webkit-tap-highlight-color:transparent}

.screen{
  position:fixed;inset:0;width:100%;height:100%;
  overflow:hidden;background:#08040d;
}

.hidden{display:none!important}

.full-image{
  position:absolute;inset:0;width:100%;height:100%;
  object-fit:cover;object-position:center;
  display:block;
}

.shade{
  position:absolute;inset:0;pointer-events:none;
  background:linear-gradient(
    0deg,rgba(0,0,0,.88) 0%,
    rgba(0,0,0,.48) 25%,
    transparent 62%,
    rgba(0,0,0,.18) 100%
  );
}

#introImage{animation:slowZoom 12s ease-in-out infinite alternate}

@keyframes slowZoom{
  from{transform:scale(1)}
  to{transform:scale(1.08)}
}

#filmImage{
  opacity:1;
  transition:opacity .8s ease;
}

#filmImage.fade{opacity:0}

.story-copy{
  position:absolute;z-index:3;
  left:6%;right:6%;bottom:10%;
  text-align:left;
  text-shadow:0 3px 8px #000,0 0 18px #000;
}

.eyebrow{
  color:#ffd28a;
  font:bold 12px Arial,sans-serif;
  letter-spacing:3px;
  margin-bottom:12px;
}

.story-copy h1{
  font-size:clamp(28px,5vw,58px);
  margin:0 0 12px;
  color:#ffe0a1;
  text-shadow:0 0 20px #a14cff;
}

.story-copy p{
  font-size:clamp(18px,2.7vw,29px);
  line-height:1.4;
  max-width:900px;
  margin:0;
}

.film-progress{
  position:absolute;left:0;right:0;top:0;
  height:4px;background:#ffffff30;z-index:5;
}

.film-progress span{
  display:block;width:0;height:100%;
  background:#ffd28a;
}

.action{
  border:1px solid #ffe0a1;
  color:white;
  background:linear-gradient(135deg,#8a36a8,#32103e);
  padding:14px 24px;
  border-radius:40px;
  font:bold 15px Arial,sans-serif;
  cursor:pointer;
  box-shadow:0 5px 25px #0009;
}

.action:hover{filter:brightness(1.2)}

.intro-content{
  position:absolute;z-index:3;
  inset:0;display:flex;
  flex-direction:column;align-items:center;
  justify-content:flex-end;
  padding:30px 18px 9vh;
  background:linear-gradient(transparent 25%,#08040dd9 100%);
}

.intro-content h1{
  color:#ffdc9b;
  font-size:clamp(32px,7vw,72px);
  text-shadow:0 0 25px #9a40ff;
  margin:0 0 12px;
}

.intro-content p{
  font-size:clamp(16px,2.5vw,23px);
  margin:0 0 22px;
}

.top-controls{
  position:absolute;top:15px;right:15px;
  z-index:8;display:flex;gap:8px;
}

.round{
  border:1px solid #ffffff70;
  background:#130b1dbb;color:white;
  border-radius:50%;width:44px;height:44px;
  font-size:19px;cursor:pointer;
  backdrop-filter:blur(8px);
}

.tomb-title{
  position:absolute;z-index:4;
  top:5%;left:5%;right:5%;
  text-align:center;
  text-shadow:0 2px 8px #000,0 0 15px #000;
  pointer-events:none;
}

.tomb-title h2{
  font-size:clamp(24px,4.5vw,48px);
  color:#ffe0a1;margin:0 0 8px;
}

.tomb-title p{
  font-size:clamp(14px,2vw,21px);
  margin:0;
}

.tomb-choice{
  position:absolute;z-index:3;
  top:32%;height:47%;width:12%;
  border:2px solid transparent;
  border-radius:45% 45% 8px 8px;
  background:transparent;cursor:pointer;
  color:transparent;
}

.tomb-choice:hover,.tomb-choice:focus-visible{
  outline:none;border-color:#ffe0a1;
  background:#ffd27a22;
  box-shadow:0 0 25px #ffd27a99;
}

.tomb-choice span{
  position:absolute;bottom:0;left:50%;
  transform:translateX(-50%);
  color:#fff;background:#160a22dc;
  border:1px solid #ffe0a1;
  border-radius:50%;width:32px;height:32px;
  display:grid;place-items:center;
  font:bold 15px Arial,sans-serif;
}

.result-content{
  position:absolute;z-index:4;inset:0;
  display:flex;flex-direction:column;
  justify-content:center;align-items:center;
  padding:25px;text-align:center;
  background:#08040d99;
  backdrop-filter:blur(2px);
}

.result-content h2{
  color:#ffe0a1;
  font-size:clamp(28px,5vw,52px);
  text-shadow:0 0 20px #9c3fff;
  margin:0 0 10px;
}

.prize{
  font:bold clamp(45px,10vw,85px) Arial,sans-serif;
  color:#ffda79;
  text-shadow:0 0 30px #ff832d;
  margin:14px 0;
}

.conditions{
  font:14px/1.8 Arial,sans-serif;
  text-shadow:0 2px 5px black;
  margin:10px 0 18px;
}

.muted{
  font:12px Arial,sans-serif;color:#e3d7eb;
  margin-top:16px;
}

@media(max-width:600px){
  .story-copy{bottom:9%;left:5%;right:5%}
  .story-copy p{font-size:19px}
  .eyebrow{font-size:10px}
  .tomb-title{top:5%}
  .tomb-title h2{font-size:27px}
  .tomb-title p{font-size:14px}
  .tomb-choice{top:36%;height:39%;width:13%}
}
</style>
</head>

<body>

<!-- PORTADA A PANTALLA COMPLETA -->
<section id="intro" class="screen">
  <img id="introImage" class="full-image"
       src="escena1.png" alt="Tom sale a buscar dulces">
  <div class="shade"></div>

  <div class="top-controls">
    <button class="round" id="sound" aria-label="Activar sonido">🔇</button>
  </div>

  <div class="intro-content">
    <h1>Tom y el Cementerio Maldito</h1>
    <p>Una noche de Halloween, una aventura aterradora…</p>
    <button class="action" id="start">▶ COMENZAR HISTORIA</button>
  </div>
</section>

<!-- CORTOMETRAJE AUTOMÁTICO -->
<section id="film" class="screen hidden">
  <img id="filmImage" class="full-image"
       src="escena1.png" alt="Escena de la película">
  <div class="shade"></div>
  <div class="film-progress"><span id="progress"></span></div>

  <div class="top-controls">
    <button class="round" id="muteFilm" aria-label="Activar o silenciar sonido">🔇</button>
    <button class="round" id="skip" aria-label="Saltar película">⏭</button>
  </div>

  <div class="story-copy">
    <div class="eyebrow" id="chapter"></div>
    <p id="subtitle"></p>
  </div>
</section>

<!-- IMAGEN PANORÁMICA DE LAS SEIS TUMBAS -->
<section id="tombs" class="screen hidden">
  <img class="full-image" src="tumbas.png"
       alt="Las seis tumbas del cementerio">
  <div class="shade"></div>

  <div class="top-controls">
    <button class="round" id="muteTombs" aria-label="Sonido">🔊</button>
  </div>

  <div class="tomb-title">
    <h2>Las seis tumbas malditas</h2>
    <p>Tom encontró seis tumbas… elegí una para descubrir tu premio.</p>
  </div>

  <button class="tomb-choice" style="left:3%"
          aria-label="Elegir tumba 1"><span>1</span></button>
  <button class="tomb-choice" style="left:19%"
          aria-label="Elegir tumba 2"><span>2</span></button>
  <button class="tomb-choice" style="left:35%"
          aria-label="Elegir tumba 3"><span>3</span></button>
  <button class="tomb-choice" style="left:51%"
          aria-label="Elegir tumba 4"><span>4</span></button>
  <button class="tomb-choice" style="left:67%"
          aria-label="Elegir tumba 5"><span>5</span></button>
  <button class="tomb-choice" style="left:83%"
          aria-label="Elegir tumba 6"><span>6</span></button>
</section>

<!-- RESULTADO A PANTALLA COMPLETA -->
<section id="result" class="screen hidden">
  <img class="full-image" src="tumbas.png" alt="Cementerio maldito">
  <div class="result-content">
    <h2 id="resultTitle">¡La tumba reveló tu premio!</h2>
    <div class="prize" id="prize"></div>
    <p id="resultText"></p>

    <div class="conditions">
      🎁 Sin mínimo de carga.<br>
      💰 Tope de bonificación: $30.000.<br>
      🔄 Para retirar con bono hay que duplicarlo.<br>
      🚫 No válido para ruleta.<br>
      🎮 Una plataforma, una carga y un número.<br>
      🐱 Una vez por usuario.
    </div>

    <a class="action" id="claim"
       href="https://wa.link/v2txxr"
       target="_blank" rel="noopener">
       💬 RECLAMAR MI PREMIO
    </a>

    <p class="muted">Guardá una captura de tu resultado.</p>
  </div>
</section>

<script>
(() => {
  const $ = id => document.getElementById(id);
  const screens = ["intro","film","tombs","result"];
  const storageKey = "tumbatom-premio-final-v1";

  function show(name) {
    screens.forEach(id => $(id).classList.toggle("hidden", id !== name));
    window.scrollTo(0, 0);
  }

  // Cada imagen corresponde a la escena que muestra.
  const scenes = [
    {
      image:"escena1.png",
      chapter:"CAPÍTULO I · NOCHE DE HALLOWEEN",
      text:"Tom se vistió de vampiro y salió feliz a pedir dulces por el vecindario."
    },
    {
      image:"escena2.png",
      chapter:"CAPÍTULO II · EL VECINDARIO",
      text:"Las casas estaban decoradas. Tom siguió caminando, buscando más dulces entre las luces de Halloween."
    },
    {
      image:"escena3.png",
      chapter:"CAPÍTULO III · LA NIEBLA",
      text:"De pronto, una niebla espesa cubrió el camino. Tom se perdió y no encontraba la forma de regresar."
    },
    {
      image:"escena4.png",
      chapter:"CAPÍTULO IV · LAS REJAS ABIERTAS",
      text:"A lo lejos descubrió la entrada de un cementerio. Las rejas estaban abiertas… y todo estaba en silencio."
    },
    {
      image:"escena5.png",
      chapter:"CAPÍTULO V · EL DESCUBRIMIENTO",
      text:"Tom entró lentamente. Bajo la luna aparecieron seis tumbas misteriosas. ¿Qué secreto escondían?"
    }
  ];

  let current = 0;
  let timer = null;
  let startedAt = 0;
  let soundOn = false;
  let audio = null;
  const sceneDuration = 6500;

  function stopTimer() {
    if (timer) clearInterval(timer);
    timer = null;
  }

  // Sonido sencillo, sin archivos de audio adicionales.
  function soundEffect() {
    if (!soundOn) return;

    try {
      audio = audio || new (window.AudioContext || window.webkitAudioContext)();
      if (audio.state === "suspended") audio.resume();

      const osc = audio.createOscillator();
      const gain = audio.createGain();
      osc.type = "sine";
      osc.frequency.setValueAtTime(180, audio.currentTime);
      osc.frequency.exponentialRampToValueAtTime(70, audio.currentTime + .4);
      gain.gain.setValueAtTime(.045, audio.currentTime);
      gain.gain.exponentialRampToValueAtTime(.001, audio.currentTime + .42);
      osc.connect(gain);
      gain.connect(audio.destination);
      osc.start();
      osc.stop(audio.currentTime + .43);
    } catch (e) {}
  }

  function toggleSound() {
    soundOn = !soundOn;
    ["sound","muteFilm","muteTombs"].forEach(id => {
      $(id).textContent = soundOn ? "🔊" : "🔇";
    });
    if (soundOn) soundEffect();
  }

  ["sound","muteFilm","muteTombs"].forEach(id => {
    $(id).addEventListener("click", toggleSound);
  });

  function renderScene() {
    stopTimer();
    const scene = scenes[current];
    const image = $("filmImage");

    image.classList.add("fade");

    setTimeout(() => {
      image.src = scene.image;
      image.alt = scene.chapter;
      $("chapter").textContent = scene.chapter;
      $("subtitle").textContent = scene.text;

      image.onload = () => image.classList.remove("fade");
      if (image.complete) image.classList.remove("fade");
    }, 400);

    startedAt = Date.now();

    timer = setInterval(() => {
      const elapsed = Date.now() - startedAt;
      $("progress").style.width =
        Math.min(100, elapsed / sceneDuration * 100) + "%";

      if (elapsed >= sceneDuration) nextScene();
    }, 100);

    soundEffect();
  }

  function nextScene() {
    stopTimer();

    if (current < scenes.length - 1) {
      current++;
      renderScene();
    } else {
      $("progress").style.width = "100%";
      show("tombs");
      soundEffect();
    }
  }

  $("start").addEventListener("click", () => {
    const old = getSaved();
    if (old) {
      displayResult(old, true);
      return;
    }

    current = 0;
    show("film");
    renderScene();
  });

  $("skip").addEventListener("click", () => {
    stopTimer();
    show("tombs");
  });

  function getSaved() {
    try {
      return JSON.parse(localStorage.getItem(storageKey) || "null");
    } catch (e) {
      return null;
    }
  }

  const prizes = ["$500", "$1.000", "10%", "15%", "25%", "30%"];

  function displayResult(data, repeated) {
    $("resultTitle").textContent = repeated
      ? "🪦 YA PARTICIPASTE"
      : "🎃 ¡LA TUMBA REVELÓ TU PREMIO!";

    $("prize").textContent = data.prize;

    $("resultText").textContent = repeated
      ? "Tu premio guardado fue " + data.prize +
        " en la tumba " + data.grave + "."
      : "Elegiste la tumba " + data.grave +
        " y descubriste " + data.prize + ".";

    const message =
      "¡Hola, Comunidad Tom! 🎃 Elegí la tumba " + data.grave +
      " y gané " + data.prize +
      " en Tom y el Cementerio Maldito. Quiero reclamar mi premio.";

    // Este enlace abre WhatsApp con el mensaje preparado.
    $("claim").href =
      "https://wa.me/?text=" + encodeURIComponent(message);

    show("result");
  }

  document.querySelectorAll(".tomb-choice").forEach((button, index) => {
    button.addEventListener("click", () => {
      const old = getSaved();
      if (old) {
        displayResult(old, true);
        return;
      }

      const values = new Uint32Array(1);

      if (window.crypto && window.crypto.getRandomValues) {
        window.crypto.getRandomValues(values);
      } else {
        values[0] = Math.floor(Math.random() * 4294967295);
      }

      const data = {
        grave: index + 1,
        prize: prizes[values[0] % prizes.length]
      };

      try {
        localStorage.setItem(storageKey, JSON.stringify(data));
      } catch (e) {}

      soundEffect();
      displayResult(data, false);
    });
  });

})();
</script>
</body>
</html>
