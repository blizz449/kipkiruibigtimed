

```html name=index.html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Our Love Story</title>
  <style>
    :root {
      --bg-1: #090b16;
      --bg-2: #140d1e;
      --card: rgba(19, 22, 37, 0.8);
      --gold: #ffd166;
      --pink: #ff7eb6;
      --rose: #ff9ec7;
      --lavender: #c7b3ff;
      --mint: #8ef0d3;
      --white: #f7f3ff;
      --soft: #d9d0f5;
      --shadow: rgba(0, 0, 0, 0.45);
    }

    * { box-sizing: border-box; }

    body {
      margin: 0;
      min-height: 100vh;
      display: flex;
      align-items: center;
      justify-content: center;
      background:
        radial-gradient(circle at top, rgba(255, 126, 182, 0.12), transparent 30%),
        radial-gradient(circle at bottom right, rgba(124, 92, 255, 0.14), transparent 35%),
        linear-gradient(135deg, var(--bg-1), var(--bg-2));
      color: var(--white);
      font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
      overflow: hidden;
    }

    .container {
      width: min(92vw, 850px);
      background: rgba(17, 20, 34, 0.72);
      border: 1px solid rgba(255, 255, 255, 0.08);
      border-radius: 28px;
      padding: 38px 28px;
      box-shadow: 0 30px 70px var(--shadow);
      backdrop-filter: blur(10px);
      position: relative;
      overflow: hidden;
      z-index: 1;
    }

    .container::before {
      content: "";
      position: absolute;
      inset: 0;
      background: linear-gradient(120deg, rgba(255, 209, 102, 0.04), rgba(255, 126, 182, 0.03));
      pointer-events: none;
    }

    .content {
      position: relative;
      z-index: 1;
      text-align: center;
    }

    .title {
      margin: 0;
      font-size: clamp(2.4rem, 5vw, 4.2rem);
      font-family: Georgia, "Times New Roman", serif;
      color: var(--gold);
      letter-spacing: 0.06em;
      text-shadow: 0 0 20px rgba(255, 209, 102, 0.3);
    }

    .subtitle {
      color: var(--pink);
      font-size: 1.2rem;
      margin-top: 14px;
      letter-spacing: 0.14em;
      text-transform: uppercase;
      font-weight: 700;
    }

    .date {
      color: var(--lavender);
      font-size: 1.15rem;
      margin: 20px auto 18px;
      font-weight: 600;
      letter-spacing: 0.03em;
    }

    .story {
      max-width: 640px;
      margin: 0 auto;
      color: var(--soft);
      font-size: 1.12rem;
      line-height: 1.9;
      font-family: "Trebuchet MS", "Segoe UI", sans-serif;
    }

    .story .highlight {
      color: var(--mint);
      font-weight: 700;
    }

    .story .heart {
      color: var(--pink);
      font-size: 1.5rem;
      display: inline-block;
      animation: pulse 1.2s infinite alternate;
    }

    @keyframes pulse {
      0% { transform: scale(1); }
      100% { transform: scale(1.2); }
    }

    .cta {
      margin-top: 28px;
      border: none;
      border-radius: 999px;
      padding: 16px 28px;
      font-size: 1rem;
      font-weight: 700;
      letter-spacing: 0.04em;
      cursor: pointer;
      color: #1a1025;
      background: linear-gradient(135deg, var(--pink), var(--gold));
      box-shadow: 0 10px 25px rgba(255, 126, 182, 0.35);
      transition: transform 0.2s ease, box-shadow 0.2s ease;
    }

    .cta:hover {
      transform: translateY(-2px) scale(1.02);
      box-shadow: 0 14px 30px rgba(255, 126, 182, 0.5);
    }

    .surprise {
      position: fixed;
      inset: 0;
      display: none;
      align-items: center;
      justify-content: center;
      background: rgba(5, 7, 12, 0.75);
      z-index: 5;
    }

    .surprise.show {
      display: flex;
    }

    .modal {
      width: min(92vw, 620px);
      background: linear-gradient(180deg, rgba(19, 22, 37, 0.96), rgba(11, 14, 22, 0.98));
      border: 1px solid rgba(255, 255, 255, 0.1);
      border-radius: 28px;
      padding: 30px 24px 20px;
      box-shadow: 0 25px 60px rgba(0, 0, 0, 0.45);
      position: relative;
      overflow: hidden;
    }

    .modal::before {
      content: "";
      position: absolute;
      width: 180px;
      height: 180px;
      border-radius: 50%;
      background: radial-gradient(circle, rgba(255, 126, 182, 0.25), transparent 70%);
      top: -50px;
      right: -30px;
    }

    .modal h2 {
      margin: 0 0 14px;
      color: var(--rose);
      text-align: center;
      font-size: clamp(2rem, 4vw, 3rem);
      font-family: Georgia, serif;
    }

    .modal p {
      text-align: center;
      color: var(--soft);
      font-size: 1.08rem;
      line-height: 1.7;
      margin: 0 0 20px;
    }

    .decision-box {
      position: relative;
      height: 180px;
      margin-top: 20px;
    }

    .yes-btn, .no-btn {
      position: absolute;
      border: none;
      border-radius: 999px;
      font-weight: 700;
      font-size: 1rem;
      letter-spacing: 0.04em;
      cursor: pointer;
      transition: transform 0.15s ease, box-shadow 0.15s ease;
    }

    .yes-btn {
      left: 50%;
      bottom: 18px;
      transform: translateX(-50%);
      padding: 14px 30px;
      background: linear-gradient(135deg, var(--mint), var(--lavender));
      color: #130d1e;
      box-shadow: 0 12px 30px rgba(142, 240, 211, 0.28);
    }

    .no-btn {
      right: 10%;
      top: 18px;
      padding: 12px 22px;
      background: linear-gradient(135deg, #ff9a9e, #fad0c4);
      color: #1d0d24;
      box-shadow: 0 12px 30px rgba(255, 154, 158, 0.24);
    }

    .yes-btn:hover, .no-btn:hover {
      transform: scale(1.04);
    }

    .message {
      min-height: 34px;
      margin-top: 18px;
      color: var(--gold);
      text-align: center;
      font-weight: 700;
      font-size: 1.05rem;
    }

    @media (max-width: 560px) {
      .container {
        padding: 26px 18px;
      }

      .story {
        font-size: 1rem;
      }

      .decision-box {
        height: 220px;
      }
    }
  </style>
</head>
<body>
  <div class="container">
    <div class="content">
      <h1 class="title">Our Love Story</h1>
      <div class="subtitle">Griffin & Terry</div>
      <div class="date">Started on 27 October 2026, Tuesday</div>

      <p class="story">
        From the first spark to the sweetest moments, my heart has always found its home in you.
        <span class="highlight">Terry</span>, you are the calm in my storms, the laughter in my chaos,
        and the softest dream I never want to wake from. <span class="heart">❤</span>
        <br><br>
        Every day with you feels like a beautiful chapter of a love story written by the stars.
        Your smile changes everything, your love makes everything brighter, and my soul feels
        safe with you. I want us to keep growing, laughing, and loving through every season of life.
      </p>

      <button class="cta" id="revealBtn">Open our little surprise</button>
    </div>
  </div>

  <div class="surprise" id="surprise">
    <div class="modal">
      <h2>Terry, my love</h2>
      <p>
        Will you be my forever and whenever?<br />
        My heart has chosen you, and I want to love you for all the days to come.
      </p>

      <div class="decision-box">
        <button class="yes-btn" id="yesBtn">Yes</button>
        <button class="no-btn" id="noBtn">No</button>
      </div>

      <div class="message" id="message"></div>
    </div>
  </div>

  <script>
    const revealBtn = document.getElementById("revealBtn");
    const surprise = document.getElementById("surprise");
    const yesBtn = document.getElementById("yesBtn");
    const noBtn = document.getElementById("noBtn");
    const message = document.getElementById("message");

    revealBtn.addEventListener("click", () => {
      surprise.classList.add("show");
    });

    const moveNoButton = () => {
      const box = document.querySelector(".decision-box");
      const boxRect = box.getBoundingClientRect();

      const maxX = boxRect.width - noBtn.offsetWidth - 20;
      const maxY = boxRect.height - noBtn.offsetHeight - 20;

      const x = Math.random() * maxX;
      const y = Math.random() * maxY;

      noBtn.style.left = `${x}px`;
      noBtn.style.top = `${y}px`;
      noBtn.style.right = "auto";
      noBtn.style.bottom = "auto";
    };

    noBtn.addEventListener("click", () => {
      message.textContent = "Aww, try again... my love still waits for you.";
      moveNoButton();
    });

    yesBtn.addEventListener("click", () => {
      noBtn.style.display = "none";
      yesBtn.style.left = "50%";
      yesBtn.style.bottom = "18px";
      yesBtn.style.transform = "translateX(-50%)";
      message.textContent = "You are my forever and whenever, Terry. I love you endlessly 💖";
      message.style.color = "#ffd166";
    });
  </script>
</body>
</html>
```
