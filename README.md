<!DOCTYPE html>
<html lang="de">
<head>
  <meta charset="UTF-8">
  <title>TikTok Overlay</title>

  <style>
    html, body {
      margin: 0;
      padding: 0;
      width: 100%;
      height: 100%;
      background: transparent;
      overflow: hidden;
      display: flex;
      justify-content: center;
      align-items: center;
    }

    .overlay {
      position: relative;
      width: 110px;
      height: 110px;
      border-radius: 18px;
      background: linear-gradient(135deg, #ff4b3a, #ff1f1f);
      box-shadow:
        inset 0 0 10px rgba(255,255,255,0.25),
        0 0 22px rgba(255,70,60,0.6);
      overflow: hidden;
    }

    /* 🔲 Fester Rahmen (sharp outline) */
    .overlay::after {
      content: "";
      position: absolute;
      inset: 2px;
      border-radius: 14px;
      border: 2px solid rgba(255,255,255,0.85);
      pointer-events: none;
    }

    /* ✨ Glow Outline (animiert) */
    .overlay::before {
      content: "";
      position: absolute;
      inset: -4px;
      border-radius: inherit;
      background: linear-gradient(
        270deg,
        #ffd700,
        #ff3b2f,
        #ff00ff,
        #ffd700
      );
      background-size: 400% 400%;
      animation: outlineFlow 6s linear infinite;
      filter: blur(7px);
      z-index: -1;
    }

    @keyframes outlineFlow {
      0%   { background-position: 0% 50%; }
      100% { background-position: 400% 50%; }
    }

    /* 🌟 Glint Effekt */
    .glint {
      position: absolute;
      inset: 0;
      border-radius: inherit;
      background: linear-gradient(
        120deg,
        transparent 35%,
        rgba(255,255,255,0.75) 50%,
        transparent 65%
      );
      transform: translateX(-130%);
      animation: glintMove 3.5s ease-in-out infinite;
      pointer-events: none;
    }

    @keyframes glintMove {
      0%   { transform: translateX(-130%); }
      60%  { transform: translateX(130%); }
      100% { transform: translateX(130%); }
    }
  </style>
</head>

<body>
  <div class="overlay">
    <div class="glint"></div>
  </div>
</body>
</html>
