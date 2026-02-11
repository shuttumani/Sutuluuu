index.html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>For You ❤️</title>

<style>
*{
  margin:0;
  padding:0;
  box-sizing:border-box;
  font-family:'Segoe UI',sans-serif;
}

body{
  height:100vh;
  background:linear-gradient(180deg,#ffb6c1,#ffe4e1);
  overflow:hidden;
}

.hidden{display:none;}
.page{
  position:absolute;
  width:100%;
  height:100%;
  display:flex;
  justify-content:center;
  align-items:center;
  flex-direction:column;
  text-align:center;
  padding:20px;
}

/* LOCK */
#lock input{
  padding:12px;
  border:none;
  border-radius:25px;
  text-align:center;
  font-size:16px;
}
#lock button{
  margin-top:15px;
  padding:10px 25px;
  border:none;
  border-radius:25px;
  background:#ff4d6d;
  color:white;
  font-size:16px;
}

/* TRANSITION TEXT */
#transition{
  font-size:28px;
  animation:fade 3s ease-in-out;
}

/* ENVELOPE */
#envelope{
  font-size:90px;
  cursor:pointer;
  animation:float 2s infinite;
}

/* LETTER */
#letter{
  overflow-y:auto;
  max-height:85vh;
  line-height:1.7;
  font-size:16px;
}
#letter span{
  font-size:22px;
  color:#ff2d55;
  font-weight:bold;
}

/* COMMIT PAGE */
#commit h2{
  margin-bottom:10px;
}
#timer{
  font-size:22px;
  margin:15px 0;
  color:#ff2d55;
}

/* HEARTS */
.heart{
  position:fixed;
  bottom:-10px;
  color:#ff2d55;
  animation:rise 6s linear infinite;
  opacity:.7;
}

/* ANIMATIONS */
@keyframes float{
  0%{transform:translateY(0)}
  50%{transform:translateY(-12px)}
  100%{transform:translateY(0)}
}
@keyframes rise{
  from{transform:translateY(0);opacity:1}
  to{transform:translateY(-110vh);opacity:0}
}
@keyframes fade{
  0%{opacity:0}
  30%{opacity:1}
  70%{opacity:1}
  100%{opacity:0}
}
</style>
</head>

<body>

<!-- LOCK -->
<div id="lock" class="page">
  <h2>Enter the password 💗</h2>
  <input type="password" id="pass">
  <button onclick="unlock()">Unlock</button>
</div>

<!-- TRANSITION -->
<div id="transition" class="page hidden">
  ammede ponnu araaa 💋💋
</div>

<!-- ENVELOPE PAGE -->
<div id="home" class="page hidden">
  <div id="envelope">💌</div>
  <p>Tap the letter</p>
</div>

<!-- LETTER -->
<div id="letterPage" class="page hidden">
  <div id="letter">
Happy Valentine's Day ponnahhh❤💋💋🫂<br><br>

eth nee appozha vayika ennu arayillla Appozhayalum vayikulooo ninthe first Valentine's Day annu ennu okke ariyaaa nee annu tution nu varo ennu polum arayilla ethu Azhuthumbo pinne ollathu exam okke alle ath Kazhinja kanan polum pattillalo appo enth cheyyum nee vallathum aloichu vechit indooo vaveee enthe oru idea il korach okkee indu ath Njan parayaneee pinne kali akkanda ketta Njan romantic alla ennu paranju nee enthe eduth ethuuu matte parayana oru dhivasam varum daaaa nokkikooo pinne entha sugalle engane okke nadanna mathiyooo vellapozhum enne kurich okke ortholu tta marannu povaruthu nammal mindandu aya entha indava ponnah enthayalum nammal kanum enganelum okke enthelum mindum athokke orapa pinne ammede ponnu aradaaaa 😘🩷❤️💋🫂 exam kazhinju graduation nu enthavavo kalikan poovanel ninak ath scn avum ennu enik ariyaaaaa bhaki Allavarum adipoli ayit avide erikumbo enthe ponnu matharam blaa blaaa blaaaa enthaleeeee nja. Avide annelum ninthe thanne alledaaaaaa enthokke aleeeeee eni korach serious ayit paraya 
Atheeee enik ninne bhayankara ishtam a neee yes parayo ennu arayilla ennalum enik entho parayanam ennu thooni neee Chilappo enne angane kandit undavilla ennalum Njan eth eni paranjillel eni annelum eth parayumbo annu paranjel Njan yes paranjene ennu nee Paranja enik veshamam avummm atha eppo parayane enik ninne bhayankara ishtam a "I Love You❤️"
Nee ethinu rply thannolu Chilappo eth kelkumbo nee ennod eni mindi ennu varilla angane onnum venda tta ishtam allel ath Paranja mathi scn ella eppo ishtam annu paranju ennu vech kozhapam ellata nammal pazhayath pole thanne veliya vethasam onnum ella nammal thammil ethra kollam ayit ariyaaa pinne angotum engotum ariyathathu onnum ellanu vekkanu Ninak enne ishtam anno ennu arayilla eni eth parayumbozhano athine kurich aloikane ennu polum arayilla enth okke annelum neee enthe koode indel adipoli avum ennu thooni athokke thanne prethekish onnum ella ethokke thanne appo aloichu okke paranjolu tta eppo ninne ishtapedan Karanam ennu okke choicha nee nalla kochanu mariyathak okke nokkum enthelum okke ninnod Paranja nee avide veenolum veliya scn onnnum ella oru kidilan kocha neee athranne pinne elle enthokke okke vannalum 10 kazhinju pooyalum scn onnum indavalle tta enik ninnod olla ishtam poovilla enik  aennum nee enthe koch thanneya Neeyum poovilla ennu Njan vishwosikunnu sharkareee. Aloichu okke eni paranjolu tta 
Appo veendum paraya.<br><br>

<span>I LOVE YOU ❤️</span>
  </div>
  <small>(Swipe down ❤️)</small>
</div>

<!-- COMMIT PAGE -->
<div id="commit" class="page hidden">
  <h2>We committed ❤️</h2>
  <p>01 • 03 • 2025</p>

  <div id="timer"></div>

  <ul style="text-align:left; margin-top:15px;">
    <li>01/03/2025 – She said she loves me ❤️</li>
    <li>05/06/2023 – First time I saw her in tuition</li>
    <li>20/07/2010 – When she came into this world 🌍</li>
  </ul>
</div>

<audio id="music" loop>
  <source src="YOUR_MUSIC_LINK_HERE.mp3" type="audio/mpeg">
</audio>

<script>
let current = "lock";
const music = document.getElementById("music");

function unlock(){
  if(pass.value==="01032025"){
    lock.classList.add("hidden");
    transition.classList.remove("hidden");
    music.play();
    setTimeout(()=>{
      transition.classList.add("hidden");
      home.classList.remove("hidden");
    },3000);
  } else alert("Wrong password 💔");
}

envelope.onclick=()=>{
  home.classList.add("hidden");
  letterPage.classList.remove("hidden");
  current="letter";
};

// HEARTS
setInterval(()=>{
  const h=document.createElement("div");
  h.className="heart";
  h.innerHTML="❤️";
  h.style.left=Math.random()*100+"vw";
  h.style.fontSize=15+Math.random()*20+"px";
  document.body.appendChild(h);
  setTimeout(()=>h.remove(),6000);
},350);

// SWIPE DOWN
let startY=0;
document.addEventListener("touchstart",e=>startY=e.touches[0].clientY);
document.addEventListener("touchend",e=>{
  let endY=e.changedTouches[0].clientY;
  if(startY-endY>80 && current==="letter"){
    letterPage.classList.add("hidden");
    commit.classList.remove("hidden");
    current="commit";
  }
});

// COUNTDOWN
const startDate = new Date("2025-03-01");
setInterval(()=>{
  const now=new Date();
  const diff=now-startDate;
  const days=Math.floor(diff/(1000*60*60*24));
  timer.innerHTML=`${days} days together 💕`;
},1000);
</script>

</body>
</html>

