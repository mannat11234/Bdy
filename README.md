<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Happy Birthday Mumma! 🎉</title>
<link href="https://fonts.googleapis.com/css2?family=Great+Vibes&family=Poppins:wght@300;400;600&display=swap" rel="stylesheet">
<style>
body {
    margin:0;
    padding:0;
    font-family:'Poppins', sans-serif;
    display:flex;
    justify-content:center;
    align-items:center;
    height:100vh;
    flex-direction:column;
    text-align:center;
    overflow:hidden;
    color:#fff;
    background: linear-gradient(270deg,#ff9a9e,#fad0c4,#fbc2eb);
    background-size:600% 600%;
    animation: bgMove 15s ease infinite;
}
@keyframes bgMove {
    0%{background-position:0% 50%}
    50%{background-position:100% 50%}
    100%{background-position:0% 50%}
}

h1 {
    font-family:'Great Vibes', cursive;
    font-size:4rem;
    margin-bottom:20px;
    text-shadow: 2px 2px 10px #000;
}
#slideText {
    font-size:2rem;
    margin-bottom:30px;
    text-shadow:1px 1px 8px #000;
}

.confetti {
    position:absolute;
    font-size:1.2rem;
    animation:drop 6s linear infinite;
    opacity:0.8;
}
@keyframes drop {
    0% { transform: translateY(-10vh) rotate(0deg); }
    100% { transform: translateY(110vh) rotate(360deg); }
}

#finalSlide {
    position:fixed;
    inset:0;
    display:flex;
    align-items:center;
    justify-content:center;
    font-family:'Great Vibes', cursive;
    font-size:5rem;
    background:rgba(0,0,0,0.5);
    color:#fffc00;
    text-shadow:3px 3px 15px #ff0066;
    opacity:0;
    pointer-events:none;
    transition:opacity 2s ease;
    z-index:9999;
}
#finalSlide.show { opacity:1; }
</style>
</head>
<body>

<!-- Birthday Song -->
<audio id="birthdaySong" preload="auto">
    <source src="https://pagalfree.com/musics/128-Tu%20Chahiye%20-%20Bajrangi%20Bhaijaan%20128%20Kbps.mp3" type="audio/mpeg">
</audio>

<h1>Happy Birthday Mumma! 🎉</h1>
<div id="slideText"></div>
<div id="finalSlide">I LOVE YOU SO SO MUCH ❤️</div>

<script>
const slides = [
    "You are the most amazing Mom! 💖",
    "May your day be filled with smiles 😄",
    "You deserve endless happiness 🌟",
    "Sending all my love to you 💕",
    "Happy Birthday, Mom! 🎂❤️",
    "Enjoy every moment of your special day ✨"
];

const backgrounds = [
    "linear-gradient(135deg, #ffe6e6, #fff0f5)",
    "linear-gradient(135deg, #ffccff, #ff99cc)",
    "linear-gradient(135deg, #ffeb99, #ff9999)",
    "linear-gradient(135deg, #99ffcc, #66ff99)",
    "linear-gradient(135deg, #99ccff, #6699ff)"
];

const slideText = document.getElementById("slideText");
const birthdaySong = document.getElementById("birthdaySong");
const finalSlide = document.getElementById("finalSlide");

let slideIndex = 0;

// Start song automatically from 41 sec
birthdaySong.currentTime = 41;
birthdaySong.play();

// Create floating hearts/confetti continuously
function createConfetti() {
    const colors = ["💖","💜","💛","💚","✨","🎉","❤️"];
    let conf = document.createElement("div");
    conf.className = "confetti";
    conf.style.left = Math.random()*100+"vw";
    conf.style.fontSize = Math.random()*30+20+"px";
    conf.innerText = colors[Math.floor(Math.random()*colors.length)];
    document.body.appendChild(conf);
    setTimeout(()=>conf.remove(),6000);
}
setInterval(createConfetti,200);

// Automatic slides with background change
function showSlide() {
    if(slideIndex < slides.length){
        slideText.innerText = slides[slideIndex];
        document.body.style.background = backgrounds[Math.floor(Math.random()*backgrounds.length)];
        slideIndex++;
        setTimeout(showSlide,3500); // next slide after 3.5s
    } else {
        // Show final slide
        slideText.innerText = "";
        finalSlide.classList.add("show");
    }
}

// Start the slides automatically
showSlide();
</script>

</body>
</html>
