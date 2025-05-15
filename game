<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <title>Catch the Falling Objects</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no" />
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      touch-action: manipulation;
    }
    body {
      background: linear-gradient(to bottom, #0f2027, #203a43, #2c5364);
      font-family: 'Arial', sans-serif;
      color: white;
      display: flex;
      flex-direction: column;
      align-items: center;
      height: 100vh;
      overflow: hidden;
    }
    h1 {
      margin: 20px;
      font-size: 1.8rem;
      text-align: center;
    }
    #game {
      position: relative;
      width: 90%;
      max-width: 400px;
      height: 500px;
      background: #333;
      border: 4px solid #222;
      border-radius: 12px;
      overflow: hidden;
    }
    #basket {
      position: absolute;
      bottom: 10px;
      width: 20%;
      height: 25px;
      background: #00bcd4;
      border-radius: 10px;
      transition: all 0.1s ease;
      box-shadow: 0 0 10px rgba(0, 188, 212, 0.7);
    }
    .object {
      position: absolute;
      width: 25px;
      height: 25px;
      border-radius: 50%;
      animation: fall linear forwards;
      z-index: 10;
    }
    .apple {
      background: #ff5252;
      box-shadow: 0 0 10px #ff5252;
    }
    .orange {
      background: #ff9800;
      box-shadow: 0 0 10px #ff9800;
    }
    .banana {
      background: #ffeb3b;
      box-shadow: 0 0 10px #ffeb3b;
      border-radius: 50% 50% 30% 30%;
    }
    .bomb {
      background: #333;
      box-shadow: 0 0 10px #ff0000;
      border-radius: 30% 30% 50% 50%;
    }
    .diamond {
      background: #00bcd4;
      box-shadow: 0 0 15px #00bcd4;
      border-radius: 50%;
      transform: rotate(45deg);
    }
    #game-info {
      display: flex;
      justify-content: space-between;
      width: 90%;
      max-width: 400px;
      margin-bottom: 10px;
    }
    #score, #level, #lives {
      font-size: 18px;
      font-weight: bold;
    }
    #controls {
      display: flex;
      gap: 10px;
      margin-top: 10px;
    }
    .game-btn {
      padding: 10px 20px;
      font-size: 16px;
      border: none;
      border-radius: 8px;
      color: white;
      cursor: pointer;
      box-shadow: 0 4px 10px rgba(0,0,0,0.3);
      transition: all 0.2s;
    }
    .game-btn:hover {
      transform: translateY(-2px);
    }
    #startBtn {
      background: #4caf50;
    }
    #startBtn:hover {
      background: #388e3c;
    }
    #pauseBtn {
      background: #ff9800;
    }
    #pauseBtn:hover {
      background: #f57c00;
    }
    .touch-controls {
      display: flex;
      justify-content: space-around;
      margin-top: 15px;
      width: 100%;
      max-width: 400px;
    }
    .touch-btn {
      padding: 15px 25px;
      font-size: 20px;
      background: #ff5722;
      color: white;
      border: none;
      border-radius: 10px;
      cursor: pointer;
      user-select: none;
      -webkit-user-select: none;
    }
    .touch-btn:active {
      transform: scale(0.95);
    }
    #game-over {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: rgba(0, 0, 0, 0.8);
      display: none;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      z-index: 100;
    }
    #game-over h2 {
      font-size: 2.5rem;
      color: #ff5252;
      margin-bottom: 20px;
    }
    #final-score, #high-score {
      font-size: 1.5rem;
      margin: 10px 0;
    }
    #restartBtn {
      margin-top: 20px;
      padding: 15px 30px;
      font-size: 1.2rem;
      background: #4caf50;
      border: none;
      border-radius: 10px;
      color: white;
      cursor: pointer;
    }
    .creator {
      color: white;
      border: 5px solid #0af;
      padding: 5px;
      margin-top: 15px;
      text-align: center;
    }
    .particle {
      position: absolute;
      width: 10px;
      height: 10px;
      border-radius: 50%;
      pointer-events: none;
      z-index: 5;
    }
    #musicControls {
      margin-top: 10px;
    }
    #musicToggle {
      padding: 8px 15px;
      background: #9c27b0;
      color: white;
      border: none;
      border-radius: 5px;
      cursor: pointer;
    }
  </style>
</head>
<body>
  <h1>🍎 Catch the Falling Objects</h1>
  <div id="game-info">
    <div id="score">Score: 0</div>
    <div id="level">Level: 1</div>
    <div id="lives">Lives: ❤️❤️❤️</div>
  </div>
  <div id="game">
    <div id="basket"></div>
    <div id="game-over">
      <h2>GAME OVER</h2>
      <div id="final-score">Final Score: 0</div>
      <div id="high-score">High Score: 0</div>
      <button id="restartBtn">Play Again</button>
    </div>
  </div>
  <div id="controls">
    <button id="startBtn" class="game-btn">Start Game</button>
    <button id="pauseBtn" class="game-btn">Pause</button>
  </div>
  <div class="touch-controls">
    <button class="touch-btn" id="leftBtn">◀️ Left</button>
    <button class="touch-btn" id="rightBtn">▶️ Right</button>
  </div>
  <div id="musicControls">
    <button id="musicToggle">🎵 Pause Music</button>
  </div>
  <div class="creator">
    Created by: <b>TEMESGEN ZELALEM</b>
  </div>

  <!-- Sound Effects -->
  <audio id="catchSound" src="https://assets.mixkit.co/sfx/preview/mixkit-arcade-game-jump-coin-216.mp3 " preload="auto"></audio>
  <audio id="bombSound" src="https://assets.mixkit.co/sfx/preview/mixkit-explosion-impact-1684.mp3 " preload="auto"></audio>
  <audio id="levelUpSound" src="https://assets.mixkit.co/sfx/preview/mixkit-unlock-game-notification-253.mp3 " preload="auto"></audio>
  <audio id="gameOverSound" src="https://assets.mixkit.co/sfx/preview/mixkit-retro-arcade-lose-2027.mp3 " preload="auto"></audio>
  <audio id="bgMusic" loop>
    <source src="Alan.mp3" type="audio/mp3">
    Your browser does not support the audio element.
  </audio>

  <script>
    const game = document.getElementById("game");
    const basket = document.getElementById("basket");
    const scoreDisplay = document.getElementById("score");
    const levelDisplay = document.getElementById("level");
    const livesDisplay = document.getElementById("lives");
    const startBtn = document.getElementById("startBtn");
    const pauseBtn = document.getElementById("pauseBtn");
    const leftBtn = document.getElementById("leftBtn");
    const rightBtn = document.getElementById("rightBtn");
    const gameOverScreen = document.getElementById("game-over");
    const finalScoreDisplay = document.getElementById("final-score");
    const highScoreDisplay = document.getElementById("high-score");
    const restartBtn = document.getElementById("restartBtn");
    const musicToggle = document.getElementById("musicToggle");
    const bgMusic = document.getElementById("bgMusic");

    // Sound effects
    const catchSound = document.getElementById("catchSound");
    const bombSound = document.getElementById("bombSound");
    const levelUpSound = document.getElementById("levelUpSound");
    const gameOverSound = document.getElementById("gameOverSound");

    let basketX = 40;
    let score = 0;
    let level = 1;
    let lives = 3;
    let highScore = localStorage.getItem('highScore') || 0;
    let fallingObjects = [];
    let fallInterval;
    let gameLoop;
    let gameRunning = false;
    let gamePaused = false;
    let musicPlaying = false;
    let leftPressed = false;
    let rightPressed = false;

    const objectTypes = [
      { class: 'apple', points: 10, speed: 1.5, spawnRate: 0.4 },
      { class: 'orange', points: 20, speed: 2, spawnRate: 0.3 },
      { class: 'banana', points: 30, speed: 2.5, spawnRate: 0.2 },
      { class: 'diamond', points: 50, speed: 3, spawnRate: 0.1 },
      { class: 'bomb', points: -1, speed: 2.5, spawnRate: 0.2 }
    ];

    function setBasketPosition() {
      basket.style.left = basketX + "%";
    }

    function createParticles(x, y, color, count = 10) {
      for (let i = 0; i < count; i++) {
        const particle = document.createElement("div");
        particle.className = "particle";
        particle.style.background = color;
        particle.style.left = x + "px";
        particle.style.top = y + "px";
        game.appendChild(particle);

        const angle = Math.random() * Math.PI * 2;
        const speed = Math.random() * 5 + 2;
        const lifetime = Math.random() * 1000 + 500;
        const vx = Math.cos(angle) * speed;
        const vy = Math.sin(angle) * speed;
        let startTime = Date.now();

        function updateParticle() {
          const elapsed = Date.now() - startTime;
          const progress = elapsed / lifetime;
          if (progress >= 1) {
            if (particle.parentNode) game.removeChild(particle);
            return;
          }
          particle.style.transform = `translate(${vx * progress * 50}px, ${vy * progress * 50}px)`;
          particle.style.opacity = 1 - progress;
          requestAnimationFrame(updateParticle);
        }
        requestAnimationFrame(updateParticle);
      }
    }

    function createObject() {
      if (!gameRunning || gamePaused) return;
      const obj = document.createElement("div");
      const totalSpawnRate = objectTypes.reduce((sum, type) => sum + type.spawnRate, 0);
      let random = Math.random() * totalSpawnRate;
      let selectedType;
      for (const type of objectTypes) {
        if (random < type.spawnRate) {
          selectedType = type;
          break;
        }
        random -= type.spawnRate;
      }
      obj.className = `object ${selectedType.class}`;
      obj.style.left = Math.random() * 90 + "%";
      obj.style.top = "0px";
      const fallSpeed = selectedType.speed * (1 + level * 0.05);
      obj.style.animationDuration = `${5/fallSpeed}s`;
      obj.dataset.points = selectedType.points;
      obj.dataset.type = selectedType.class;
      game.appendChild(obj);
      fallingObjects.push(obj);
    }

    function updateObjects() {
      const gameRect = game.getBoundingClientRect();
      const basketRect = basket.getBoundingClientRect();

      for (let i = fallingObjects.length - 1; i >= 0; i--) {
        const obj = fallingObjects[i];
        const rect = obj.getBoundingClientRect();

        const objXPercent = ((rect.left - gameRect.left) / gameRect.width) * 100;
        const objWidthPercent = (rect.width / gameRect.width) * 100;
        const objYPercent = ((rect.top - gameRect.top) / gameRect.height) * 100;
        const basketWidthPercent = (basketRect.width / gameRect.width) * 100;

        const isCaught = (
          objYPercent >= 90 &&
          objXPercent + objWidthPercent >= basketX &&
          objXPercent <= basketX + basketWidthPercent
        );

        const isOutOfBounds = rect.top >= gameRect.top + gameRect.height;

        if (isCaught) {
          const points = parseInt(obj.dataset.points);
          const type = obj.dataset.type;
          if (type === 'bomb') {
            bombSound.currentTime = 0;
            bombSound.play();
            lives--;
            updateLivesDisplay();
            if (lives <= 0) {
              gameOver();
              return;
            }
            createParticles(
              rect.left - gameRect.left + rect.width / 2,
              rect.top - gameRect.top,
              '#ff0000',
              20
            );
          } else {
            catchSound.currentTime = 0;
            catchSound.play();
            score += points;
            scoreDisplay.textContent = `Score: ${score}`;
            createParticles(
              rect.left - gameRect.left + rect.width / 2,
              rect.top - gameRect.top,
              getComputedStyle(obj).background,
              15
            );
          }
          if (obj.parentNode) game.removeChild(obj);
          fallingObjects.splice(i, 1);
          if (score >= level * 100) {
            levelUp();
          }
        } else if (isOutOfBounds) {
          if (obj.dataset.type !== 'bomb') {
            lives--;
            updateLivesDisplay();
            if (lives <= 0) {
              gameOver();
              return;
            }
          }
          if (obj.parentNode) game.removeChild(obj);
          fallingObjects.splice(i, 1);
        }
      }
    }

    function updateLivesDisplay() {
      livesDisplay.textContent = "Lives: " + "❤️".repeat(Math.max(0, lives));
    }

    function levelUp() {
      level++;
      levelDisplay.textContent = `Level: ${level}`;
      levelUpSound.currentTime = 0;
      levelUpSound.play();
      clearInterval(fallInterval);
      fallInterval = setInterval(createObject, Math.max(500, 1000 - level * 30));
      levelDisplay.style.transform = "scale(1.5)";
      levelDisplay.style.color = "#00ff00";
      setTimeout(() => {
        levelDisplay.style.transform = "scale(1)";
        levelDisplay.style.color = "white";
      }, 500);
    }

    function moveBasket() {
      const moveSpeed = 0.8 + level * 0.1;
      if (leftPressed && basketX > 0) basketX -= moveSpeed;
      if (rightPressed && basketX < 80) basketX += moveSpeed;
      setBasketPosition();
    }

    function resumeMusicOnFirstInteraction() {
      const playPromise = bgMusic.play();
      if (playPromise !== undefined) {
        playPromise.catch(() => {});
      }
    }

    function startGame() {
      score = 0;
      level = 1;
      lives = 3;
      basketX = 40;
      setBasketPosition();
      scoreDisplay.textContent = "Score: 0";
      levelDisplay.textContent = "Level: 1";
      updateLivesDisplay();
      gameRunning = true;
      gamePaused = false;
      gameOverScreen.style.display = "none";
      startBtn.textContent = "Restart";
      pauseBtn.style.display = "block";

      fallingObjects.forEach(obj => {
        if (obj.parentNode) game.removeChild(obj);
      });
      fallingObjects = [];

      clearInterval(fallInterval);
      cancelAnimationFrame(gameLoop);

      fallInterval = setInterval(createObject, 1000);

      function loop() {
        if (gameRunning && !gamePaused) {
          moveBasket();
          updateObjects();
          gameLoop = requestAnimationFrame(loop);
        }
      }
      loop();

      resumeMusicOnFirstInteraction(); // Resume on first tap
    }

    function pauseGame() {
      gamePaused = !gamePaused;
      pauseBtn.textContent = gamePaused ? "Resume" : "Pause";
      if (gamePaused) {
        fallingObjects.forEach(obj => {
          obj.style.animationPlayState = 'paused';
        });
      } else {
        fallingObjects.forEach(obj => {
          obj.style.animationPlayState = 'running';
        });
        function loop() {
          if (gameRunning && !gamePaused) {
            moveBasket();
            updateObjects();
            gameLoop = requestAnimationFrame(loop);
          }
        }
        loop();
      }
    }

    function gameOver() {
      gameRunning = false;
      clearInterval(fallInterval);
      cancelAnimationFrame(gameLoop);
      if (score > highScore) {
        highScore = score;
        localStorage.setItem('highScore', highScore);
      }
      finalScoreDisplay.textContent = `Final Score: ${score}`;
      highScoreDisplay.textContent = `High Score: ${highScore}`;
      gameOverScreen.style.display = "flex";
      gameOverSound.currentTime = 0;
      gameOverSound.play();
    }

    function toggleMusic() {
      if (musicPlaying) {
        bgMusic.pause();
        musicToggle.textContent = "🎵 Play Music";
      } else {
        bgMusic.play().catch(() => {});
        musicToggle.textContent = "🎵 Pause Music";
      }
      musicPlaying = !musicPlaying;
    }

    // Ensure music starts after user interaction
    [startBtn, pauseBtn, leftBtn, rightBtn, restartBtn, musicToggle].forEach(btn => {
      btn.addEventListener("touchstart", resumeMusicOnFirstInteraction, { once: true });
    });

    // Keyboard Controls
    document.addEventListener("keydown", (e) => {
      if (e.code === "ArrowLeft") leftPressed = true;
      if (e.code === "ArrowRight") rightPressed = true;
      if (e.code === "Space" && gameRunning) pauseGame();
    });

    document.addEventListener("keyup", (e) => {
      if (e.code === "ArrowLeft") leftPressed = false;
      if (e.code === "ArrowRight") rightPressed = false;
    });

    // Touch & Mouse Controls
    leftBtn.addEventListener("touchstart", (e) => {
      e.preventDefault();
      leftPressed = true;
    });
    leftBtn.addEventListener("touchend", () => leftPressed = false);
    rightBtn.addEventListener("touchstart", (e) => {
      e.preventDefault();
      rightPressed = true;
    });
    rightBtn.addEventListener("touchend", () => rightPressed = false);

    // Button Click Events
    startBtn.addEventListener("click", startGame);
    pauseBtn.addEventListener("click", pauseGame);
    restartBtn.addEventListener("click", startGame);
    musicToggle.addEventListener("click", toggleMusic);

    pauseBtn.style.display = "none";

    // Animation Keyframes
    const style = document.createElement('style');
    style.textContent = `
      @keyframes fall {
        from { transform: translateY(0); }
        to { transform: translateY(500px); }
      }
    `;
    document.head.appendChild(style);
  </script>
</body>
</html>