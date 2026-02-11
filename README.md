index.html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Private ❤️</title>
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<style>
body{
  margin:0;
  font-family:'Segoe UI',sans-serif;
  background:linear-gradient(135deg,#ff9a9e,#fad0c4);
  overflow:hidden;
}

/* LOCK SCREEN */
#lockScreen{
  position:fixed;
  inset:0;
  display:flex;
  flex-direction:column;
  justify-content:center;
  align-items:center;
  color:white;
  text-align:center;
}

#lockScreen h1{
  font-size:26px;
  margin-bottom:20px;
}

#lockScreen input{
  padding:12px;
  width:250px;
  border-radius:25px;
  border:none;
  text-align:center;
  font-size:16px;
}

#lockScreen button{
  margin-top:15px;
  padding:10px 30px;
  border:none;
  border-radius:25px;
  background:#e63946;
  color:white;
  font-size:16px;
  cursor:pointer;
}

/* POPUP */
#popup{
  position:fixed;
  inset:0;
  background:rgba(0,0,0,0.6);
  display:none;
  justify-content:center;
  align-items:center;
  color:white;
  font-size:24px;
  text-align:center;
  z-index:10;
}

/* LETTER */
#letterPage{
  display:none;
  background:linear-gradient(135deg,#ffdde1,#ee9ca7);
  min-height:100vh;
  padding:30px;
}

.letter-box{
  background:white;
  border-radius:20px;
  padding:25px;
  max-width:900px;
  margin:auto;
  box-shadow:0 15px 40px rgba(0,0,0,0.2);
}

h2{
  text-align:center;
  color:#e63946;
}

.letter-text{
  white-space:pre-wrap;
  line-height:1.8;
  color:#333;
}
</style>
</head>

<body>

<!-- LOCK SCREEN -->
<div id="lockScreen">
  <h1>🔒 Private Page</h1>
  <p>Enter the magic words 💋</p>
  <input id="password" placeholder="01032025" />
  <button onclick="unlock()">Unlock ❤️</button>
</div>

<!-- POPUP -->
<div id="popup">
  ammede ponnu araaa 💋💋
</div>

<!-- LETTER PAGE -->
<div id="letterPage">
  <div class="letter-box">
    <h2>Happy Valentine’s Day ❤️</h2>

    <div class="letter-text">
eth nee appozha vayika ennu arayillla Appozhayalum vayikulooo ninthe first Valentine's Day annu ennu okke ariyaaa nee annu tution nu varo ennu polum arayilla ethu Azhuthumbo pinne ollathu exam okke alle ath Kazhinja kanan polum pattillalo appo enth cheyyum nee vallathum aloichu vechit indooo vaveee enthe oru idea il korach okkee indu ath Njan parayaneee pinne kali akkanda ketta Njan romantic alla ennu paranju nee enthe eduth ethuuu matte parayana oru dhivasam varum daaaa nokkikooo pinne entha sugalle engane okke nadanna mathiyooo vellapozhum enne kurich okke ortholu tta marannu povaruthu nammal mindandu aya entha indava ponnah enthayalum nammal kanum enganelum okke enthelum mindum athokke orapa pinne ammede ponnu aradaaaa 😘🩷❤️💋🫂 exam kazhinju graduation nu enthavavo kalikan poovanel ninak ath scn avum ennu enik ariyaaaaa bhaki Allavarum adipoli ayit avide erikumbo enthe ponnu matharam blaa blaaa blaaaa enthaleeeee nja. Avide annelum ninthe thanne alledaaaaaa enthokke aleeeeee eni korach serious ayit paraya

Atheeee enik ninne bhayankara ishtam a neee yes parayo ennu arayilla ennalum enik entho parayanam ennu thooni neee Chilappo enne angane kandit undavilla ennalum Njan eth eni paranjillel eni annelum eth parayumbo annu paranjel Njan yes paranjene ennu nee Paranja enik veshamam avummm atha eppo parayane enik ninne bhayankara ishtam a "I Love You❤️"

Nee ethinu rply thannolu Chilappo eth kelkumbo nee ennod eni mindi ennu varilla angane onnum venda tta ishtam allel ath Paranja mathi scn ella eppo ishtam annu paranju ennu vech kozhapam ellata nammal pazhayath pole thanne veliya vethasam onnum ella nammal thammil ethra kollam ayit ariyaaa pinne angotum engotum ariyathathu onnum ellanu vekkanu Ninak enne ishtam anno ennu arayilla eni eth parayumbozhano athine kurich aloikane ennu polum arayilla enth okke annelum neee enthe koode indel adipoli avum ennu thooni athokke thanne prethekish onnum ella ethokke thanne appo aloichu okke paranjolu tta

Appo veendum paraya  
I LOVE YOU ❤️
    </div>
  </div>
</div>

<script>
function unlock(){
  const pass = document.getElementById("password").value.trim();
  if(pass === "ammede ponnu araaa💋💋"){
    document.getElementById("popup").style.display="flex";
    setTimeout(()=>{
      document.getElementById("popup").style.display="none";
      document.getElementById("lockScreen").style.display="none";
      document.getElementById("letterPage").style.display="block";
    },2000);
  }else{
    alert("Wrong magic words 😝");
  }
}
</script>

</body>
</html>



