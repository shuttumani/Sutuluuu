index.html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>Shuttumani 💋</title>

<style>
  :root{
    --bg:#000;
    --card:#0f0f0f;
    --pink:#ff4d88;
    --soft:#ffd1e6;
    --muted:rgba(255,255,255,.78);
    --border:rgba(255,77,136,.18);
  }

  *{ box-sizing:border-box; }
  body{
    margin:0;
    background:var(--bg);
    color:#fff;
    font-family:Arial, sans-serif;
    overflow:hidden;
    text-align:center;
  }

  /* PAGES */
  .page{
    position:fixed;
    inset:0;
    display:none;
    padding:20px;
    opacity:0;
    transform:scale(.995);
    transition:opacity .22s ease, transform .22s ease;
  }
  .page.active{
    display:block;
    opacity:1;
    transform:scale(1);
  }
  .scrollPage{
    overflow-y:auto;
    -webkit-overflow-scrolling:touch;
    overscroll-behavior:contain;
  }
  .center{
    height:100%;
    display:flex;
    flex-direction:column;
    justify-content:center;
    align-items:center;
    gap:12px;
  }

  input{
    padding:14px;
    font-size:18px;
    border-radius:12px;
    border:none;
    text-align:center;
    width:min(340px, 86vw);
    outline:none;
  }

  button{
    padding:14px 22px;
    font-size:18px;
    border:none;
    border-radius:12px;
    background:var(--pink);
    color:#fff;
    cursor:pointer;
    transition:transform .08s ease, filter .12s ease;
  }
  button:active{ transform:scale(.98); }
  .btnDark{ background:#222; }

  .title{ margin:8px 0 14px; text-align:center; }
  .card{
    max-width:900px;
    margin:0 auto;
    text-align:left;
    line-height:1.75;
    font-size:17px;
    background:var(--card);
    border-radius:16px;
    padding:18px;
    border:1px solid var(--border);
  }

  /* GLOBAL HEARTS */
  .heart{
    position:fixed;
    bottom:-10px;
    font-size:18px;
    animation:floatUp 5s linear;
    opacity:.7;
    pointer-events:none;
    z-index:1;
  }
  @keyframes floatUp{
    0%{ transform:translateY(0); }
    100%{ transform:translateY(-110vh); }
  }

  /* WELCOME OVERLAY */
  #welcomeOverlay{
    position:fixed;
    inset:0;
    display:none;
    align-items:center;
    justify-content:center;
    z-index:9998;
    background:rgba(0,0,0,.65);
    backdrop-filter:blur(3px);
  }
  #welcomeOverlay.show{ display:flex; }
  .welcomeBox{
    max-width:86vw;
    padding:18px 18px;
    border-radius:18px;
    border:1px solid rgba(255,77,136,.25);
    background:linear-gradient(180deg, rgba(255,77,136,.16), rgba(0,0,0,.30));
    box-shadow:0 18px 60px rgba(0,0,0,.6);
    text-align:center;
    animation:welcomePop .28s ease both;
  }
  @keyframes welcomePop{
    from{ opacity:0; transform:translateY(10px) scale(.98); }
    to{ opacity:1; transform:translateY(0) scale(1); }
  }
  .welcomeText{ font-size:18px; line-height:1.6; color:var(--soft); }
  .welcomeSub{ margin-top:6px; font-size:13px; opacity:.8; }

  /* ENVELOPE */
  .newEnvelope{
    position:relative;
    width:270px;
    height:175px;
    cursor:pointer;
    user-select:none;
  }
  .newEnvelope .body{
    position:absolute;
    inset:0;
    background:#d6336c;
    border-radius:14px;
    box-shadow:0 12px 34px rgba(0,0,0,.45);
  }
  .newEnvelope .topFlap{
    position:absolute;
    top:0; left:0;
    width:0; height:0;
    border-left:135px solid transparent;
    border-right:135px solid transparent;
    border-top:88px solid #ff6b9e;
    transform-origin:top;
    transition:transform .8s ease;
    z-index:3;
  }
  .newEnvelope .paper{
    position:absolute;
    top:22px; left:10px; right:10px; bottom:10px;
    background:#fff0f6;
    border-radius:12px;
    display:flex;
    justify-content:center;
    align-items:center;
    font-size:30px;
    color:#d6336c;
    transform:translateY(44px);
    transition:transform .8s ease;
    z-index:1;
  }
  .newEnvelope.open .topFlap{ transform:rotateX(180deg); }
  .newEnvelope.open .paper{ transform:translateY(-18px); }

  /* COUNTDOWN */
  .timer{
    font-size:18px;
    opacity:.95;
    margin-top:6px;
  }
  .countBox{
    max-width:900px;
    margin:16px auto 0;
    text-align:left;
    line-height:1.9;
    font-size:15px;
    background:var(--card);
    border-radius:16px;
    padding:16px;
    border:1px solid var(--border);
  }

  /* OPTIONS HUB */
  .optCol{
    display:flex;
    flex-direction:column;
    gap:12px;
    max-width:520px;
    margin:0 auto;
  }

  /* OUR TIME GALLERY */
  .galleryGrid{
    display:grid;
    grid-template-columns:repeat(3, 1fr);
    gap:10px;
    margin-top:12px;
  }
  @media (min-width:720px){
    .galleryGrid{ grid-template-columns:repeat(4, 1fr); }
  }
  .galleryGrid img{
    width:100%;
    height:108px;
    object-fit:cover;
    border-radius:16px;
    border:1px solid rgba(255,77,136,.18);
    background:rgba(255,255,255,.04);
    cursor:pointer;
  }
  @media (min-width:720px){
    .galleryGrid img{ height:140px; }
  }

  /* FULLSCREEN VIEWER */
  .viewer{
    position:fixed;
    inset:0;
    background:rgba(0,0,0,.92);
    z-index:9999;
    display:none;
    flex-direction:column;
    justify-content:center;
    align-items:center;
    padding:14px;
  }
  .viewer.show{ display:flex; }
  .viewerStage{
    width:min(92vw, 980px);
    height:min(70vh, 660px);
    border-radius:18px;
    overflow:hidden;
    border:1px solid rgba(255,77,136,.20);
    background:#050505;
    display:flex;
    justify-content:center;
    align-items:center;
  }
  .viewerStage img{ width:100%; height:100%; object-fit:contain; }
  .viewerBar{
    margin-top:12px;
    width:min(92vw, 980px);
    display:flex;
    justify-content:space-between;
    align-items:center;
    gap:10px;
    flex-wrap:wrap;
  }
  .viewerCounter{ opacity:.9; font-size:14px; }
  .viewerBtns{ display:flex; gap:10px; flex-wrap:wrap; }

  /* MEMORIES: small cute bench animation */
  .benchScene{
    position:relative;
    height:220px;
    border-radius:18px;
    overflow:hidden;
    margin:10px 0 16px;
    border:1px solid var(--border);
    background:
      radial-gradient(circle at 30% 30%, rgba(255,255,255,.10), transparent 60%),
      radial-gradient(circle at 80% 40%, rgba(255,77,136,.16), transparent 60%),
      rgba(0,0,0,.22);
  }
  .moon{
    position:absolute; right:18px; top:16px;
    width:46px; height:46px; border-radius:50%;
    background:rgba(255,255,255,.14);
    box-shadow:0 0 30px rgba(255,255,255,.10);
  }
  .stairs{
    position:absolute; left:16px; top:18px;
    width:110px; height:70px;
    border-radius:14px;
    border:1px solid rgba(255,255,255,.08);
    background:rgba(0,0,0,.20);
    overflow:hidden;
  }
  .step{
    height:10px;
    border-top:1px solid rgba(255,255,255,.08);
    opacity:.9;
  }
  .bench{
    position:absolute; left:50%; bottom:26px;
    transform:translateX(-50%);
    width:260px; height:74px;
  }
  .seat{
    position:absolute; left:0; right:0; top:20px;
    height:18px; border-radius:12px;
    background:rgba(255,255,255,.12);
    border:1px solid rgba(255,255,255,.08);
  }
  .backrest{
    position:absolute; left:18px; right:18px; top:0;
    height:16px; border-radius:12px;
    background:rgba(255,77,136,.18);
    border:1px solid rgba(255,77,136,.22);
  }
  .leg{ position:absolute; bottom:0; width:14px; height:34px; border-radius:10px; background:rgba(255,255,255,.10); }
  .leg.l1{ left:24px; } .leg.l2{ right:24px; }
  .couple{
    position:absolute; left:50%; bottom:62px;
    transform:translateX(-50%);
    display:flex; gap:16px;
    align-items:flex-end;
    animation:cuddle 2.4s ease-in-out infinite;
  }
  @keyframes cuddle{
    0%,100%{ transform:translateX(-50%) translateY(0); }
    50%{ transform:translateX(-50%) translateY(-3px); }
  }
  .person{ width:54px; height:110px; position:relative; }
  .head{ width:30px; height:30px; border-radius:50%; background:rgba(255,255,255,.88); position:absolute; top:18px; left:12px; }
  .hair{ width:38px; height:18px; border-radius:12px; background:rgba(255,255,255,.14); position:absolute; top:6px; left:8px; }
  .hair2{ background:rgba(255,77,136,.16); width:42px; left:6px; }
  .body{ width:38px; height:56px; border-radius:18px; background:rgba(255,77,136,.50); position:absolute; top:52px; left:8px; }
  .body2{ background:rgba(255,255,255,.12); border:1px solid rgba(255,77,136,.20); }
  .handHeart{
    position:absolute; left:50%; bottom:96px;
    transform:translateX(-50%);
    font-size:18px;
    opacity:0;
    animation:handPop 2.4s ease-in-out infinite;
  }
  @keyframes handPop{
    0%,35%{ opacity:0; transform:translateX(-50%) translateY(10px) scale(.9); }
    55%{ opacity:1; transform:translateX(-50%) translateY(0) scale(1); }
    100%{ opacity:0; transform:translateX(-50%) translateY(-14px) scale(1.05); }
  }

  /* ONE DAY: wedding + kids animation */
  .futureScene{
    position:relative;
    height:240px;
    border-radius:18px;
    overflow:hidden;
    margin:10px 0 16px;
    border:1px solid var(--border);
    background:
      radial-gradient(circle at 30% 20%, rgba(255,255,255,.10), transparent 60%),
      radial-gradient(circle at 80% 40%, rgba(255,77,136,.16), transparent 60%),
      rgba(0,0,0,.20);
  }
  .stars{
    position:absolute; inset:0;
    background:
      radial-gradient(circle at 12% 18%, rgba(255,255,255,.9) 0 1px, transparent 2px),
      radial-gradient(circle at 28% 36%, rgba(255,255,255,.7) 0 1px, transparent 2px),
      radial-gradient(circle at 68% 22%, rgba(255,255,255,.85) 0 1px, transparent 2px),
      radial-gradient(circle at 82% 44%, rgba(255,255,255,.6) 0 1px, transparent 2px),
      radial-gradient(circle at 52% 12%, rgba(255,255,255,.75) 0 1px, transparent 2px);
    background-size:220px 220px;
    opacity:.22;
    animation:starMove 8s linear infinite;
  }
  @keyframes starMove{
    0%{ transform:translateY(0); }
    50%{ transform:translateY(-8px); }
    100%{ transform:translateY(0); }
  }
  .arch{
    position:absolute; top:18px; left:50%;
    transform:translateX(-50%);
    width:220px; height:120px;
  }
  .archTop{
    position:absolute; inset:0;
    border-radius:120px 120px 16px 16px;
    border:6px solid rgba(255,255,255,.16);
    border-bottom:none;
  }
  .flowers{
    position:absolute;
    font-size:18px;
    opacity:.95;
    filter:drop-shadow(0 6px 10px rgba(0,0,0,.35));
  }
  .f1{ left:8px; top:20px; }
  .f2{ right:10px; top:16px; }
  .f3{ left:50%; transform:translateX(-50%); top:8px; }

  .coupleWrap{
    position:absolute; left:50%; bottom:62px;
    transform:translateX(-50%);
    display:flex; gap:18px; align-items:flex-end;
    animation:cuddle2 2.4s ease-in-out infinite;
  }
  @keyframes cuddle2{
    0%,100%{ transform:translateX(-50%) translateY(0); }
    50%{ transform:translateX(-50%) translateY(-3px); }
  }
  .personW{ position:relative; width:62px; height:120px; }
  .pHair{ position:absolute; top:4px; left:8px; width:46px; height:22px; border-radius:14px; background:rgba(255,255,255,.14); }
  .pHair.veil{ background:rgba(255,77,136,.18); width:54px; left:4px; }
  .pHead{ position:absolute; top:18px; left:14px; width:34px; height:34px; border-radius:50%; background:rgba(255,255,255,.88); }
  .pBody{ position:absolute; top:56px; left:10px; width:42px; height:56px; border-radius:18px; background:rgba(255,77,136,.55); }
  .pBody.dress{ background:rgba(255,255,255,.12); border:1px solid rgba(255,77,136,.22); }
  .ring{
    position:absolute; left:50%; top:-10px;
    transform:translateX(-50%);
    font-size:22px;
    opacity:0;
    animation:ringPop 2.4s ease-in-out infinite;
  }
  @keyframes ringPop{
    0%,35%{ opacity:0; transform:translateX(-50%) translateY(12px) scale(.85); }
    55%{ opacity:1; transform:translateX(-50%) translateY(0) scale(1); }
    100%{ opacity:0; transform:translateX(-50%) translateY(-12px) scale(1.08); }
  }
  .caption{
    position:absolute; left:50%; bottom:12px;
    transform:translateX(-50%);
    width:92%; max-width:720px;
    font-size:14px; opacity:.9;
    padding:8px 10px; border-radius:14px;
    background:rgba(0,0,0,.38);
    border:1px solid rgba(255,255,255,.08);
    text-align:center;
  }
  .kidsScene{
    height:210px;
    background:
      radial-gradient(circle at 30% 30%, rgba(255,255,255,.10), transparent 60%),
      rgba(0,0,0,.20);
  }
  .home{
    position:absolute; left:50%; top:18px;
    transform:translateX(-50%);
    font-size:34px; opacity:.95;
    filter:drop-shadow(0 10px 18px rgba(0,0,0,.35));
  }
  .kidsRow{
    position:absolute; left:50%; bottom:68px;
    transform:translateX(-50%);
    display:flex; gap:16px;
  }
  .kid{
    font-size:22px;
    animation:kidJump 1.8s ease-in-out infinite;
  }
  .k2{ animation-delay:.35s; }
  .k3{ animation-delay:.7s; }
  @keyframes kidJump{
    0%,100%{ transform:translateY(0); }
    50%{ transform:translateY(-10px); }
  }

  /* SURPRISE PAGE */
  .surHero{
    position:relative;
    max-width:900px;
    margin:10px auto 16px;
    border-radius:18px;
    overflow:hidden;
    border:1px solid rgba(255,77,136,.22);
    background:
      radial-gradient(circle at 30% 20%, rgba(255,255,255,.12), transparent 60%),
      radial-gradient(circle at 80% 40%, rgba(255,77,136,.18), transparent 60%),
      rgba(0,0,0,.25);
    padding:18px 16px;
    text-align:center;
  }
  .surGlow{
    position:absolute; inset:-60px;
    background:radial-gradient(circle at 50% 35%, rgba(255,77,136,.26), transparent 60%);
    filter:blur(10px);
    opacity:.9;
  }
  .surLine1{ position:relative; z-index:2; font-size:16px; opacity:.9; }
  .surLine2{ position:relative; z-index:2; font-size:32px; font-weight:900; color:var(--soft); margin:4px 0; }
  .surLine3{ position:relative; z-index:2; font-size:14px; opacity:.85; }

  .giftRow{ display:flex; gap:12px; justify-content:center; flex-wrap:wrap; margin-top:10px; }
  .giftBig{
    position:relative;
    width:120px;
    height:120px;
    cursor:pointer;
    user-select:none;
  }
  .giftBox{
    position:absolute; left:0; right:0; bottom:0;
    height:86px; border-radius:16px;
    background:linear-gradient(180deg, rgba(255,77,136,.85), rgba(255,77,136,.55));
    box-shadow:0 18px 38px rgba(0,0,0,.45);
  }
  .giftLid{
    position:absolute; left:-4px; right:-4px;
    top:30px; height:34px; border-radius:16px;
    background:rgba(255,255,255,.12);
    transform-origin:center bottom;
    transition:transform .7s ease;
  }
  .giftBow{
    position:absolute; top:10px; left:50%;
    transform:translateX(-50%);
    font-size:26px;
    transition:transform .7s ease, opacity .7s ease;
  }
  .giftTag{
    position:absolute; bottom:-22px; left:50%;
    transform:translateX(-50%);
    font-size:13px; opacity:.8;
  }
  .giftBig.open .giftLid{ transform:rotateX(180deg) translateY(-10px); }
  .giftBig.open .giftBow{ transform:translateX(-50%) translateY(-8px) scale(.95); opacity:.8; }

  /* LOVE FLOOD */
  #loveFloodPage{ overflow:hidden; }
  #loveCanvas{
    position:fixed;
    inset:0;
    width:100vw;
    height:100vh;
    z-index:1;
  }
  .loveFloodTop{
    position:fixed;
    top:10px; left:0; right:0;
    display:flex;
    justify-content:space-between;
    padding:0 12px;
    z-index:3;
    gap:10px;
  }
  .loveFloodCenter{
    position:fixed;
    inset:0;
    display:flex;
    flex-direction:column;
    align-items:center;
    justify-content:center;
    z-index:2;
    pointer-events:none;
    padding:20px;
  }
  .bigLoveText{
    font-size:34px;
    font-weight:900;
    color:var(--soft);
    text-shadow:0 18px 60px rgba(0,0,0,.7);
    line-height:1.08;
    animation:pulseLove 1.8s ease-in-out infinite;
  }
  @keyframes pulseLove{
    0%,100%{ transform:scale(1); opacity:.95; }
    50%{ transform:scale(1.03); opacity:1; }
  }
  .bigLoveSub{ margin-top:10px; font-size:14px; opacity:.88; }

  /* PROMISE */
  .promiseHero{
    position:relative;
    border-radius:18px;
    overflow:hidden;
    border:1px solid rgba(255,77,136,.22);
    background:rgba(0,0,0,.20);
    padding:18px;
    text-align:center;
  }
  .promiseGlow{
    position:absolute; inset:-80px;
    background:radial-gradient(circle at 50% 35%, rgba(255,77,136,.28), transparent 65%);
    filter:blur(12px);
    opacity:.9;
  }
  .promiseBig{ position:relative; z-index:2; font-size:20px; font-weight:900; color:var(--soft); }
  .promiseSmall{ position:relative; z-index:2; margin-top:6px; opacity:.9; }
  .promiseList{ margin-top:16px; display:grid; gap:10px; }
  .pItem{
    padding:12px;
    border-radius:16px;
    background:rgba(0,0,0,.25);
    border:1px solid rgba(255,255,255,.08);
    opacity:.95;
    animation:popIn .35s ease both;
  }
  .pItem:nth-child(2){ animation-delay:.05s; }
  .pItem:nth-child(3){ animation-delay:.10s; }
  .pItem:nth-child(4){ animation-delay:.15s; }
  .pItem:nth-child(5){ animation-delay:.20s; }
  .pItem:nth-child(6){ animation-delay:.25s; }
  @keyframes popIn{
    from{ opacity:0; transform:translateY(10px); }
    to{ opacity:1; transform:translateY(0); }
  }

  /* FOREVER */
  #foreverPage{ overflow:hidden; }
  #fireCanvas{
    position:fixed;
    inset:0;
    width:100vw;
    height:100vh;
    z-index:1;
  }
  .foreverWrap{
    position:fixed;
    inset:0;
    z-index:2;
    display:flex;
    flex-direction:column;
    align-items:center;
    justify-content:center;
    text-align:center;
    padding:22px;
    pointer-events:none;
  }
  .foreverGlow{
    position:absolute;
    inset:-90px;
    background:radial-gradient(circle at 50% 40%, rgba(255,77,136,.30), transparent 65%);
    filter:blur(16px);
    opacity:.95;
  }
  .foreverTitle{
    position:relative;
    z-index:2;
    font-size:28px;
    font-weight:900;
    color:var(--soft);
    text-shadow:0 18px 60px rgba(0,0,0,.7);
    animation:foreverPulse 1.9s ease-in-out infinite;
  }
  @keyframes foreverPulse{
    0%,100%{ transform:scale(1); }
    50%{ transform:scale(1.03); }
  }
  .foreverSub{
    position:relative; z-index:2;
    margin-top:10px;
    font-size:14px;
    opacity:.88;
    line-height:1.7;
    max-width:740px;
  }
  .foreverBig{
    position:relative; z-index:2;
    margin-top:16px;
    font-size:20px;
    font-weight:900;
    color:var(--soft);
  }
  .foreverSmall{
    position:relative; z-index:2;
    margin-top:6px;
    opacity:.9;
  }
  .foreverBtns{
    position:relative; z-index:3;
    margin-top:18px;
    display:flex;
    gap:10px;
    flex-wrap:wrap;
    justify-content:center;
    pointer-events:auto;
  }

  /* REPLY (GOOGLE FORM) */
  .formWrap{
    width:100%;
    max-width:900px;
    margin:12px auto 0;
    border-radius:16px;
    overflow:hidden;
    border:1px solid rgba(255,77,136,.18);
    background:#fff;
  }
  iframe{
    width:100%;
    height:820px;
    border:0;
    display:block;
  }
</style>
</head>

<body>

<audio id="bgMusic" loop>
  <source src="music.mp3" type="audio/mpeg" />
</audio>

<!-- Welcome overlay -->
<div id="welcomeOverlay">
  <div class="welcomeBox">
    <div class="welcomeText">ammede ponnu araaa 💋💋</div>
    <div class="welcomeSub">Welcome to our secret world 🩷</div>
  </div>
</div>

<!-- 1) LOCK -->
<div id="lockPage" class="page active">
  <div class="center">
    <h1>shuttumani 💋</h1>
    <input id="passwordInput" type="password" placeholder="Enter date (01032025)" inputmode="numeric" />
    <button onclick="checkPassword()">Unlock</button>
    <div style="opacity:.75;font-size:13px;margin-top:6px;">(only for you 💗)</div>
  </div>
</div>

<!-- 2) ENVELOPE -->
<div id="envelopePage" class="page">
  <div class="center">
    <h2 style="margin-bottom:10px;">Love Letter 💌</h2>

    <div class="newEnvelope" id="envTap" onclick="openLetter()">
      <div class="topFlap"></div>
      <div class="body"></div>
      <div class="paper">💖</div>
    </div>

    <p style="opacity:.85;">Tap the envelope to open 💌</p>
  </div>
</div>

<!-- 3) LETTER -->
<div id="letterPage" class="page scrollPage">
  <h2 class="title">For You ❤️</h2>
  if(fireResizeHandler){
    window.removeEventListener("resize", fireResizeHandler);
    fireResizeHandler=null;
  }
}

/* ===========================
   INIT
=========================== */
document.addEventListener("DOMContentLoaded", () => {
  buildGallery();
  show("lockPage"); // always start at lock
});
</script>

</body>
</html
<div class="newEnvelope" id="envTap" onclick="openLetter()">
      <div class="topFlap"></div>
      <div class="body"></div>
      <div class="paper">💖</div>
    </div>

    <p style="opacity:.85;">Tap the envelope to open 💌</p>
  </div>
</div>

<!-- 3) LETTER -->
<div id="letterPage" class="page scrollPage">
  <h2 class="title">For You ❤️</h2>

  <div class="card">
    eth nee appozha vayika ennu arayillla Appozhayalum vayikulooo ninthe first Valentine's Day annu ennu okke ariyaaa nee annu tution nu varo ennu polum arayilla ethu Azhuthumbo pinne ollathu exam okke alle ath Kazhinja kanan polum pattillalo appo enth cheyyum nee vallathum aloichu vechit indooo vaveee enthe oru idea il korach okkee indu ath Njan parayaneee pinne kali akkanda ketta Njan romantic alla ennu paranju nee enthe eduth ethuuu matte parayana oru dhivasam varum daaaa nokkikooo pinne entha sugalle engane okke nadanna mathiyooo vellapozhum enne kurich okke ortholu tta marannu povaruthu nammal mindandu aya entha indava ponnah enthayalum nammal kanum enganelum okke enthelum mindum athokke orapa pinne ammede ponnu aradaaaa 😘🩷❤️💋🫂 exam kazhinju graduation nu enthavavo kalikan poovanel ninak ath scn avum ennu enik ariyaaaaa bhaki Allavarum adipoli ayit avide erikumbo enthe ponnu matharam blaa blaaa blaaaa enthaleeeee nja. Avide annelum ninthe thanne alledaaaaaa enthokke aleeeeee eni korach serious ayit paraya
    <br><br>
    Atheeee enik ninne bhayankara ishtam a neee yes parayo ennu arayilla ennalum enik entho parayanam ennu thooni neee Chilappo enne angane kandit undavilla ennalum Njan eth eni paranjillel eni annelum eth parayumbo annu paranjel Njan yes paranjene ennu nee Paranja enik veshamam avummm atha eppo parayane enik ninne bhayankara ishtam a "I Love You❤️"
    <br><br>
    Nee ethinu rply thannolu Chilappo eth kelkumbo nee ennod eni mindi ennu varilla angane onnum venda tta ishtam allel ath Paranja mathi scn ella eppo ishtam annu paranju ennu vech kozhapam ellata nammal pazhayath pole thanne veliya vethasam onnum ella nammal thammil ethra kollam ayit ariyaaa pinne angotum engotum ariyathathu onnum ellanu vekkanu Ninak enne ishtam anno ennu arayilla eni eth parayumbozhano athine kurich aloikane ennu polum arayilla enth okke annelum neee enthe koode indel adipoli avum ennu thooni athokke thanne prethekish onnum ella ethokke thanne appo aloichu okke paranjolu tta eppo ninne ishtapedan Karanam ennu okke choicha nee nalla kochanu mariyathak okke nokkum enthelum okke ninnod Paranja nee avide veenolum veliya scn onnnum ella oru kidilan kocha neee athranne pinne elle enthokke okke vannalum 10 kazhinju pooyalum scn onnum indavalle tta enik ninnod olla ishtam poovilla enik  aennum nee enthe koch thanneya Neeyum poovilla ennu Njan vishwosikunnu sharkareee. Aloichu okke eni paranjolu tta
    <br><br>
    Appo veendum paraya I LOVE YOU ❤️
  </div>

  <div style="max-width:900px;margin:14px auto 30px;display:flex;gap:10px;justify-content:center;flex-wrap:wrap;">
    <button onclick="show('countdownPage')">Our Date 💞</button>
    <button class="btnDark" onclick="resetEnvelopeAndGo()">Back 💌</button>
  </div>
</div>

<!-- 4) COUNTDOWN + BULLETS -->
<div id="countdownPage" class="page scrollPage">
  <h2 class="title" style="color:var(--pink);">We committed on</h2>
  <h1 style="margin:0 0 6px;">01 • 03 • 2025 💖</h1>
  <div id="countdownTimer" class="timer"></div>

  <div class="countBox">
    <p>💗 <b>01-03-2025 — The Day We Became “Us”</b><br>
    This was not just a date on the calendar. This was the day feelings turned into something real. The day we stopped standing on two different sides and slowly started walking in the same direction. From this day, your happiness became my peace, your sadness became my concern, and your presence became my comfort. 01-03-2025 is not just when we committed… it is the day my heart officially chose you.</p>

    <p>💗 <b>05-06-2023 — The First Time I Saw You</b><br>
    I still don’t know if you noticed me that day in tuition class… but I remember noticing you. Maybe it was just another normal day for the world, but for me, it quietly became special. I didn’t know that the girl sitting there would later become someone who would change my thoughts, my feelings, and my future. That first sight was simple… but it was the beginning of everything.</p>

    <p>💗 <b>20-07-2010 — The Day the World Became Beautiful</b><br>
    Long before I knew you… before tuition, before conversations, before feelings… this was the day you came into this world. And I sometimes think how lucky this world is to have you in it. Because without this day, there would be no smiles from you, no talks with you, no “us.” 20-07-2010 is special not just because you were born… but because that’s the day the person I would one day love started her journey.</p>
  </div>
  <div style="max-width:900px;margin:14px auto 30px;display:flex;gap:10px;justify-content:center;flex-wrap:wrap;">
    <button onclick="show('diaryPage')">Diary 📖</button>
    <button class="btnDark" onclick="show('letterPage')">Back ❤️</button>
  </div>
</div>

<!-- 5) DIARY -->
<div id="diaryPage" class="page scrollPage">
  <h2 class="title" style="color:var(--pink);">Daily Diary 📖</h2>

  <div class="card" style="text-align:center;">
    <h3 style="margin-top:0;">Today’s message from me 💗</h3>

    <p style="line-height:1.9;text-align:left;">
      Today… I just want you to know that you mean a lot to me.
      Even small talks with you make my day better.
      Whatever happens, I’m always here for you. ❤️
    </p>

    <div style="display:flex;gap:10px;justify-content:center;flex-wrap:wrap;margin-top:16px;">
      <button onclick="show('replyPage')">Reply Today 💌</button>
      <button onclick="show('optionsPage')">Our World 🌙</button>
      <button class="btnDark" onclick="show('countdownPage')">Back ❤️</button>
    </div>
  </div>
</div>

<!-- 6) REPLY (GOOGLE FORM EMBED) -->
<div id="replyPage" class="page scrollPage">
  <h2 class="title" style="color:var(--pink);">Reply to me 💌</h2>

  <div class="card" style="text-align:center;">
    <p style="margin-top:0;opacity:.9;">
      Write your reply here… and if you want, upload a photo too 🩷
    </p>

    <div class="formWrap">
      <iframe
        loading="lazy"
        src="https://docs.google.com/forms/d/e/1FAIpQLSc1JncNbHTVKlZooN4NaDi_Ov08J6Q1g-v5PMHlNnZ_mcGp6A/viewform?usp=dialog">
      </iframe>
    </div>

    <div style="display:flex;gap:10px;justify-content:center;flex-wrap:wrap;margin-top:16px;">
      <button class="btnDark" onclick="show('diaryPage')">Back 📖</button>
      <button onclick="show('optionsPage')">Our World 🌙</button>
    </div>
  </div>
</div>

<!-- 7) OPTIONS HUB -->
<div id="optionsPage" class="page scrollPage">
  <h2 class="title" style="color:var(--pink);">Our World 🌙💗</h2>

  <div class="card" style="text-align:center;">
    <p style="opacity:.9;margin-top:0;">Choose one…</p>

    <div class="optCol">
      <button onclick="show('ourTimePage')">Our Time 📸</button>
      <button onclick="show('memoriesPage')">Memories 🪵</button>
      <button onclick="show('oneDayPage')">One Day 💍</button>
      <button onclick="show('surprisePage')">Surprise For Us 🎁</button>
    </div>

    <div style="margin-top:18px;">
      <button class="btnDark" onclick="show('diaryPage')">Back 📖</button>
    </div>
  </div>
</div>

<!-- 8) OUR TIME (50 PHOTOS PLACEHOLDERS READY) -->
<div id="ourTimePage" class="page scrollPage">
  <h2 class="title" style="color:var(--pink);">Our Time 📸</h2>

  <div class="card">
    <p style="margin-top:0;">
      This page is for our photos… little moments, silly selfies, random clicks — everything that feels like “us”.
    </p>

    <p style="opacity:.85;">
      📌 Add photos later: create folder <b>photos/</b> and name them <b>1.jpg … 50.jpg</b>.
    </p>

    <div class="galleryGrid" id="galleryGrid"></div>

    <div style="display:flex;gap:10px;justify-content:center;flex-wrap:wrap;margin-top:16px;">
      <button class="btnDark" onclick="show('optionsPage')">Back 🌙</button>
    </div>
  </div>
</div>

<!-- 9) MEMORIES -->
<div id="memoriesPage" class="page scrollPage">
  <h2 class="title" style="color:var(--pink);">Memories 🪵</h2>

  <div class="card">
    <div class="benchScene">
      <div class="moon"></div>
      <div class="stairs">
        <div class="step"></div><div class="step"></div><div class="step"></div><div class="step"></div><div class="step"></div><div class="step"></div>
      </div>

      <div class="couple">
        <div class="person">
          <div class="hair"></div>
          <div class="head"></div>
          <div class="body"></div>
        </div>
        <div class="person">
          <div class="hair hair2"></div>
          <div class="head"></div>
          <div class="body body2"></div>
        </div>
        <div class="handHeart">💗</div>
      </div>

      <div class="bench">
        <div class="backrest"></div>
        <div class="seat"></div>
        <div class="leg l1"></div>
        <div class="leg l2"></div>
      </div>
      <div class="caption">Tuition bench… secret talks… staircase moments… all became “us”.</div>
    </div>

    <p style="margin-top:0;">
      I still remember those tuition days… that long wooden bench and the long wooden table.
      Sitting close, pretending it’s normal — but my heart was shouting.
      Even the smallest touch felt like a whole story.
    </p>

    <p>
      And those secret talks… the staircase to the second floor…
      where we acted like strangers in front of everyone,
      but inside, we were building our own little world quietly.
    </p>

    <p style="opacity:.9;">
      Some places become memories not because of the place…
      but because <b>YOU</b> were there. 💗
    </p>

    <div style="display:flex;gap:10px;justify-content:center;flex-wrap:wrap;margin-top:16px;">
      <button class="btnDark" onclick="show('optionsPage')">Back 🌙</button>
    </div>
  </div>
</div>

<!-- 10) ONE DAY -->
<div id="oneDayPage" class="page scrollPage">
  <h2 class="title" style="color:var(--pink);">One Day 💍</h2>

  <div class="card">

    <div class="futureScene">
      <div class="stars"></div>

      <div class="arch">
        <div class="archTop"></div>
        <div class="flowers f1">🌸</div>
        <div class="flowers f2">🌸</div>
        <div class="flowers f3">🌸</div>
      </div>

      <div class="coupleWrap">
        <div class="personW">
          <div class="pHair"></div>
          <div class="pHead"></div>
          <div class="pBody"></div>
        </div>
        <div class="personW">
          <div class="pHair veil"></div>
          <div class="pHead"></div>
          <div class="pBody dress"></div>
        </div>
        <div class="ring">💍</div>
      </div>

      <div class="caption">“One day… I’ll hold your hand like this forever.”</div>
    </div>

    <div class="futureScene kidsScene">
      <div class="home">🏡</div>
      <div class="kidsRow">
        <div class="kid k1">👶</div>
        <div class="kid k2">🧒</div>
        <div class="kid k3">👧</div>
      </div>
      <div class="caption">A small home… noisy laughs… and you as my peace 🩷</div>
    </div>

    <p style="margin-top:10px;">
      One day… not in a rush, not in a dream — in real life…
      I want a peaceful home where your laugh is the happiest sound.
    </p>

    <p style="opacity:.9;">
      Morning tea, silly jokes, small fights, holding hands in crowds…
      I don’t want a perfect life… I want a life with you. 🩷
    </p>

    <div style="display:flex;gap:10px;justify-content:center;flex-wrap:wrap;margin-top:16px;">
      <button class="btnDark" onclick="show('optionsPage')">Back 🌙</button>
    </div>
  </div>
</div>

<!-- 11) SURPRISE PAGE -->
<div id="surprisePage" class="page scrollPage">
  <h2 class="title" style="color:var(--pink);">Surprise For Us 🎁</h2>

  <div class="surHero">
    <div class="surGlow"></div>
    <div class="surLine1">You + Me</div>
    <div class="surLine2">= “Us”</div>
    <div class="surLine3">A small world… built only for you & me 🩷</div>
  </div>

  <div class="card" style="text-align:center;">
    <h3 style="margin-top:0;color:var(--soft);">Open 3 Gifts 🎁</h3>
    <div class="giftRow">
      <div class="giftBig" onclick="openGift(1)">
        <div class="giftLid"></div><div class="giftBow">🎀</div><div class="giftBox"></div><div class="giftTag">Gift 1</div>
      </div>
      <div class="giftBig" onclick="openGift(2)">
        <div class="giftLid"></div><div class="giftBow">🎀</div><div class="giftBox"></div><div class="giftTag">Gift 2</div>
      </div>
      <div class="giftBig" onclick="openGift(3)">
        <div class="giftLid"></div><div class="giftBow">🎀</div><div class="giftBox"></div><div class="giftTag">Gift 3</div>
      </div>
    </div>

    <div style="margin-top:16px;padding:14px;border-radius:16px;border:1px solid rgba(255,77,136,.18);background:rgba(0,0,0,.24);">
      <div id="giftTitle" style="font-size:18px;color:var(--soft);font-weight:900;">💌</div>
      <div id="giftText" style="opacity:.92;line-height:1.8;margin-top:6px;">Tap a gift above…</div>
    </div>

    <div style="margin-top:18px;display:flex;gap:10px;justify-content:center;flex-wrap:wrap;">
      <button class="btnDark" onclick="show('optionsPage')">Back 🌙</button>
      <button onclick="goToLoveFlood()">Next: Love Flood 🌊💗</button>
    </div>
  </div>
</div>

<!-- 12) LOVE FLOOD -->
<div id="loveFloodPage" class="page">
  <div class="loveFloodTop">
    <button class="btnDark" onclick="show('surprisePage')">Back 🎁</button>
    <button onclick="show('promisePage')">Next ➜</button>
  </div>

  <div class="loveFloodCenter">
    <div class="bigLoveText">
      I LOVE YOU<br>SUTTUMANIII ❤️💋
    </div>
    <div class="bigLoveSub">A thousand times… still not enough 🩷</div>
  </div>

  <canvas id="loveCanvas"></canvas>
</div>

<!-- 13) PROMISE -->
<div id="promisePage" class="page scrollPage">
  <h2 class="title" style="color:var(--pink);">Promise Page 🩷</h2>

  <div class="card">
    <div class="promiseHero">
      <div class="promiseGlow"></div>
      <div class="promiseBig">You are my peace.</div>
      <div class="promiseSmall">And I will choose you… again & again.</div>
    </div>

    <div class="promiseList">
      <div class="pItem">💗 I will protect your peace.</div>
      <div class="pItem">💗 I will respect your heart and your boundaries.</div>
      <div class="pItem">💗 I will love you softly — not loudly.</div>
      <div class="pItem">💗 Even in silence, I will still be yours.</div>
      <div class="pItem">💗 I will never make you feel alone.</div>
      <div class="pItem">💗 If the world is heavy, I’ll be your comfort.</div>
    </div>
    <div style="display:flex;gap:10px;justify-content:center;flex-wrap:wrap;margin-top:16px;">
      <button class="btnDark" onclick="show('loveFloodPage')">Back 🌊</button>
      <button onclick="goToForever()">Finish 🎆</button>
    </div>
  </div>
</div>

<!-- 14) FOREVER (FIREWORKS) -->
<div id="foreverPage" class="page">
  <canvas id="fireCanvas"></canvas>

  <div class="foreverWrap">
    <div class="foreverGlow"></div>

    <div class="foreverTitle">WE ARE FOREVER 💗</div>
    <div class="foreverSub">
      Not perfect… but real.<br>
      Not loud… but deep.<br>
      Always “us”. 🩷
    </div>

    <div class="foreverBig">I LOVE YOU SUTTUMANIII ❤️💋</div>
    <div class="foreverSmall">ummahhhh 💋💋💋</div>

    <div class="foreverBtns">
      <button class="btnDark" onclick="show('optionsPage')">Home 🌙</button>
      <button onclick="lockAgain()">Lock 🔒</button>
    </div>
  </div>
</div>

<!-- PHOTO VIEWER -->
<div id="viewer" class="viewer">
  <div class="viewerStage" id="viewerStage">
    <img id="viewerImg" alt="photo"/>
  </div>
  <div class="viewerBar">
    <div class="viewerCounter" id="viewerCounter">1 / 1</div>
    <div class="viewerBtns">
      <button class="btnDark" onclick="prevPhoto()">◀</button>
      <button class="btnDark" onclick="closeViewer()">Close ✖</button>
      <button class="btnDark" onclick="nextPhoto()">▶</button>
    </div>
  </div>
</div>

<script>
/* ===========================
   CORE NAV
=========================== */
function show(pageId){
  document.querySelectorAll(".page").forEach(p => p.classList.remove("active"));
  const next = document.getElementById(pageId);
  if(next) next.classList.add("active");
  if(next && next.classList.contains("scrollPage")) next.scrollTop = 0;

  // stop special effects when leaving pages
  if(pageId !== "loveFloodPage") stopLoveFlood();
  if(pageId !== "foreverPage") stopFireworks();

  // start them when entering pages
  if(pageId === "loveFloodPage") startLoveFlood();
  if(pageId === "foreverPage") startFireworks();
}

/* ===========================
   LOCK + MUSIC
=========================== */
function checkPassword(){
  const raw = document.getElementById("passwordInput").value || "";
  const entered = raw.replace(/\D/g,""); // keep digits only

  if(entered === "01032025"){
    const music = document.getElementById("bgMusic");
    if(music){
      music.volume = 0.75;
      // mobile autoplay requires click – Unlock click is interaction
      music.play().catch(()=>{});
    }

    const overlay = document.getElementById("welcomeOverlay");
    overlay.classList.add("show");
    setTimeout(() => {
      overlay.classList.remove("show");
      show("envelopePage");
    }, 1400);
  }else{
    alert("Wrong date 💔");
  }
}

function lockAgain(){
  // reset privacy
  closeViewer();
  stopLoveFlood();
  stopFireworks();

  const env = document.getElementById("envTap");
  if(env) env.classList.remove("open");

  const inp = document.getElementById("passwordInput");
  if(inp) inp.value = "";

  show("lockPage");
}

/* ===========================
   ENVELOPE -> LETTER
=========================== */
function openLetter(){
  const env = document.getElementById("envTap");
  if(env) env.classList.add("open");
  setTimeout(() => show("letterPage"), 850);
}
function resetEnvelopeAndGo(){
  const env = document.getElementById("envTap");
  if(env) env.classList.remove("open");
  show("envelopePage");
}

/* ===========================
   GLOBAL HEARTS (lightweight)
=========================== */
setInterval(() => {
  const h = document.createElement("div");
  h.className = "heart";
  h.innerHTML = "❤️";
  h.style.left = Math.random()*100 + "%";
  document.body.appendChild(h);
  setTimeout(()=>h.remove(), 4200);
}, 1050);

/* ===========================
   COUNTDOWN (since 01-03-2025)
=========================== */
(function startCountdown(){
  const target = new Date("2025-03-01T00:00:00").getTime();
  setInterval(() => {
    const now = Date.now();
    const diff = now - target;

    const days = Math.floor(diff / (1000*60*60*24));
    const hours = Math.floor((diff % (1000*60*60*24)) / (1000*60*60));
    const mins = Math.floor((diff % (1000*60*60)) / (1000*60));
    const secs = Math.floor((diff % (1000*60)) / 1000);

    const el = document.getElementById("countdownTimer");
    if(el) el.innerHTML = `${days} days 💕 ${hours} hrs 💕 ${mins} mins 💕 ${secs} sec together`;
  }, 1000);
})();

/* ===========================
   OUR TIME 50 PHOTOS
   Add later: /photos/1.jpg ... /photos/50.jpg
=========================== */
const PHOTOS = [];
for(let i=1;i<=50;i++) PHOTOS.push(`photos/${i}.jpg`);
let currentIndex = 0;

function buildGallery(){
  const grid = document.getElementById("galleryGrid");
  if(!grid) return;
  grid.innerHTML = "";

  PHOTOS.forEach((src, i) => {
    const img = document.createElement("img");
    img.src = src;
    img.alt = "photo " + (i+1);
    img.loading = "lazy";

    // If you haven't uploaded photos yet, show placeholders
    img.onerror = () => {
      img.src = "data:image/svg+xml;utf8," + encodeURIComponent(
        `<svg xmlns='http://www.w3.org/2000/svg' width='600' height='400'>
          <rect width='100%' height='100%' fill='#111'/>
          <text x='50%' y='50%' dominant-baseline='middle' text-anchor='middle'
            fill='#ff4d88' font-family='Arial' font-size='28'>
            Add photo ${i+1}
          </text>
        </svg>`
      );
    };

    img.addEventListener("click", () => openViewer(i));
    grid.appendChild(img);
  });
}

function openViewer(i){
  currentIndex = i;
  document.getElementById("viewer").classList.add("show");
  renderViewer();
}
function closeViewer(){
  const v = document.getElementById("viewer");
  if(v) v.classList.remove("show");
}
function nextPhoto(){
  currentIndex = (currentIndex + 1) % PHOTOS.length;
  renderViewer();
}
function prevPhoto(){
  currentIndex = (currentIndex - 1 + PHOTOS.length) % PHOTOS.length;
  renderViewer();
}
function renderViewer(){
  const img = document.getElementById("viewerImg");
  const counter = document.getElementById("viewerCounter");
  if(!img || !counter) return;

  img.src = PHOTOS[currentIndex];
  counter.textContent = `${currentIndex + 1} / ${PHOTOS.length}`;
}

// swipe in viewer
(function enableViewerSwipe(){
  const stage = document.getElementById("viewerStage");
  if(!stage) return;
  let startX=0;
  stage.addEventListener("touchstart",(e)=>{ startX = e.touches[0].clientX; },{passive:true});
  stage.addEventListener("touchend",(e)=>{
    const endX = e.changedTouches[0].clientX;
    const diff = endX - startX;
    if(Math.abs(diff) > 40){
      if(diff < 0) nextPhoto(); else prevPhoto();
    }
  },{passive:true});
})();

/* ===========================
   SURPRISE GIFTS
=========================== */
function openGift(n){
  const gifts = document.querySelectorAll(".giftBig");
  if(gifts[n-1]) gifts[n-1].classList.add("open");

  const title = document.getElementById("giftTitle");
  const text = document.getElementById("giftText");
  if(!title || !text) return;

  if(n===1){
    title.textContent = "💌 Open when you miss me";
    text.textContent = "Close your eyes for 2 seconds… imagine I’m holding your hand. Even if we are not together now, my heart is always with you.";
  }
  if(n===2){
    title.textContent = "🩷 Our small promise";
    text.textContent = "No pressure, no fear… only care. I’ll respect you, protect your peace, and love you in a way that feels safe and real.";
  }
  if(n===3){
    title.textContent = "✨ The “Us” secret";
    text.textContent = "From the moment you entered my life, everything felt softer. I don’t want perfect life… I want a life with YOU. I Love You suttumaniiii ❤️💋";
  }
}

function goToLoveFlood(){
  show("loveFloodPage");
}
  /* ===========================
   LOVE FLOOD CANVAS
=========================== */
let loveFloodRunning=false;
let loveRAF=null;
let loveResizeHandler=null;

function startLoveFlood(){
  if(loveFloodRunning) return;
  loveFloodRunning=true;

  const canvas = document.getElementById("loveCanvas");
  if(!canvas) return;
  const ctx = canvas.getContext("2d", {alpha:true});

  function resize(){
    canvas.width = Math.floor(window.innerWidth * devicePixelRatio);
    canvas.height = Math.floor(window.innerHeight * devicePixelRatio);
    canvas.style.width = window.innerWidth + "px";
    canvas.style.height = window.innerHeight + "px";
    ctx.setTransform(1,0,0,1,0,0);
    ctx.scale(devicePixelRatio, devicePixelRatio);
  }
  resize();
  loveResizeHandler = resize;
  window.addEventListener("resize", loveResizeHandler);

  const MSG = "I LOVE YOU SUTTUMANIII ❤️";
  const COUNT = 240; // looks like thousands because continuous
  const parts = Array.from({length:COUNT}).map(()=>spawn());

  function spawn(){
    return {
      x: Math.random()*window.innerWidth,
      y: Math.random()*window.innerHeight,
      vy: 0.6 + Math.random()*1.8,
      size: 10 + Math.random()*10,
      rot: (-0.08 + Math.random()*0.16),
      alpha: 0.18 + Math.random()*0.55
    };
  }

  function tick(){
    const page = document.getElementById("loveFloodPage");
    if(!page || !page.classList.contains("active")){
      stopLoveFlood();
      return;
    }

    ctx.clearRect(0,0,window.innerWidth, window.innerHeight);

    // soft background layer
    ctx.fillStyle = "rgba(255,77,136,0.05)";
    ctx.fillRect(0,0,window.innerWidth, window.innerHeight);

    for(const p of parts){
      p.y += p.vy;
      p.x += Math.sin(p.y*0.01)*0.35;

      if(p.y > window.innerHeight + 40){
        p.y = -30;
        p.x = Math.random()*window.innerWidth;
        p.vy = 0.6 + Math.random()*1.8;
        p.size = 10 + Math.random()*10;
        p.rot = (-0.08 + Math.random()*0.16);
        p.alpha = 0.18 + Math.random()*0.55;
      }

      ctx.save();
      ctx.globalAlpha = p.alpha;
      ctx.translate(p.x, p.y);
      ctx.rotate(p.rot);
      ctx.font = `bold ${p.size}px Arial`;
      ctx.fillStyle = "rgba(255,209,230,1)";
      ctx.fillText(MSG, 0, 0);
      ctx.restore();
    }

    loveRAF = requestAnimationFrame(tick);
  }
  tick();
}

function stopLoveFlood(){
  loveFloodRunning=false;
  if(loveRAF) cancelAnimationFrame(loveRAF);
  loveRAF=null;

  if(loveResizeHandler){
    window.removeEventListener("resize", loveResizeHandler);
    loveResizeHandler=null;
  }
}

/* ===========================
   FOREVER FIREWORKS
=========================== */
let fireRunning=false;
let fireRAF=null;
let fireResizeHandler=null;

function goToForever(){
  show("foreverPage");
}

function startFireworks(){
  if(fireRunning) return;
  fireRunning=true;

  const canvas = document.getElementById("fireCanvas");
  if(!canvas) return;
  const ctx = canvas.getContext("2d", {alpha:true});

  function resize(){
    canvas.width = Math.floor(window.innerWidth * devicePixelRatio);
    canvas.height = Math.floor(window.innerHeight * devicePixelRatio);
    canvas.style.width = window.innerWidth + "px";
    canvas.style.height = window.innerHeight + "px";
    ctx.setTransform(1,0,0,1,0,0);
    ctx.scale(devicePixelRatio, devicePixelRatio);
  }
  resize();
  fireResizeHandler = resize;
  window.addEventListener("resize", fireResizeHandler);

  const particles=[];

  function burst(x,y){
    const n = 26 + Math.floor(Math.random()*20);
    for(let i=0;i<n;i++){
      const a = Math.random()*Math.PI*2;
      const s = 1.2 + Math.random()*2.8;
      particles.push({
        x,y,
        vx: Math.cos(a)*s,
        vy: Math.sin(a)*s,
        life: 40 + Math.random()*34,
        r: 2 + Math.random()*2.6,
        alpha: 1
      });
    }
  }

  let t=0;
  function tick(){
    const page = document.getElementById("foreverPage");
    if(!page || !page.classList.contains("active")){
      stopFireworks();
      return;
    }

    t++;
    ctx.fillStyle = "rgba(0,0,0,0.20)";
    ctx.fillRect(0,0,window.innerWidth, window.innerHeight);

    if(t % 18 === 0){
      burst(
        60 + Math.random()*(window.innerWidth-120),
        70 + Math.random()*(window.innerHeight*0.45)
      );
    }

    for(let i=particles.length-1;i>=0;i--){
      const p = particles[i];
      p.x += p.vx;
      p.y += p.vy;
      p.vy += 0.03;
      p.life -= 1;
      p.alpha = Math.max(0, p.life/70);

      ctx.beginPath();
      ctx.globalAlpha = p.alpha;
      ctx.fillStyle = "rgba(255,209,230,1)";
      ctx.arc(p.x, p.y, p.r, 0, Math.PI*2);
      ctx.fill();

      if(p.life <= 0) particles.splice(i,1);
    }
    ctx.globalAlpha = 1;

    fireRAF = requestAnimationFrame(tick);
  }
  tick();
}

function stopFireworks(){
  fireRunning=false;
  if(fireRAF) cancelAnimationFrame(fireRAF);
  fireRAF=null;

  if(fireResizeHandler){
    window.removeEventListener("resize", fireResizeHandler);
    fireResizeHandler=null;
  }
}

/* ===========================
   INIT
=========================== */
document.addEventListener("DOMContentLoaded", () => {
  buildGallery();
  show("lockPage"); // always start at lock
});
</script>

</body>
</html>
