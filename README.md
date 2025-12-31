<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Happy New Year Mussu</title>

<style>
@import url('https://fonts.googleapis.com/css2?family=Dancing+Script:wght@600&family=Poppins:wght@300;400&display=swap');

body, html {
    margin: 0;
    padding: 0;
    height: 100%;
    width: 100%;
    overflow: hidden;
    font-family: 'Poppins', sans-serif;
    color: white;
    background:
        linear-gradient(rgba(0,0,0,0.5), rgba(0,0,0,0.5)),
        url('https://drive.google.com/uc?export=view&id=1JfgM-nznj93lDvBeUKZQWIm4eHGkbLd9');
    background-size: cover;
    background-position: center;
}

.slide {
    height: 100vh;
    width: 100vw;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    text-align: center;
    position: absolute;
    opacity: 0;
    transform: scale(0.95);
    transition: 1s;
    pointer-events: none;
}

.active {
    opacity: 1;
    transform: scale(1);
    z-index: 5;
    pointer-events: auto;
}

h1 {
    font-family: 'Dancing Script', cursive;
    font-size: clamp(2rem, 8vw, 3.5rem);
    color: #ff4d6d;
    text-shadow: 2px 2px 10px black;
}

p {
    font-size: 1.2rem;
    max-width: 600px;
    text-shadow: 1px 1px 5px black;
}

.btn {
    margin-top: 30px;
    padding: 12px 25px;
    background: #ff4d6d;
    color: white;
    border: none;
    border-radius: 25px;
    cursor: pointer;
    transition: 0.3s;
}

.btn:hover { transform: scale(1.05); }

#music-control {
    position: fixed;
    bottom: 20px;
    right: 20px;
    background: rgba(255,77,109,0.9);
    border: none;
    border-radius: 50%;
    width: 45px;
    height: 45px;
    color: white;
    cursor: pointer;
    z-index: 20;
}

/* ❤️ Floating hearts */
.heart {
    position: fixed;
    font-size: 20px;
    animation: float 5s linear forwards;
    pointer-events: none;
}
@keyframes float {
    from { transform: translateY(110vh); opacity:1; }
    to { transform: translateY(-10vh); opacity:0; }
}

/* 🎆 Fireworks */
.firework {
    position: fixed;
    width: 6px;
    height: 6px;
    border-radius: 50%;
    animation: explode 1.2s ease-out forwards;
    pointer-events: none;
}

@keyframes explode {
    from { transform: scale(1); opacity: 1; }
    to { transform: scale(20); opacity: 0; }
}
</style>
</head>

<body>

<audio id="bgMusic" loop>
    <source src="PASTE_DIRECT_MP3_LINK_HERE" type="audio/mpeg">
</audio>

<button id="music-control" onclick="toggleMusic()">▶️</button>

<div class="slide active" id="slide1">
    <h1>Happy New Year my baccha mussu 🫂💗</h1>
    <p>A new chapter begins, and I'm so happy it's with you.</p>
    <button class="btn" onclick="startExperience()">Click here, Mussu</button>
</div>

<div class="slide" id="slide2">
    <h1>You Made My Year Better ✨</h1>
    <p>Your presence turned ordinary days into beautiful memories.</p>
    <button class="btn" onclick="nextSlide(3)">And one more thing...</button>
</div>

<div class="slide" id="slide3">
    <h1>Forever & Always ❤️</h1>
    <p>I want to be with you today, tomorrow, and every year after. 💍</p>
    <button class="btn" onclick="nextSlide(1)">Restart ❤️</button>
</div>

<script>
const music = document.getElementById("bgMusic");
const musicBtn = document.getElementById("music-control");

function startExperience(){
    music.play().catch(()=>{});
    musicBtn.innerHTML = "⏸️";
    nextSlide(2);
    launchFirework();
}

function nextSlide(n){
    document.querySelectorAll(".slide").forEach(s=>s.classList.remove("active"));
    document.getElementById("slide"+n).classList.add("active");
    launchFirework();
}

function toggleMusic(){
    if(music.paused){ music.play(); musicBtn.innerHTML="⏸️"; }
    else{ music.pause(); musicBtn.innerHTML="▶️"; }
}

/* ❤️ Hearts */
setInterval(()=>{
    const h=document.createElement("div");
    h.className="heart";
    h.innerHTML="❤️";
    h.style.left=Math.random()*100+"vw";
    document.body.appendChild(h);
    setTimeout(()=>h.remove(),5000);
},700);

/* 🎆 Fireworks */
function launchFirework(x=Math.random()*window.innerWidth, y=Math.random()*window.innerHeight/1.5){
    const f=document.createElement("div");
    f.className="firework";
    f.style.left=x+"px";
    f.style.top=y+"px";
    f.style.background=`hsl(${Math.random()*360},100%,60%)`;
    document.body.appendChild(f);
    setTimeout(()=>f.remove(),1200);
}

setInterval(launchFirework, 2000);
document.addEventListener("click", e => launchFirework(e.clientX, e.clientY));
</script>

</body>
</html>
