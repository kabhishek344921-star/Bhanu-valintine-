<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Bhanu 💖 My Valentine</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">

  <style>
    body {
      margin: 0;
      height: 100vh;
      background: linear-gradient(135deg, #ffd6e8, #ffffff);
      display: flex;
      justify-content: center;
      align-items: center;
      font-family: 'Segoe UI', sans-serif;
      overflow: hidden;
    }

    .container {
      background: white;
      padding: 35px;
      border-radius: 22px;
      text-align: center;
      box-shadow: 0 10px 30px rgba(255, 105, 180, 0.3);
      max-width: 90%;
      z-index: 2;
    }

    h1 {
      color: #ff4d88;
      margin-bottom: 5px;
    }

    h3 {
      color: #ff7aa8;
      margin-bottom: 25px;
    }

    .buttons {
      position: relative;
      height: 130px;
      margin-top: 20px;
    }

    button {
      padding: 15px 35px;
      font-size: 18px;
      border-radius: 30px;
      border: none;
      cursor: pointer;
      transition: 0.3s;
    }

    #yesBtn {
      background: #ff4d88;
      color: white;
    }

    #yesBtn:hover {
      background: #ff1f6a;
    }

    #noBtn {
      background: #cccccc;
      color: #333;
      position: absolute;
      left: 50%;
      transform: translateX(-50%);
    }

    #result {
      display: none;
      margin-top: 25px;
    }

    #result img {
      max-width: 260px;
      border-radius: 18px;
      margin-top: 15px;
    }

    /* Floating hearts */
    .heart {
      position: absolute;
      bottom: -20px;
      font-size: 24px;
      animation: float 6s linear infinite;
      opacity: 0.8;
    }

    @keyframes float {
      0% {
        transform: translateY(0) scale(1);
        opacity: 1;
      }
      100% {
        transform: translateY(-100vh) scale(1.5);
        opacity: 0;
      }
    }
  </style>
</head>
<body>

  <div class="container">
    <h1>Bhanu 💖</h1>
    <h3>Will you be my Valentine?</h3>

    <div class="buttons">
      <button id="yesBtn">Yes ❤️</button>
      <button id="noBtn">No 💔</button>
    </div>

    <div id="result">
      <h2>Good choice, Bhanu 😏💖</h2>
      <p id="typing"></p>
      <img src="https://i.imgflip.com/4/30b1gx.jpg" alt="Valentine Meme">
    </div>
  </div>

  <!-- Romantic Music -->
  <audio id="music" loop>
    <source src="https://www.bensound.com/bensound-music/bensound-love.mp3" type="audio/mpeg">
  </audio>

  <script>
    const noBtn = document.getElementById("noBtn");
    const yesBtn = document.getElementById("yesBtn");
    const result = document.getElementById("result");
    const music = document.getElementById("music");
    const typing = document.getElementById("typing");

    function moveButton() {
      const x = Math.random() * 240 - 120;
      const y = Math.random() * 100 - 50;
      noBtn.style.transform = `translate(${x}px, ${y}px)`;
    }

    noBtn.addEventListener("mouseover", moveButton);
    noBtn.addEventListener("touchstart", moveButton);

    yesBtn.addEventListener("click", () => {
      result.style.display = "block";
      yesBtn.style.display = "none";
      noBtn.style.display = "none";
      music.play();
      createHearts();
      startTyping();
    });

    const message =
      "You just made me the happiest person today.\n" +
      "Thank you for being my Valentine 💕\n\n" +
      "I love you, Bhanu ❤️";

    let index = 0;

    function startTyping() {
      typing.innerHTML = "";
      index = 0;
      const interval = setInterval(() => {
        typing.innerHTML += message[index] === "\n" ? "<br>" : message[index];
        index++;
        if (index >= message.length) clearInterval(interval);
      }, 60);
    }

    function createHearts() {
      setInterval(() => {
        const heart = document.createElement("div");
        heart.className = "heart";
        heart.innerHTML = "💖";
        heart.style.left = Math.random() * 100 + "vw";
        heart.style.animationDuration = Math.random() * 2 + 4 + "s";
        document.body.appendChild(heart);
        setTimeout(() => heart.remove(), 6000);
      }, 400);
    }
  </script>

</body>
</html>
