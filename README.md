<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8">
<title>Ma Valentine 💖</title>
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
  font-family: Arial, sans-serif;
}

body {
  height: 100vh;
  background: linear-gradient(135deg, #ff9a9e, #fad0c4);
  display: flex;
  justify-content: center;
  align-items: center;
  overflow: hidden;
}

.container {
  text-align: center;
  color: #fff;
}

h1 {
  font-size: 2.5em;
  margin-bottom: 40px;
}

.buttons {
  position: relative;
  height: 100px;
}

button {
  padding: 15px 30px;
  font-size: 1.2em;
  border: none;
  border-radius: 30px;
  cursor: pointer;
}

#yes {
  background: #ff4d6d;
  color: white;
  margin-right: 20px;
  transition: transform 0.3s;
}

#no {
  background: #ffffff;
  color: #ff4d6d;
  position: absolute;
}

#final {
  display: none;
  animation: pop 1s ease forwards;
}

@keyframes pop {
  0% { transform: scale(0); opacity: 0; }
  100% { transform: scale(1); opacity: 1; }
}

.hearts {
  position: fixed;
  inset: 0;
  pointer-events: none;
}

.heart {
  position: absolute;
  font-size: 24px;
  animation: float 3s linear infinite;
}

@keyframes float {
  from { transform: translateY(100vh); opacity: 1; }
  to { transform: translateY(-10vh); opacity: 0; }
}
</style>
</head>

<body>

<div class="container" id="question">
  <h1>Veux-tu être ma Valentine ? 💘</h1>

  <div class="buttons">
    <button id="yes">OUI 💖</button>
    <button id="no">NON 🙈</button>
  </div>
</div>

<div class="container" id="final">
  <h1>J’ai tellement hâte de continuer avec toi 💞</h1>
  <p>Merci d’avoir dit oui 💖</p>
</div>

<div class="hearts" id="hearts"></div>

<script>
const noBtn = document.getElementById("no");
const yesBtn = document.getElementById("yes");
const question = document.getElementById("question");
const final = document.getElementById("final");
const hearts = document.getElementById("hearts");

noBtn.addEventListener("mouseover", () => {
  const x = Math.random() * (window.innerWidth - 100);
  const y = Math.random() * (window.innerHeight - 100);
  noBtn.style.left = x + "px";
  noBtn.style.top = y + "px";
});

yesBtn.addEventListener("click", () => {
  yesBtn.style.transform = "scale(1.5)";
  question.style.display = "none";
  final.style.display = "block";
  launchHearts();
});

function launchHearts() {
  for (let i = 0; i < 30; i++) {
    const heart = document.createElement("div");
    heart.className = "heart";
    heart.innerHTML = "💖";
    heart.style.left = Math.random() * 100 + "vw";
    heart.style.animationDuration = 2 + Math.random() * 3 + "s";
    hearts.appendChild(heart);
    setTimeout(() => heart.remove(), 5000);
  }
}
</script>

</body>
</html>
