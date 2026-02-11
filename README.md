index.html
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>Shuttumani</title>

<style>
  body{margin:0;background:#000;color:#fff;font-family:Arial,sans-serif;overflow:hidden;text-align:center;}
  .page{position:fixed;inset:0;display:none;padding:20px;box-sizing:border-box;}
  .page.active{display:block;}
  .center{height:100%;display:flex;flex-direction:column;justify-content:center;align-items:center;gap:12px;}

  button{padding:14px 22px;font-size:18px;border:none;border-radius:12px;background:#ff4da6;color:#fff;}
  .btnDark{background:#222;}

  input{padding:14px;font-size:18px;border-radius:10px;border:none;text-align:center;width:min(320px,85vw);}

  .scrollPage{overflow-y:auto;-webkit-overflow-scrolling:touch;}

  .card{max-width:720px;margin:0 auto;text-align:left;line-height:1.7;font-size:17px;background:#0f0f0f;border-radius:14px;padding:18px;}
  .title{margin:10px 0 14px;text-align:center;}
  .countBox{max-width:720px;margin:18px auto 0;text-align:left;line-height:1.9;font-size:15px;background:#0f0f0f;border-radius:14px;padding:16px;}
  .timer{font-size:18px;margin:10px 0 0;opacity:.95;}

  /* hearts */
  .heart{position:fixed;bottom:-10px;font-size:20px;animation:floatUp 5s linear infinite;opacity:.7;pointer-events:none;z-index:1;}
  @keyframes floatUp{0%{transform:translateY(0);}100%{transform:translateY(-110vh);} }

  /* Envelope tap-safe */
  .newEnvelope{position:relative;width:260px;height:170px;cursor:pointer;margin-top:10px;user-select:none;-webkit-tap-highlight-color:transparent;}
  .newEnvelope *{pointer-events:none;} /* IMPORTANT: tap anywhere works */
  .newEnvelope .body{position:absolute;inset:0;background:#d6336c;border-radius:12px;box-shadow:0 10px 30px rgba(0,0,0,.4);z-index:1;}
  .newEnvelope .topFlap{position:absolute;top:0;left:0;width:0;height:0;border-left:130px solid transparent;border-right:130px solid transparent;border-top:85px solid #ff6b9e;transform-origin:top;transition:transform .8s ease;z-index:3;}
  .newEnvelope .paper{position:absolute;top:20px;left:10px;right:10px;bottom:10px;background:#fff0f6;border-radius:10px;display:flex;justify-content:center;align-items:center;font-size:28px;color:#d6336c;transform:translateY(40px);transition:transform .8s ease;z-index:2;}
  .newEnvelope.open .topFlap{transform:rotateX(180deg);}
  .newEnvelope.open .paper{transform:translateY(-20px);}
  .gallery{
  max-width:900px;
  margin:0 auto;
  display:grid;
  grid-template-columns:repeat(3, 1fr);
  gap:10px;
}
@media (min-width:700px){
  .gallery{ grid-template-columns:repeat(4, 1fr); }
}
.photoCard{
  background:#0f0f0f;
  border-radius:14px;
  overflow:hidden;
  border:1px solid #222;
}
.photoCard img{
  width:100%;
  height:140px;
  object-fit:cover;
  display:block;
  background:#111;
}
.photoCap{
  padding:8px 10px;
  font-size:13px;
  opacity:.9;
  text-align:left;
}
  .scene{
  max-width:900px;
  margin:0 auto;
  background:#0f0f0f;
  border:1px solid #222;
  border-radius:16px;
  padding:16px;
}

.sceneTitle{
  margin:0 0 10px;
  color:#ff4d88;
  text-align:center;
}

.benchArea{
  position:relative;
  height:180px;
  border-radius:14px;
  background:linear-gradient(180deg,#0b0b0b,#121212);
  overflow:hidden;
  border:1px solid #222;
}

.bench{
  position:absolute;
  left:-60%;
  top:60%;
  width:180%;
  height:50px;
  background:linear-gradient(90deg,#7a4a2a,#5c341d);
  border-radius:14px;
  box-shadow:0 10px 30px rgba(0,0,0,.4);
  animation: benchSlide 7s ease-in-out infinite;
}

.table{
  position:absolute;
  left:-40%;
  top:30%;
  width:160%;
  height:36px;
  background:linear-gradient(90deg,#9a5f35,#6a3b20);
  border-radius:14px;
  opacity:.95;
  animation: tableSlide 7s ease-in-out infinite;
}

@keyframes benchSlide{
  0%{transform:translateX(0);}
  50%{transform:translateX(20%);}
  100%{transform:translateX(0);}
}
@keyframes tableSlide{
  0%{transform:translateX(0);}
  50%{transform:translateX(-18%);}
  100%{transform:translateX(0);}
}

.kids{
  position:absolute;
  left:50%;
  top:48%;
  transform:translate(-50%,-50%);
  display:flex;
  gap:14px;
  align-items:center;
  font-size:34px;
  z-index:5;
}
.kids .hand{
  font-size:22px;
  opacity:.9;
  animation: handPulse 1.4s ease-in-out infinite;
}
@keyframes handPulse{
  0%,100%{transform:scale(1);}
  50%{transform:scale(1.15);}
}

.stairsArea{
  position:relative;
  height:200px;
  border-radius:14px;
  background:linear-gradient(180deg,#0b0b0b,#151515);
  overflow:hidden;
  border:1px solid #222;
  margin-top:14px;
}

.step{
  position:absolute;
  bottom:0;
  width:120%;
  height:26px;
  background:#1c1c1c;
  border-top:1px solid #2a2a2a;
  transform:skewX(-18deg);
}
.step.s1{bottom:0; opacity:.95;}
.step.s2{bottom:26px; opacity:.9;}
.step.s3{bottom:52px; opacity:.85;}
.step.s4{bottom:78px; opacity:.8;}
.step.s5{bottom:104px; opacity:.75;}
.step.s6{bottom:130px; opacity:.7;}

.whisper{
  position:absolute;
  left:50%;
  top:52%;
  transform:translate(-50%,-50%);
  font-size:30px;
  display:flex;
  gap:12px;
  align-items:center;
  z-index:5;
}
.bubble{
  background:#111;
  border:1px solid #2a2a2a;
  padding:8px 12px;
  border-radius:999px;
  font-size:13px;
  opacity:.9;
  animation: bubbleFloat 2.2s ease-in-out infinite;
}
@keyframes bubbleFloat{
  0%,100%{transform:translateY(0);}
  50%{transform:translateY(-6px);}
}
  .futureWrap{
  max-width:900px;
  margin:0 auto;
  background:#0f0f0f;
  border:1px solid #222;
  border-radius:16px;
  padding:16px;
}

.ringGlow{
  font-size:46px;
  animation:ringPulse 1.6s ease-in-out infinite;
  filter:drop-shadow(0 0 12px rgba(255,77,136,.35));
}
@keyframes ringPulse{
  0%,100%{transform:scale(1);}
  50%{transform:scale(1.12);}
}

.weddingScene{
  position:relative;
  height:210px;
  border-radius:14px;
  background:linear-gradient(180deg,#070707,#151515);
  border:1px solid #222;
  overflow:hidden;
  margin-top:12px;
}

.lights{
  position:absolute;
  inset:-20px;
  background:
    radial-gradient(circle at 20% 20%, rgba(255,77,136,.22), transparent 45%),
    radial-gradient(circle at 80% 30%, rgba(58,160,255,.18), transparent 45%),
    radial-gradient(circle at 50% 70%, rgba(255,255,255,.08), transparent 50%);
  animation:lightsMove 6s ease-in-out infinite;
}
@keyframes lightsMove{
  0%,100%{transform:translateY(0);}
  50%{transform:translateY(10px);}
}

.couple{
  position:absolute;
  left:50%;
  top:55%;
  transform:translate(-50%,-50%);
  font-size:44px;
  display:flex;
  gap:14px;
  align-items:center;
  z-index:5;
}
.couple .kiss{
  font-size:26px;
  animation:kissPop 1.2s ease-in-out infinite;
}
@keyframes kissPop{
  0%,100%{transform:scale(1);opacity:.9;}
  50%{transform:scale(1.2);opacity:1;}
}

.kidsRow{
  margin-top:14px;
  display:flex;
  justify-content:center;
  gap:12px;
  flex-wrap:wrap;
}

.kidBubble{
  background:#111;
  border:1px solid #2a2a2a;
  border-radius:999px;
  padding:10px 14px;
  font-size:15px;
  opacity:.95;
  animation:kidFloat 2.3s ease-in-out infinite;
}
.kidBubble:nth-child(2){animation-delay:.3s;}
.kidBubble:nth-child(3){animation-delay:.6s;}
@keyframes kidFloat{
  0%,100%{transform:translateY(0);}
  50%{transform:translateY(-6px);}
}

.promiseLine{
  margin-top:14px;
  padding:12px 14px;
  border-radius:14px;
  background:#111;
  border:1px solid #222;
  text-align:left;
  line-height:1.9;
  opacity:.95;
}
  .surpriseBox{
  max-width:900px;
  margin:0 auto;
  background:#0f0f0f;
  border:1px solid #222;
  border-radius:16px;
  padding:18px;
  text-align:center;
}

.gift{
  font-size:60px;
  cursor:pointer;
  animation:giftBounce 1.6s ease-in-out infinite;
}

@keyframes giftBounce{
  0%,100%{transform:translateY(0);}
  50%{transform:translateY(-10px);}
}

.revealText{
  display:none;
  margin-top:16px;
  padding:14px;
  background:#111;
  border-radius:12px;
  border:1px solid #222;
  line-height:1.8;
  opacity:.95;
}

.sparkle{
  font-size:26px;
  animation:sparkleGlow 1.5s infinite;
}
@keyframes sparkleGlow{
  0%,100%{opacity:.7;}
  50%{opacity:1;}
}

.loveRow{
  display:flex;
  flex-wrap:wrap;
  justify-content:center;
  gap:10px;
  margin-top:14px;
}

.loveChip{
  background:#111;
  border:1px solid #2a2a2a;
  padding:8px 12px;
  border-radius:999px;
  font-size:14px;
  opacity:.9;
}
</style>
</head>

<body>

<audio id="bgMusic" loop>
  <source src="music.mp3" type="audio/mpeg" />
</audio>
<div id="lockPage" class="page active">
  <div class="center">
    <h1>shuttumani 💋</h1>
    <div style="opacity:.85;">“ammede ponnu araaa 💋💋”</div>

    <input id="passwordInput" type="password" placeholder="Enter date"
      inputmode="numeric" autocomplete="off"
      onkeydown="if(event.key==='Enter'){ checkPassword(); }">

    <button type="button" onclick="checkPassword()">Unlock</button>
  </div>
</div>
<div id="envelopePage" class="page">
  <div class="center">
    <h2 style="margin:0 0 8px;">Love Letter 💌</h2>

    <div class="newEnvelope" onclick="openLetter()">
      <div class="topFlap"></div>
      <div class="body"></div>
      <div class="paper">💖</div>
    </div>

    <p style="opacity:.8;margin:8px 0 0;">Tap the envelope to open 💌</p>
  </div>
</div>
<div id="letterPage" class="page scrollPage">
  <h2 class="title">For You ❤️</h2>

  <div class="card">
    eth nee appozha vayika ennu arayillla Appozhayalum vayikulooo ninthe first Valentine's Day annu ennu okke ariyaaa nee annu tution nu varo ennu polum arayilla ethu Azhuthumbo pinne ollathu exam okke alle ath Kazhinja kanan polum pattillalo appo enth cheyyum nee vallathum aloichu vechit indooo vaveee enthe oru idea il korach okkee indu ath Njan parayaneee pinne kali akkanda ketta Njan romantic alla ennu paranju nee enthe eduth ethuuu matte parayana oru dhivasam varum daaaa nokkikooo pinne entha sugalle engane okke nadanna mathiyooo vellapozhum enne kurich okke ortholu tta marannu povaruthu nammal mindandu aya entha indava ponnah enthayalum nammal kanum enganelum okke enthelum mindum athokke orapa pinne ammede ponnu aradaaaa 😘🩷❤️💋🫂 exam kazhinju graduation nu enthavavo kalikan poovanel ninak ath scn avum ennu enik ariyaaaaa bhaki Allavarum adipoli ayit avide erikumbo enthe ponnu matharam blaa blaaa blaaaa enthaleeeee nja. Avide annelum ninthe thanne alledaaaaaa enthokke aleeeeee eni korach serious ayit paraya
    <br><br>
    Atheeee enik ninne bhayankara ishtam a neee yes parayo ennu arayilla ennalum enik entho parayanam ennu thooni neee Chilappo enne angane kandit undavilla ennalum Njan eth eni paranjillel eni annelum eth parayumbo annu paranjel Njan yes paranjene ennu nee Paranja enik veshamam avummm atha eppo parayane enik ninne bhayankara ishtam a "I Love You❤️"
    <br><br>
    Nee ethinu rply thannolu Chilappo eth kelkumbo nee ennod eni mindi ennu varilla angane onnum venda tta ishtam allel ath Paranja mathi scn ella eppo ishtam annu paranju ennu vech kozhapam ellata nammal pazhayath pole thanne veliya vethasam onnum ella nammal thammil ethra kollam ayit ariyaaa pinne angotum engotum ariyathathu onnum ellanu vekkanu Ninak enne ishtam anno ennu arayilla eni eth parayumbozhano athine kurich aloikane ennu polum arayilla enth okke annelum neee enthe koode indel adipoli avum ennu thooni athokke thanne prethekish onnum ella ethokke thanne appo aloichu okke paranjolu tta eppo ninne ishtapedan Karanam ennu okke choicha nee nalla kochanu mariyathak okke nokkum enthelum okke ninnod Paranja nee avide veenolum veliya scn onnnum ella oru kidilan kocha neee athranne pinne elle enthokke okke vannalum 10 kazhinju pooyalum scn onnum indavalle tta enik ninnod olla ishtam poovilla enik aennum nee enthe koch thanneya Neeyum poovilla ennu Njan vishwosikunnu sharkareee. Aloichu okke eni paranjolu tta
    <br><br>
    Appo veendum paraya I LOVE YOU ❤️
  </div>

  <div style="max-width:720px;margin:14px auto 30px;display:flex;gap:10px;justify-content:center;flex-wrap:wrap;">
    <button onclick="show('countdownPage')">Our Date 💞</button>
    <button class="btnDark" onclick="show('envelopePage')">Back 💌</button>
  </div>
</div>
<div id="countdownPage" class="page scrollPage">
  <h2 class="title" style="color:#ff4d88;">We committed on</h2>
  <h1 style="margin:0 0 6px;">01 • 03 • 2025 💖</h1>
  <div id="countdownTimer" class="timer"></div>

  <div class="countBox">
    <p>💗 01-03-2025 — The Day We Became “Us”  
    This was not just a date on the calendar. This was the day feelings turned into something real. The day we stopped standing on two different sides and slowly started walking in the same direction. From this day, your happiness became my peace, your sadness became my concern, and your presence became my comfort. 01-03-2025 is not just when we committed… it is the day my heart officially chose you.</p>

    <p>💗 05-06-2023 — The First Time I Saw You  
    I still don’t know if you noticed me that day in tuition class… but I remember noticing you. Maybe it was just another normal day for the world, but for me, it quietly became special. I didn’t know that the girl sitting there would later become someone who would change my thoughts, my feelings, and my future. That first sight was simple… but it was the beginning of everything.</p>

    <p>💗 20-07-2010 — The Day the World Became Beautiful  
    Long before I knew you… before tuition, before conversations, before feelings… this was the day you came into this world. And I sometimes think how lucky this world is to have you in it. Because without this day, there would be no smiles from you, no talks with you, no “us.” 20-07-2010 is special not just because you were born… but because that’s the day the person I would one day love started her journey.</p>
  </div>

  <div style="max-width:720px;margin:14px auto 30px;display:flex;gap:10px;justify-content:center;flex-wrap:wrap;">
    <button onclick="show('diaryPage')">Diary 📖</button>
    <button class="btnDark" onclick="show('letterPage')">Back ❤️</button>
  </div>
</div>
<div id="diaryPage" class="page scrollPage">
  <h2 class="title" style="color:#ff4d88;">Daily Diary 📖</h2>

  <div class="card">
    <h3 style="margin-top:0;text-align:center;">Today’s message from me 💗</h3>

    <p style="line-height:1.9;">
      Today… I just want you to know that you mean a lot to me.
      Even small talks with you make my day better.
      Whatever happens, I’m always here for you. ❤️
    </p>

    <div style="display:flex;gap:10px;justify-content:center;flex-wrap:wrap;margin-top:16px;">
      <button onclick="openGoogleForm()">Reply Today 💌</button>
      <button onclick="show('optionsPage')">Our World 🌙</button>
      <button class="btnDark" onclick="show('countdownPage')">Back ❤️</button>
    </div>
  </div>
</div>

<div id="optionsPage" class="page scrollPage">
  <h2 class="title" style="color:#ff4d88;">Our World 🌙💗</h2>

  <div class="card" style="text-align:center;">
    <p style="opacity:.9;margin-top:0;">Choose one…</p>

    <div style="display:flex;flex-direction:column;gap:12px;max-width:420px;margin:0 auto;">
      <button onclick="show('ourTimePage')">Our Time 📸</button>
      <button onclick="show('memoriesPage')">Memories 🪵</button>
      <button onclick="show('oneDayPage')">One Day 💍</button>
      <button onclick="show('surprisePage')">Surprise ✨</button>
    </div>

    <div style="margin-top:18px;">
      <button class="btnDark" onclick="show('diaryPage')">Back 📖</button>
    </div>
  </div>
</div>

<div id="ourTimePage" class="page scrollPage">
  <h2 class="title" style="color:#ff4d88;">Our Time 📸</h2>

  <div class="card" style="text-align:center;">
    <p style="margin-top:0;opacity:.9;">
      This is our photo wall 💗  
      (I added 50 slots. You can replace photos later.)
    </p>

    <div class="gallery" id="galleryGrid"></div>

    <div style="margin-top:16px;">
      <button class="btnDark" onclick="show('optionsPage')">Back 🌙</button>
    </div>
  </div>
</div>

<div id="memoriesPage" class="page scrollPage">
  <h2 class="title" style="color:#ff4d88;">Memories 🪵</h2>

  <div class="card">
    <p style="margin-top:0;">
      Tuition days… that long wooden bench and the long table.
      Sitting close, acting normal… but inside my heart was shouting.
    </p>
    <p>
      And those secret talks on the staircase to the second floor…
      where we looked like strangers outside, but inside we were building our own world.
    </p>
    <p style="opacity:.9;">
      Some places become memories not because of the place… but because YOU were there. 💗
    </p>
  </div>

  <div class="scene" style="margin-top:14px;">
    <h3 class="sceneTitle">📚 Tuition Bench Moment</h3>
    <div class="benchArea">
      <div class="table"></div>
      <div class="bench"></div>
      <div class="kids">
        <span>🧑‍🎓</span>
        <span class="hand">🤝</span>
        <span>👩‍🎓</span>
      </div>
    </div>
    <p style="opacity:.85;margin:10px 0 0;">
      That small “hand-hold” felt bigger than the whole classroom.
    </p>
  </div>

  <div class="scene" style="margin-top:14px;">
    <h3 class="sceneTitle">🪜 Staircase Secret Talk</h3>
    <div class="stairsArea">
      <div class="step s1"></div><div class="step s2"></div><div class="step s3"></div>
      <div class="step s4"></div><div class="step s5"></div><div class="step s6"></div>

      <div class="whisper">
        <span>🧑</span>
        <span class="bubble">“don’t look 😳”</span>
        <span>👩</span>
      </div>
    </div>
    <p style="opacity:.85;margin:10px 0 0;">
      We spoke softly… but the memory stayed loud in my heart.
    </p>
  </div>

  <div style="max-width:720px;margin:14px auto 30px;display:flex;gap:10px;justify-content:center;flex-wrap:wrap;">
    <button class="btnDark" onclick="show('optionsPage')">Back 🌙</button>
  </div>
</div>

<div id="oneDayPage" class="page scrollPage">
  <h2 class="title" style="color:#ff4d88;">One Day 💍</h2>

  <div class="card" style="text-align:center;">
    <div class="ringGlow">💍</div>
    <p style="margin:10px 0 0;opacity:.92;">
      One day… not in a rush, not only in dreams — in real life…  
      I want a peaceful home where your laugh is the loudest sound.
    </p>
  </div>

  <div class="futureWrap" style="margin-top:14px;">
    <h3 style="margin:0;color:#ff4d88;text-align:center;">Our Wedding Moment ✨</h3>

    <div class="weddingScene">
      <div class="lights"></div>
      <div class="couple">
        <span>🤵</span>
        <span class="kiss">💋</span>
        <span>👰</span>
      </div>
    </div>

    <div class="promiseLine">
      I want to hold your hand in crowds and still feel like it’s only us.  
      Morning tea, small fights, silly jokes, planning trips…  
      and always coming back to the same comfort — **you**.
    </div>

    <h3 style="margin:16px 0 8px;color:#ff4d88;text-align:center;">Our Little Future 👶💗</h3>
    <div class="kidsRow">
      <div class="kidBubble">👶 “amma!”</div>
      <div class="kidBubble">👧 “appa!”</div>
      <div class="kidBubble">🧸 “our home”</div>
    </div>

    <p style="opacity:.9;text-align:center;margin:12px 0 0;">
      I don’t want a perfect life… I want a life with you. 🩷
    </p>
  </div>

  <div style="max-width:720px;margin:14px auto 30px;display:flex;gap:10px;justify-content:center;flex-wrap:wrap;">
    <button class="btnDark" onclick="show('optionsPage')">Back 🌙</button>
  </div>
</div>
<script>
function show(pageId){
  document.querySelectorAll('.page').forEach(p=>p.classList.remove('active'));
  const page = document.getElementById(pageId);
  if(!page){ alert("Missing page: " + pageId); return; }
  page.classList.add('active');
  window.scrollTo(0,0);
}

function checkPassword(){
  const raw = document.getElementById("passwordInput").value || "";
  const entered = raw.replace(/\D/g,""); // allows 01-03-2025 too
  if(entered === "01032025"){
    const music = document.getElementById("bgMusic");
    if(music) music.play().catch(()=>{});
    show("envelopePage");
  } else {
    alert("Wrong date 💔");
  }
}

function openLetter(){
  const env = document.querySelector(".newEnvelope");
  if(env) env.classList.add("open");
  setTimeout(()=>show("letterPage"), 850);
}

function openGoogleForm(){
  window.open("https://docs.google.com/forms/d/e/1FAIpQLSc1JncNbHTVKlZooN4NaDi_Ov08J6Q1g-v5PMHlNnZ_mcGp6A/viewform?usp=dialog","_blank");
}

// Hearts
setInterval(()=>{
  const heart=document.createElement("div");
  heart.className="heart";
  heart.innerHTML="❤️";
  heart.style.left=Math.random()*100+"%";
  document.body.appendChild(heart);
  setTimeout(()=>heart.remove(),5000);
},800);

// Countdown since 01-03-2025
(function(){
  const target = new Date("2025-03-01T00:00:00").getTime();
  setInterval(()=>{
    const diff = Date.now() - target;
    const days = Math.floor(diff / (1000*60*60*24));
    const hours = Math.floor((diff % (1000*60*60*24)) / (1000*60*60));
    const mins = Math.floor((diff % (1000*60*60)) / (1000*60));
    const secs = Math.floor((diff % (1000*60)) / 1000);
    const el = document.getElementById("countdownTimer");
    if(el) el.innerHTML = `${days} days 💕 ${hours} hrs 💕 ${mins} mins 💕 ${secs} sec together`;
  },1000);
})();
(function buildGallery(){
  const grid = document.getElementById("galleryGrid");
  if(!grid) return;

  for(let i=1; i<=50; i++){
    const card = document.createElement("div");
    card.className = "photoCard";

    // placeholder image (works even if you don't add photos yet)
    const img = document.createElement("img");
    img.alt = "Photo " + i;
    img.src = `https://picsum.photos/seed/shuttumani_${i}/500/500`;

    const cap = document.createElement("div");
    cap.className = "photoCap";
    cap.innerHTML = `💗 Photo ${i}`;

    card.appendChild(img);
    card.appendChild(cap);
    grid.appendChild(card);
  }
})();
<div id="surprisePage" class="page scrollPage">
  <h2 class="title" style="color:#ff4d88;">A Small Surprise ✨</h2>

  <div class="surpriseBox">
    <p style="opacity:.9;margin-top:0;">
      I kept something special for you here…  
      Tap the gift to open it 🎁
    </p>

    <div class="gift" onclick="openSurprise()">🎁</div>

    <div id="hiddenSurprise" class="revealText">
      <div class="sparkle">✨💖✨</div>

      <p>
        No matter what happens in life…  
        I just want you to know one thing.
      </p>

      <p>
        Meeting you was not an accident.  
        Caring for you is not a duty.  
        Loving you is not a choice…  
        it just happened naturally.
      </p>

      <p>
        Even if the world changes,  
        my feeling for you will stay the same.
      </p>

      <div class="loveRow">
        <div class="loveChip">You are my peace 🌙</div>
        <div class="loveChip">You are my comfort 💗</div>
        <div class="loveChip">You are my happiness 🥹</div>
      </div>

      <p style="margin-top:12px;">
        And always remember…  
        you will never be alone as long as I am here.
      </p>

      <div class="sparkle">✨ I Love You ✨</div>
    </div>

    <div style="margin-top:18px;">
      <button class="btnDark" onclick="show('optionsPage')">Back 🌙</button>
    </div>
  </div>
</div>

</script>

</body>
</html>
