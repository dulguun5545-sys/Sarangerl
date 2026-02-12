<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Will You Be My Valentine?</title>

  <style>
    body {
      margin: 0;
      font-family: Arial, sans-serif;
      background: linear-gradient(135deg, #ff9acb, #ffc0da);
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      overflow: hidden;
    }

    .container {
      text-align: center;
      background: rgba(255,255,255,0.9);
      padding: 30px;
      border-radius: 20px;
      box-shadow: 0 0 20px rgba(0,0,0,0.2);
      width: 350px;
      z-index: 2;
    }

    h1 {
      color: #ff2f92;
      margin-bottom: 20px;
    }

    button {
      font-size: 18px;
      padding: 12px 25px;
      margin: 10px;
      border: none;
      border-radius: 12px;
      cursor: pointer;
      transition: 0.2s;
    }

    #yesBtn {
      background: #ff4da6;
      color: white;
    }

    #noBtn {
      background: #777;
      color: white;
    }

    #tryBtn {
      background: #ff4da6;
      color: white;
    }

    button:hover {
      transform: scale(1.1);
    }

    .heart {
      position: fixed;
      bottom: -20px;
      font-size: 20px;
      animation: floatUp linear infinite;
      opacity: 0.8;
      z-index: 1;
    }

    @keyframes floatUp {
      from { transform: translateY(0); opacity: 1; }
      to { transform: translateY(-100vh); opacity: 0; }
    }

    .boom {
      position: fixed;
      font-size: 30px;
      animation: explode 1s forwards;
      pointer-events: none;
      z-index: 5;
    }

    @keyframes explode {
      from {
        transform: scale(1);
        opacity: 1;
      }
      to {
        transform: scale(2) translate(var(--x), var(--y));
        opacity: 0;
      }
    }
  </style>
</head>

<body>

  <!-- Cupid Song -->
  <audio autoplay loop>
    <source src="https://www.dropbox.com/scl/fi/0knhtf1x5opqzgj6v6b6b/cupid.mp3?rlkey=tc4s6v9ql9jv88ib3x9tfm4o1&raw=1" type="audio/mpeg">
  </audio>

  <div class="container">
    <h1 id="text">Will you be my Valentine? 💕</h1>

    <div id="buttons">
      <button id="yesBtn" onclick="yesClick()">Yes 💘</button>
      <button id="noBtn" onclick="noClick()">No 💔</button>
    </div>
  </div>

  <script>
    function yesClick() {
      document.getElementById("text").innerHTML =
        "Thank you for being my first Valentine 💖";
      document.getElementById("buttons").innerHTML = "";

      heartExplosion();
    }

    function noClick() {
      document.getElementById("text").innerHTML =
        "Why? 😢 Try again 💕";

      document.getElementById("buttons").innerHTML =
        '<button id="tryBtn" onclick="reset()">Try Again 🔄</button>';
    }

    function reset() {
      document.getElementById("text").innerHTML =
        "Will you be my Valentine? 💕";

      document.getElementById("buttons").innerHTML =
        '<button id="yesBtn" onclick="yesClick()">Yes 💘</button>' +
        '<button id="noBtn" onclick="noClick()">No 💔</button>';
    }

    function createHeart() {
      const heart = document.createElement("div");
      heart.className = "heart";
      heart.innerHTML = "💖";

      heart.style.left = Math.random() * 100 + "vw";
      heart.style.animationDuration = (2 + Math.random() * 3) + "s";

      document.body.appendChild(heart);

      setTimeout(() => {
        heart.remove();
      }, 5000);
    }

    setInterval(createHeart, 300);

    function heartExplosion() {
      for (let i = 0; i < 40; i++) {
        const boom = document.createElement("div");
        boom.className = "boom";
        boom.innerHTML = "💖";

        boom.style.left = "50%";
        boom.style.top = "50%";

        boom.style.setProperty("--x", (Math.random()*400 - 200) + "px");
        boom.style.setProperty("--y", (Math.random()*400 - 200) + "px");

        document.body.appendChild(boom);

        setTimeout(() => {
          boom.remove();
        }, 1000);
      }
    }
  </script>

</body>
</html>
/mysite
