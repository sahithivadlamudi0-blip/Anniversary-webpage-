# Anniversary-webpage-

<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta http-equiv="X-UA-Compatible" content="IE=edge">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Two Years | Sahithi & Sai</title>

<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:wght@400;600&family=Montserrat:wght@300;400&display=swap" rel="stylesheet">

<style>
:root{
--primary:#8e1b1b;
--bg:#fdfcfb;
--glass:rgba(255,255,255,0.85);
}
*{margin:0;padding:0;box-sizing:border-box;}
html{scroll-behavior:smooth;}
body{
background:var(--bg);
font-family:'Montserrat',sans-serif;
overflow-x:hidden;
color:#333;
}

/* LOCK SCREEN */
#lock-screen{
position:fixed;
inset:0;
background:linear-gradient(135deg,#fdfcfb,#f5e6e6);
display:flex;
flex-direction:column;
justify-content:center;
align-items:center;
z-index:9999;
transition:opacity 1.5s ease;
}

.lock-box{
border:1px solid var(--primary);
padding:40px;
text-align:center;
}

.unlock-btn{
margin-top:25px;
padding:15px 40px;
border:1px solid var(--primary);
background:transparent;
color:var(--primary);
letter-spacing:4px;
cursor:pointer;
transition:0.4s;
}

.unlock-btn:hover{
background:var(--primary);
color:#fff;
}

/* MAIN */
#main{
opacity:0;
transition:opacity 2s ease;
max-width:850px;
margin:auto;
padding:100px 20px;
}

.hero{
text-align:center;
margin-bottom:80px;
}

.hero h1{
font-family:'Cormorant Garamond',serif;
font-size:clamp(2.5rem,7vw,4rem);
color:var(--primary);
}

.sub{
letter-spacing:6px;
font-size:0.8rem;
color:#999;
margin-top:10px;
}

.section{
margin-bottom:130px;
opacity:0;
transform:translateY(40px);
transition:all 1.2s ease;
}

.section.visible{
opacity:1;
transform:translateY(0);
}

.card{
background:var(--glass);
backdrop-filter:blur(10px);
padding:40px;
border-radius:6px;
font-family:'Cormorant Garamond',serif;
font-size:1.3rem;
line-height:2;
box-shadow:0 20px 50px rgba(0,0,0,0.05);
margin-bottom:40px;
}

.img-box{
overflow:hidden;
border-radius:6px;
box-shadow:0 30px 60px rgba(0,0,0,0.08);
}

.img-box img{
width:100%;
display:block;
transition:transform 1s ease;
}

.img-box:hover img{
transform:scale(1.05);
}

/* ROSE */
.rose{
position:fixed;
top:-10%;
pointer-events:none;
animation:fall linear forwards;
}
@keyframes fall{
to{transform:translateY(110vh) rotate(360deg);}
}

/* FINAL */
#finalBtn{
display:block;
margin:40px auto;
padding:18px 60px;
background:var(--primary);
color:#fff;
border:none;
letter-spacing:3px;
cursor:pointer;
}

.signature{
display:none;
text-align:center;
margin-top:80px;
font-family:'Cormorant Garamond',serif;
font-size:3rem;
color:var(--primary);
padding-bottom:120px;
}

/* MOBILE POLISH */
@media(max-width:600px){
.card{font-size:1.1rem;padding:30px;}
.hero h1{font-size:2.3rem;}
}
</style>
</head>

<body>

<audio id="bg-music" loop>
<source src="https://files.freemusicarchive.org/storage-freemusicarchive-org/music/no_curator/Scott_Holmes_Music/Romantic_Piano/Scott_Holmes_Music_-_05_-_Love_Story.mp3" type="audio/mpeg">
</audio>

<div id="lock-screen">
<div class="lock-box">
<h2 style="font-family:'Cormorant Garamond',serif;color:#8e1b1b;">A Letter Locked in Time</h2>
<button class="unlock-btn" onclick="unlock()">Unlock</button>
</div>
</div>

<div id="main">
<div class="hero">
<h1>A Symphony of Us</h1>
<p class="sub">August 2023 — 2026</p>
</div>

<div class="section">
<div class="card">To my Sai... August 2023 was just the prologue. From a 9th-grade crush to the man who holds my heart, every day since February 15, 2024, has been a beautiful lesson in love.</div>
<div class="img-box">
<img src="https://i.postimg.cc/L4wNz5Pm/IMG-20260214-233527-269.jpg">
</div>
</div>

<div class="section">
<div class="card">I know I am not always easy to love. My tantrums, my moods — yet you carry me gently. I am proud of you, endlessly.</div>
<div class="img-box">
<img src="https://i.postimg.cc/3rVngNGh/IMG-20260214-233602-649.jpg">
</div>
</div>

<div class="section">
<div class="card">Choosing you was the easiest decision I ever made. I will choose you in every lifetime.</div>
<div class="img-box">
<img src="https://i.postimg.cc/66gYdqZ9/IMG-20260214-233605-327.jpg">
</div>
</div>

<button id="finalBtn" onclick="showFinal()">End Scene</button>
<div class="signature" id="sign">Forever Yours, Sahithi</div>
</div>

<script>
function unlock(){
document.getElementById('bg-music').play();
document.getElementById('lock-screen').style.opacity='0';
setTimeout(()=>{
document.getElementById('lock-screen').style.display='none';
document.getElementById('main').style.opacity='1';
reveal();
roseRain();
},1500);
}

function reveal(){
const sections=document.querySelectorAll('.section');
const observer=new IntersectionObserver(entries=>{
entries.forEach(entry=>{
if(entry.isIntersecting){
entry.target.classList.add('visible');
}
});
},{threshold:0.3});
sections.forEach(sec=>observer.observe(sec));
}

function roseRain(){
setInterval(()=>{
const r=document.createElement('div');
r.className='rose';
r.innerHTML='🌹';
r.style.left=Math.random()*100+'vw';
r.style.fontSize=(Math.random()*20+10)+'px';
r.style.animationDuration=(Math.random()*4+6)+'s';
document.body.appendChild(r);
setTimeout(()=>r.remove(),10000);
},700);
}

function showFinal(){
document.getElementById('sign').style.display='block';
window.scrollTo({top:document.body.scrollHeight,behavior:'smooth'});
}
</script>

</body>
</html>