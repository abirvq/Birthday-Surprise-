
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Birthday Surprise 🎀</title>

<style>
* {
  box-sizing: border-box;
}

body {
  margin: 0;
  font-family: "Trebuchet MS", sans-serif;
  overflow: hidden;
  text-align: center;
  background: #fff0f5;
  color: #8b4267;
}

.screen {
  position: fixed;
  inset: 0;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding: 20px;
  overflow: hidden;
  transition: opacity 0.8s ease;
}

.hidden {
  display: none !important;
}

/* FLOWER SCREEN */
#flowerScreen {
  background: linear-gradient(135deg, #fff0f6, #ffd6e7, #fff7fa);
}

.flower {
  font-size: clamp(40px, 12vw, 75px);
  animation: flowerFloat 3s ease-in-out infinite;
  filter: drop-shadow(0 5px 10px #e99bb9);
}

.flower:nth-child(even) {
  animation-delay: -1.5s;
}

.flowerGarden {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 12px;
  max-width: 350px;
  margin-bottom: 20px;
}

h1 {
  font-size: clamp(27px, 7vw, 42px);
  margin: 12px 0;
}

p {
  font-size: 17px;
  line-height: 1.6;
}

button {
  border: none;
  border-radius: 30px;
  padding: 14px 28px;
  margin: 10px;
  font-size: 17px;
  font-weight: bold;
  cursor: pointer;
  box-shadow: 0 5px 15px #c86d9840;
  transition: transform 0.2s;
}

button:active {
  transform: scale(0.94);
}

.primary {
  background: #f28bb5;
  color: white;
}

.secondary {
  background: white;
  color: #d45b91;
}

@keyframes flowerFloat {
  0%, 100% { transform: translateY(0) rotate(-5deg); }
  50% { transform: translateY(-12px) rotate(5deg); }
}

/* QUESTION SCREEN */
#questionScreen {
  background: linear-gradient(145deg, #ffe4ef, #fff4f8);
}

.heart {
  font-size: 75px;
  animation: heartbeat 1.5s infinite;
}

@keyframes heartbeat {
  0%, 100% { transform: scale(1); }
  50% { transform: scale(1.12); }
}

.buttons {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 8px;
}

#noMessage {
  min-height: 30px;
  color: #bb5683;
}

/* SURPRISE SCREEN */
#surpriseScreen {
  background: linear-gradient(to bottom, #ffe5f0, #ffd0e4);
}

#balloonArea {
  position: absolute;
  inset: 0;
  overflow: hidden;
  pointer-events: none;
}

.balloon {
  position: absolute;
  bottom: -130px;
  font-size: clamp(35px, 9vw, 58px);
  animation: rise linear forwards;
  filter: drop-shadow(0 5px 4px #c8759b40);
}

@keyframes rise {
  0% {
    transform: translateY(0) rotate(-8deg);
    opacity: 0;
  }
  10% { opacity: 1; }
  50% { transform: translateY(-55vh) rotate(10deg); }
  100% {
    transform: translateY(-125vh) rotate(-12deg);
    opacity: 0.8;
  }
}

.surpriseContent {
  position: relative;
  z-index: 2;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  width: 100%;
  min-height: 100%;
}

#teddy {
  font-size: clamp(100px, 28vw, 155px);
  opacity: 0;
  transform: scale(0.2) translateY(30px);
  transition: all 1.2s cubic-bezier(.2, 1.5, .4, 1);
  filter: drop-shadow(0 12px 12px #b85b8840);
}

#teddy.show {
  opacity: 1;
  transform: scale(1) translateY(0);
}

#birthdayText {
  opacity: 0;
  transform: translateY(20px);
  transition: all 1s ease;
}

#birthdayText.show {
  opacity: 1;
  transform: translateY(0);
}

#birthdayText h1 {
  color: #d84d8a;
  text-shadow: 0 3px 12px #ffffff;
}

#birthdayText p {
  color: #a94b77;
}

#nameInput {
  width: min(260px, 85vw);
  padding: 13px 16px;
  border: 2px solid #f4a2c3;
  border-radius: 25px;
  font-size: 16px;
  text-align: center;
  outline: none;
  margin: 10px 0;
  background: #fffafd;
  color: #8b4267;
}

#replay {
  display: none;
}
</style>
</head>

<body>

<!-- SCREEN 1: FLOWERS -->
<section id="flowerScreen" class="screen">
  <div class="flowerGarden">
    <span class="flower">🌸</span>
    <span class="flower">🌷</span>
    <span class="flower">🌼</span>
    <span class="flower">🌹</span>
    <span class="flower">🌸</span>
    <span class="flower">🌺</span>
  </div>

  <h1>A Little Gift For You 💗</h1>
  <p>Someone has prepared something special...</p>
  <button class="primary" onclick="openQuestion()">
    Open Your Gift 🌷
  </button>
</section>

<!-- SCREEN 2: QUESTION -->
<section id="questionScreen" class="screen hidden">
  <div class="heart">💌</div>

  <h1>Wanna see surprise?</h1>
  <p>I made something cute just for you! 🎀</p>

  <div class="buttons">
    <button class="primary" onclick="startSurprise()">
      YES 💗
    </button>

    <button class="secondary" onclick="sayNo()">
      NO 🥺
    </button>
  </div>

  <p id="noMessage"></p>
</section>

<!-- SCREEN 3: BALLOONS AND TEDDY -->
<section id="surpriseScreen" class="screen hidden">
  <div id="balloonArea"></div>

  <div class="surpriseContent">
    <div id="introText">
      <h1>Here Comes Your Surprise! 🎈</h1>
      <p>Get ready for a little happiness...</p>
    </div>

    <div id="teddy">🧸🎈</div>

    <div id="birthdayText">
      <h1>Happy Birthday! 🎂</h1>
      <p>May your life always be filled with love,</p>
      <p>happiness, flowers and beautiful moments! 💖</p>

      <button class="primary" onclick="replaySurprise()">
        Replay Surprise 🎀
      </button>
    </div>
  </div>
</section>

<script>
const flowerScreen = document.getElementById("flowerScreen");
const questionScreen = document.getElementById("questionScreen");
const surpriseScreen = document.getElementById("surpriseScreen");
const balloonArea = document.getElementById("balloonArea");
const teddy = document.getElementById("teddy");
const birthdayText = document.getElementById("birthdayText");
const introText = document.getElementById("introText");

let balloonTimer;
let finalTimer;

function showScreen(screen) {
  flowerScreen.classList.add("hidden");
  questionScreen.classList.add("hidden");
  surpriseScreen.classList.add("hidden");

  screen.classList.remove("hidden");
}

function openQuestion() {
  showScreen(questionScreen);
}

function sayNo() {
  document.getElementById("noMessage").textContent =
    "Aww 🥺 Maybe a little surprise will make you smile? 💗";
}

function createBalloon() {
  const balloon = document.createElement("span");
  balloon.className = "balloon";

  const balloons = ["🎈", "🎈", "💗", "🎈", "💖"];
  balloon.textContent =
    balloons[Math.floor(Math.random() * balloons.length)];

  balloon.style.left = Math.random() * 92 + "%";
  balloon.style.animationDuration = (5 + Math.random() * 5) + "s";
  balloon.style.animationDelay = (Math.random() * 1.5) + "s";

  balloonArea.appendChild(balloon);

  balloon.addEventListener("animationend", () => {
    balloon.remove();
  });
}

function startSurprise() {
  showScreen(surpriseScreen);

  balloonArea.innerHTML = "";
  teddy.classList.remove("show");
  birthdayText.classList.remove("show");
  introText.style.display = "block";

  clearInterval(balloonTimer);
  clearTimeout(finalTimer);

  // Balloons slowly float upward
  for (let i = 0; i < 12; i++) {
    setTimeout(createBalloon, i * 220);
  }

  balloonTimer = setInterval(createBalloon, 380);

  // Teddy appears after the balloon animation begins
  finalTimer = setTimeout(() => {
    clearInterval(balloonTimer);

    introText.style.display = "none";
    teddy.classList.add("show");

    setTimeout(() => {
      birthdayText.classList.add("show");
    }, 900);
  }, 6500);
}

function replaySurprise() {
  startSurprise();
}
</script>

</body>
</html>
