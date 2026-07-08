<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Compte à rebours</title>
  <style>
    @import url('https://fonts.googleapis.com/css2?family=Quicksand:wght@300;400;600&display=swap');

    * { margin: 0; padding: 0; box-sizing: border-box; }

    body {
      background: transparent;
      font-family: 'Quicksand', sans-serif;
      display: flex;
      justify-content: center;
      align-items: center;
      min-height: 100vh;
      overflow: hidden;
    }

    .tulip {
      position: fixed;
      opacity: 0.2;
      pointer-events: none;
      animation: float 8s ease-in-out infinite;
    }
    .tulip:nth-child(1)  { top: 5%;  left: 5%;  font-size: 2.5rem; animation-delay: 0s; }
    .tulip:nth-child(2)  { top: 10%; right: 8%; font-size: 1.8rem; animation-delay: 1s; }
    .tulip:nth-child(3)  { top: 75%; left: 3%;  font-size: 2rem;   animation-delay: 2s; }
    .tulip:nth-child(4)  { top: 80%; right: 5%; font-size: 2.2rem; animation-delay: 3s; }
    .tulip:nth-child(5)  { top: 40%; left: 2%;  font-size: 1.5rem; animation-delay: 1.5s; }
    .tulip:nth-child(6)  { top: 50%; right: 3%; font-size: 1.7rem; animation-delay: 2.5s; }

    @keyframes float {
      0%, 100% { transform: translateY(0px) rotate(0deg); }
      50%       { transform: translateY(-12px) rotate(6deg); }
    }

    .container {
      text-align: center;
      padding: 1.5rem 2rem;
    }

    .title {
      font-size: 0.85rem;
      font-weight: 300;
      color: #7abf9e;
      letter-spacing: 0.2em;
      text-transform: uppercase;
      margin-bottom: 1.2rem;
    }

    .blocks {
      display: flex;
      gap: 1rem;
      justify-content: center;
      align-items: flex-start;
    }

    .block {
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 0.4rem;
    }

    .number {
      background: rgba(162, 213, 180, 0.12);
      border: 1px solid rgba(162, 213, 180, 0.3);
      border-radius: 12px;
      padding: 0.6rem 0.9rem;
      font-size: 2rem;
      font-weight: 600;
      color: #a2d5b4;
      min-width: 70px;
      text-align: center;
      letter-spacing: 0.05em;
    }

    .label {
      font-size: 0.65rem;
      color: #7abf9e;
      letter-spacing: 0.15em;
      text-transform: uppercase;
      font-weight: 400;
    }

    .separator {
      font-size: 2rem;
      color: rgba(162, 213, 180, 0.4);
      font-weight: 300;
      margin-top: 0.5rem;
      align-self: center;
    }

    .done {
      font-size: 1.2rem;
      color: #a2d5b4;
      font-weight: 300;
      letter-spacing: 0.1em;
    }
  </style>
</head>
<body>

  <!-- Tulipes décoratives -->
  <div class="tulip">🌷</div>
  <div class="tulip">🌷</div>
  <div class="tulip">🌷</div>
  <div class="tulip">🌷</div>
  <div class="tulip">🌷</div>
  <div class="tulip">🌷</div>

  <div class="container">
    <div class="title">🌷 sélection cosplay 🌷</div>
    <div class="blocks" id="countdown">
      <div class="block">
        <div class="number" id="days">--</div>
        <div class="label">jours</div>
      </div>
      <div class="separator">·</div>
      <div class="block">
        <div class="number" id="hours">--</div>
        <div class="label">heures</div>
      </div>
      <div class="separator">·</div>
      <div class="block">
        <div class="number" id="minutes">--</div>
        <div class="label">minutes</div>
      </div>
      <div class="separator">·</div>
      <div class="block">
        <div class="number" id="seconds">--</div>
        <div class="label">secondes</div>
      </div>
    </div>
  </div>

  <script>
    const target = new Date('2026-11-13T00:00:00');

    function update() {
      const now  = new Date();
      const diff = target - now;

      if (diff <= 0) {
        document.getElementById('countdown').innerHTML =
          '<p class="done">🌷 C\'est le grand jour ! 🌷</p>';
        return;
      }

      const days    = Math.floor(diff / 86400000);
      const hours   = Math.floor((diff % 86400000) / 3600000);
      const minutes = Math.floor((diff % 3600000)  / 60000);
      const seconds = Math.floor((diff % 60000)    / 1000);

      document.getElementById('days').textContent    = String(days).padStart(2, '0');
      document.getElementById('hours').textContent   = String(hours).padStart(2, '0');
      document.getElementById('minutes').textContent = String(minutes).padStart(2, '0');
      document.getElementById('seconds').textContent = String(seconds).padStart(2, '0');
    }

    update();
    setInterval(update, 1000);
  </script>
</body>
</html>
