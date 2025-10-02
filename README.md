# ZAKIR45
THE WORLD GAME FASTEST  GAMING 
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Fast Reaction Game</title>
  <style>
    body {
      text-align: center;
      font-family: Arial, sans-serif;
      background-color: #111;
      color: #fff;
    }
    #gameBox {
      margin-top: 100px;
    }
    #btn {
      padding: 20px 40px;
      font-size: 24px;
      background-color: red;
      color: white;
      border: none;
      cursor: not-allowed;
      border-radius: 10px;
      transition: background-color 0.3s;
    }
    #btn.active {
      background-color: green;
      cursor: pointer;
    }
    #result {
      margin-top: 30px;
      font-size: 24px;
    }
  </style>
</head>
<body>
  <div id="gameBox">
    <h1>🎯 Reaction Speed Game</h1>
    <p>Click the button as soon as it turns <span style="color:lime">green</span>.</p>
    <button id="btn" disabled>Wait for Green...</button>
    <div id="result"></div>
  </div>

  <script>
    const button = document.getElementById("btn");
    const result = document.getElementById("result");
    let startTime, timeout;

    function startGame() {
      button.disabled = true;
      button.classList.remove("active");
      button.textContent = "Wait for Green...";
      result.textContent = "";

      const randomTime = Math.floor(Math.random() * 3000) + 2000; // 2-5 sec

      timeout = setTimeout(() => {
        button.classList.add("active");
        button.disabled = false;
        button.textContent = "CLICK!";
        startTime = Date.now();
      }, randomTime);
    }

    button.addEventListener("click", () => {
      if (!button.classList.contains("active")) {
        result.textContent = "⛔ Too Soon! Wait for Green!";
        clearTimeout(timeout);
        startGame();
      } else {
        const reactionTime = Date.now() - startTime;
        result.textContent = `⚡ Your Reaction Time: ${reactionTime} ms`;
        startGame();
      }
    });

    // Start the game initially
    startGame();
  </script>
</body>
</html>
