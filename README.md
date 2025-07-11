<!DOCTYPE html>
<html lang="cs">
<head>
  <meta charset="UTF-8">
  <title>Turnaj začíná!</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <style>
    body {
      font-family: 'Segoe UI', sans-serif;
      background: linear-gradient(135deg, #212121, #0d47a1);
      color: #fff;
      margin: 0;
      padding: 20px;
      text-align: center;
    }
    .step {
      display: none;
      animation: fade 0.6s ease-in-out forwards;
    }
    @keyframes fade {
      from {opacity:0; transform:translateY(20px);}
      to {opacity:1; transform:translateY(0);}
    }
    .active { display: block; }
    h1 { font-size: 1.8rem; margin-bottom: 1rem; }
    p { font-size: 1rem; margin: 1rem 0; }
    button {
      background: #ffca28;
      color: #000;
      border: none;
      padding: 12px 25px;
      border-radius: 30px;
      font-size: 1rem;
      cursor: pointer;
      margin-top: 20px;
      transition: background 0.3s;
    }
    button:hover { background: #ffd54f; }
    .option {
      background: rgba(255,255,255,0.1);
      padding: 12px;
      border-radius: 10px;
      margin: 10px auto;
      max-width: 360px;
      cursor: pointer;
      transition: background 0.2s;
    }
    .option:hover { background: rgba(255,255,255,0.2); }
    #timer {
      font-size: 1.2rem;
      background: rgba(255,255,255,0.15);
      padding: 8px 16px;
      border-radius: 50px;
      display: inline-block;
      margin-bottom: 15px;
    }
  </style>
</head>
<body>

  <!-- Step 1 -->
  <div class="step active" id="step1">
    <h1>🏆 Jsi připraven na výzvu?</h1>
    <div id="timer">01:00</div>
    <p>Začni tímto krátkým testem a zjisti svůj styl hry:</p>
    <div class="option" onclick="nextStep(1)">🎯 Preferuji strategii a plán</div>
    <div class="option" onclick="nextStep(1)">⚡ Mám rád náhodu a spontánnost</div>
  </div>

  <!-- Step 2 -->
  <div class="step" id="step2">
    <h1>🎲 Jak často riskuješ?</h1>
    <div class="option" onclick="nextStep(2)">Jen když mám jistotu</div>
    <div class="option" onclick="nextStep(2)">Riskuji často, kvůli vzrušení</div>
  </div>

  <!-- Step 3 -->
  <div class="step" id="step3">
    <h1>🧠 Co je pro tebe důležité při hře?</h1>
    <div class="option" onclick="document.getElementById('cta').style.display='block';">Zábava a relax</div>
    <div class="option" onclick="document.getElementById('cta').style.display='block';">Výhra a soutěžení</div>

    <!-- CTA -->
    <div id="cta" style="display:none;">
      <p style="font-size:0.9rem; margin-top:10px;">
        Tato nabídka je dostupná pouze pro uživatele starší 18 let.<br>
        Provozovatel je držitelem české licence pro online hazardní hry.
      </p>
      <button onclick="window.location.href='https://www.tipsport.cz/?utm_source=facebook&utm_medium=cpc&utm_campaign=promo2025';">
        🎁 Získat bonus a začít
      </button>
    </div>
  </div>

  <script>
    // Timer
    let time = 60;
    const timerEl = document.getElementById('timer');
    const countdown = setInterval(() => {
      time--;
      if (time >= 0) {
        timerEl.textContent = "00:" + String(time).padStart(2,'0');
      } else {
        clearInterval(countdown);
        timerEl.textContent = "⏳ Čas vypršel";
      }
    },1000);

    // Step logic
    function nextStep(current) {
      document.getElementById('step'+current).classList.remove('active');
      document.getElementById('step'+(current+1)).classList.add('active');
    }
  </script>

</body>
</html>
