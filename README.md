
<!DOCTYPE html>
<html lang="pl">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>Salon Aut — Kategorie</title>

<style>
*{box-sizing:border-box;margin:0;padding:0}
body{
  min-height:100vh;
  font-family:Arial, Helvetica, sans-serif;
  color:#fff;
  background:#050505 url("salon_background.png") center/cover no-repeat fixed;
  overflow:hidden;
}
body::before{
  content:"";
  position:fixed;
  inset:0;
  background:rgba(0,0,0,.55);
  backdrop-filter:blur(1px);
  z-index:0;
}
.app{position:relative;z-index:1;height:100vh;padding:10px 40px 24px}

/* Górne kategorie */
.categories{
  position:absolute;
  top:8px;
  left:50%;
  transform:translateX(-50%);
  display:flex;
  gap:22px;
  padding:14px 28px;
  border:1px solid rgba(255,255,255,.18);
  border-radius:22px;
  background:rgba(0,0,0,.62);
  backdrop-filter:blur(8px);
  white-space:nowrap;
}
.cat{
  transition:.2s;
  border:0;
  background:transparent;
  color:#aaa;
  font-weight:900;
  letter-spacing:2px;
  text-transform:uppercase;
  cursor:pointer;
  font-size:13px;
}
.cat.active,.cat:hover{
  color:#58c8ff;
  background:rgba(88,200,255,.18);
  border:1px solid #58c8ff;
  padding:10px 18px;
  border-radius:12px;
  box-shadow:0 0 18px rgba(88,200,255,.35);
}

/* Główne info */
.hero{
  position:absolute;
  left:75px;
  bottom:250px;
}
.car-name{
  font-size:76px;
  line-height:.9;
  font-weight:1000;
  font-style:italic;
  text-transform:uppercase;
  text-shadow:0 5px 20px #000;
}
.price{
  margin-top:20px;
  font-size:48px;
  font-weight:300;
}
.price span{
  color:#58c8ff;
  font-weight:1000;
}

/* Panel FullTune */
.stats{
  position:absolute;
  right:70px;
  top:245px;
  width:340px;
  background:rgba(0,0,0,.55);
  border:1px solid rgba(255,255,255,.12);
  border-radius:18px;
  padding:14px;
  backdrop-filter:blur(8px);
  display:flex;
  flex-direction:column;
  gap:0;
}
.tune-row{
  display:flex;
  justify-content:space-between;
  align-items:center;
  padding:13px 10px;
  border-bottom:1px solid rgba(255,255,255,.08);
  font-size:14px;
  font-weight:900;
}
.tune-row:last-child{border-bottom:none}
.tune-name{
  color:#fff;
  text-transform:uppercase;
  letter-spacing:1px;
}
.tune-price{
  color:#58c8ff;
  font-size:15px;
  font-weight:1000;
}
.tune-main{
  background:rgba(255,255,255,.04);
  border-radius:12px;
  margin-bottom:6px;
}
.tune-main .tune-name{font-size:15px}
.tune-main .tune-price{font-size:17px}


/* Przyciski */
.actions{
  position:absolute;
  right:70px;
  top:590px;
  display:flex;
  gap:14px;
}
.action{
  border:0;
  border-radius:12px;
  padding:18px 35px;
  font-weight:1000;
  cursor:pointer;
}
.buy{background:#58c8ff;color:#000}
.test{background:#fff;color:#000}

/* Dolne karty */
.cars{
  position:absolute;
  left:75px;
  right:75px;
  bottom:35px;
  display:flex;
  gap:20px;
  overflow-x:auto;
  overflow-y:hidden;
  padding:10px 0;
  scroll-behavior:smooth;
}
.cars::-webkit-scrollbar{height:0}
.card{
  min-width:220px;
  height:160px;
  border-radius:16px;
  background:rgba(0,0,0,.72);
  border:1px solid rgba(255,255,255,.12);
  padding:16px;
  cursor:pointer;
  transition:.2s;
  display:flex;
  flex-direction:column;
  align-items:center;
  justify-content:flex-end;
}
.card.active{
  border:2px solid #58c8ff;
  transform:translateY(-12px);
}
.car-img{
  width:150px;
  height:70px;
  object-fit:contain;
  margin-bottom:12px;
  filter:drop-shadow(0 8px 10px #000);
}
.card-name{
  font-size:13px;
  font-weight:900;
  color:#ccc;
  text-transform:uppercase;
}
.card-price{
  margin-top:5px;
  font-size:16px;
  font-weight:1000;
  color:#58c8ff;
}


/* SUWAK */
.slider-controls{
  position:absolute;
  bottom:210px;
  left:50%;
  transform:translateX(-50%);
  width:70%;
  display:flex;
  align-items:center;
  gap:14px;
  z-index:5;
}

.slider-btn{
  width:42px;
  height:42px;
  border-radius:50%;
  border:2px solid #58c8ff;
  background:rgba(0,0,0,.7);
  color:#fff;
  font-size:22px;
  cursor:pointer;
  transition:.2s;
}

.slider-btn:hover{
  background:#58c8ff;
}

.slider-track{
  flex:1;
  height:6px;
  background:rgba(255,255,255,.12);
  border-radius:999px;
  overflow:hidden;
  position:relative;
}

.slider-fill{
  width:35%;
  height:100%;
  background:#58c8ff;
  border-radius:999px;
  transition:.25s;
}

/* Responsywność */
@media(max-width:900px){
  body{overflow:auto}
  .app{height:auto;min-height:100vh;padding:20px}
  .categories,.hero,.stats,.actions,.cars{position:static;transform:none}
  .categories{overflow:auto;margin-bottom:40px}
  .hero{margin-top:80px}
  .car-name{font-size:52px}
  .stats{width:100%;margin:30px 0}
  .actions{margin-bottom:25px}
  .cars{display:grid;grid-template-columns:repeat(auto-fit,minmax(180px,1fr))}
}

.card.active{
  border:2px solid #58c8ff !important;
  box-shadow:0 0 25px rgba(88,200,255,.45) !important;
}
.tune-price{
  color:#58c8ff !important;
}
.car-price span{
  color:#58c8ff !important;
}


.count-info{
  position:absolute;
  left:75px;
  top:70px;
  color:#aaa;
  font-size:13px;
  font-weight:800;
  letter-spacing:1px;
  text-transform:uppercase;
}

.search-box{
  position:absolute;
  top:70px;
  right:75px;
  z-index:5;
}

.search-box input{
  width:260px;
  height:48px;
  background:rgba(15,15,15,.92);
  border:1px solid rgba(88,200,255,.45);
  border-radius:14px;
  outline:none;
  padding:0 18px;
  color:white;
  font-size:15px;
  font-weight:700;
  box-shadow:0 0 20px rgba(88,200,255,.18);
}

.search-box input:focus{
  border-color:#58c8ff;
  box-shadow:0 0 30px rgba(88,200,255,.45);
}

.search-box input::placeholder{
  color:#999;
}


body::before{
  content:"";
  position:fixed;
  inset:0;
  background:
    radial-gradient(circle at top left, rgba(88,200,255,.08), transparent 35%),
    radial-gradient(circle at bottom right, rgba(88,200,255,.06), transparent 35%);
  pointer-events:none;
  z-index:0;
}

</style>
</head>

<body>
<div class="app">

  
<div class="search-box">
  <input type="text" id="searchInput" placeholder="Wpisz nazwę auta...">
</div>

<div class="categories" id="categories"></div>
  <div class="count-info" id="countInfo"></div>

  <section class="hero">
    <div class="car-name" id="carName">ASBO</div>
    <div class="price"><span>$</span><span id="carPrice">30,000</span></div>
  </section>

  <section class="stats">
    <div class="tune-row tune-main">
      <div class="tune-name">FullTune:</div>
      <div class="tune-price" id="fullTune">350 000</div>
    </div>
    <div class="tune-row">
      <div class="tune-name">Silnik:</div>
      <div class="tune-price" id="engineTune">105 000</div>
    </div>
    <div class="tune-row">
      <div class="tune-name">Skrzynia biegów:</div>
      <div class="tune-price" id="gearTune">70 000</div>
    </div>
    <div class="tune-row">
      <div class="tune-name">Turbo:</div>
      <div class="tune-price" id="turboTune">87 500</div>
    </div>
    <div class="tune-row">
      <div class="tune-name">Zawieszenie:</div>
      <div class="tune-price" id="suspensionTune">52 500</div>
    </div>
    <div class="tune-row">
      <div class="tune-name">Hamulce:</div>
      <div class="tune-price" id="brakeTune">70 000</div>
    </div>
    <div class="tune-row">
      <div class="tune-name">Pancerz:</div>
      <div class="tune-price" id="armorTune">70 000</div>
    </div>
  </section>

  

  
<div class="slider-controls">
  <button class="slider-btn" onclick="slideCars(-1)">❮</button>

  <div class="slider-track">
    <div class="slider-fill" id="sliderFill"></div>
  </div>

  <button class="slider-btn" onclick="slideCars(1)">❯</button>
</div>

<section class="cars" id="cars"></section>

</div>

<script>
const data = {
  "Kompaktowe": [
    {name:"ASBO", price:30000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=ASBO", stats:[45, 37, 50, 33]},
    {name:"KANJO", price:100000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=KANJO", stats:[45, 37, 50, 33]},
    {name:"ISSI", price:120000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=ISSI", stats:[45, 37, 50, 33]},
    {name:"PANTO", price:123456, img:"https://via.placeholder.com/220x100/111/ff2b45?text=PANTO", stats:[45, 37, 50, 33]},
    {name:"RHAPSODY", price:300000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=RHAPSODY", stats:[46, 38, 51, 34]},
    {name:"BRIOSO R/A", price:500000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=BRIOSO+R%2FA", stats:[46, 38, 51, 34]},
    {name:"RT3000", price:900000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=RT3000", stats:[48, 40, 53, 36]},
    {name:"ISSI CLASSIC", price:2000000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=ISSI+CLASSIC", stats:[51, 43, 56, 39]}
  ],
  "Coupe": [
    {name:"WEEVIL", price:43000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=WEEVIL", stats:[45, 37, 50, 33]},
    {name:"JACKAL", price:80000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=JACKAL", stats:[45, 37, 50, 33]},
    {name:"F620", price:300000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=F620", stats:[46, 38, 51, 34]},
    {name:"WINDSOR", price:500000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=WINDSOR", stats:[46, 38, 51, 34]},
    {name:"WARRENER HKR", price:1237564, img:"https://via.placeholder.com/220x100/111/ff2b45?text=WARRENER+HKR", stats:[49, 41, 54, 37]},
    {name:"BRIOSO 300", price:1536462, img:"https://via.placeholder.com/220x100/111/ff2b45?text=BRIOSO+300", stats:[50, 42, 55, 38]},
    {name:"MASSACRO", price:2500000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=MASSACRO", stats:[53, 45, 58, 41]},
    {name:"PREVION", price:3000000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=PREVION", stats:[55, 47, 60, 43]}
  ],
  "Drift": [
    {name:"FUTO DRIFT", price:1080808, img:"https://via.placeholder.com/220x100/111/ff2b45?text=FUTO+DRIFT", stats:[48, 40, 53, 36]},
    {name:"YOSEMITE DRIFT", price:1560208, img:"https://via.placeholder.com/220x100/111/ff2b45?text=YOSEMITE+DRIFT", stats:[50, 42, 55, 38]}
  ],
  "Motocykle": [
    {name:"RATBIKE", price:50000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=RATBIKE", stats:[45, 37, 50, 33]},
    {name:"FAGGIO", price:50000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=FAGGIO", stats:[45, 37, 50, 33]},
    {name:"ZOMBIE", price:80451, img:"https://via.placeholder.com/220x100/111/ff2b45?text=ZOMBIE", stats:[45, 37, 50, 33]},
    {name:"MANCHEZ", price:175000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=MANCHEZ", stats:[45, 37, 50, 33]},
    {name:"NEMESIS", price:214000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=NEMESIS", stats:[45, 37, 50, 33]},
    {name:"NIGHTBLADE", price:248000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=NIGHTBLADE", stats:[45, 37, 50, 33]},
    {name:"HEXER", price:248000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=HEXER", stats:[45, 37, 50, 33]},
    {name:"RUFFIAN", price:257000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=RUFFIAN", stats:[45, 37, 50, 33]},
    {name:"WOLFSBANE", price:278000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=WOLFSBANE", stats:[45, 37, 50, 33]},
    {name:"SOVEREIGN", price:290000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=SOVEREIGN", stats:[45, 37, 50, 33]},
    {name:"THRUST", price:340870, img:"https://via.placeholder.com/220x100/111/ff2b45?text=THRUST", stats:[46, 38, 51, 34]},
    {name:"HAKUCHOU", price:345000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=HAKUCHOU", stats:[46, 38, 51, 34]},
    {name:"ZOMBIE LUXUARY", price:352881, img:"https://via.placeholder.com/220x100/111/ff2b45?text=ZOMBIE+LUXUARY", stats:[46, 38, 51, 34]},
    {name:"SANCHEZ SPORT", price:357000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=SANCHEZ+SPORT", stats:[46, 38, 51, 34]},
    {name:"ENDURO", price:378000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=ENDURO", stats:[46, 38, 51, 34]},
    {name:"ESSKEY", price:387000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=ESSKEY", stats:[46, 38, 51, 34]},
    {name:"GARGOYLE", price:450000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=GARGOYLE", stats:[46, 38, 51, 34]},
    {name:"CHIMERA", price:500000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=CHIMERA", stats:[46, 38, 51, 34]},
    {name:"CLIFFHANGER", price:600000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=CLIFFHANGER", stats:[47, 39, 52, 35]},
    {name:"DOUBLET", price:642000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=DOUBLET", stats:[47, 39, 52, 35]},
    {name:"SANCTUS", price:1000000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=SANCTUS", stats:[48, 40, 53, 36]},
    {name:"BAGGER", price:1100000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=BAGGER", stats:[48, 40, 53, 36]},
    {name:"AKUMA", price:1200000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=AKUMA", stats:[49, 41, 54, 37]},
    {name:"AVARUS", price:1214000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=AVARUS", stats:[49, 41, 54, 37]},
    {name:"DAEMON", price:1247600, img:"https://via.placeholder.com/220x100/111/ff2b45?text=DAEMON", stats:[49, 41, 54, 37]},
    {name:"BATI 801RR", price:1348000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=BATI+801RR", stats:[49, 41, 54, 37]},
    {name:"BF400", price:1450000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=BF400", stats:[49, 41, 54, 37]},
    {name:"CARBON RS", price:2247000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=CARBON+RS", stats:[52, 44, 57, 40]},
    {name:"FCR 1000", price:2500000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=FCR+1000", stats:[53, 45, 58, 41]},
    {name:"REEVER", price:10000000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=REEVER", stats:[78, 70, 83, 66]},
    {name:"INNOVATION", price:13000000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=INNOVATION", stats:[88, 80, 93, 76]},
    {name:"SHINOBI", price:16000000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=SHINOBI", stats:[95, 87, 95, 83]},
    {name:"HAKUCHOU DRAG", price:16000000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=HAKUCHOU+DRAG", stats:[95, 87, 95, 83]}
  ],
  "Muscle": [
    {name:"VAMOS", price:70000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=VAMOS", stats:[45, 37, 50, 33]},
    {name:"STALLION", price:100000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=STALLION", stats:[45, 37, 50, 33]},
    {name:"TAMPA", price:130000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=TAMPA", stats:[45, 37, 50, 33]},
    {name:"VIGERO", price:135000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=VIGERO", stats:[45, 37, 50, 33]},
    {name:"IMPALER", price:150000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=IMPALER", stats:[45, 37, 50, 33]},
    {name:"SLAM VAN", price:180000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=SLAM+VAN", stats:[45, 37, 50, 33]},
    {name:"PHOENIX", price:195000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=PHOENIX", stats:[45, 37, 50, 33]},
    {name:"CHINO", price:232000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=CHINO", stats:[45, 37, 50, 33]},
    {name:"VIRGO", price:250000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=VIRGO", stats:[45, 37, 50, 33]},
    {name:"HOTKNIFE", price:250000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=HOTKNIFE", stats:[45, 37, 50, 33]},
    {name:"PICADOR", price:250000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=PICADOR", stats:[45, 37, 50, 33]},
    {name:"BLADE", price:257000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=BLADE", stats:[45, 37, 50, 33]},
    {name:"YOSEMITE3", price:350000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=YOSEMITE3", stats:[46, 38, 51, 34]},
    {name:"SLAMVAN", price:350000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=SLAMVAN", stats:[46, 38, 51, 34]},
    {name:"GAUNTLET", price:380000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=GAUNTLET", stats:[46, 38, 51, 34]},
    {name:"IMPALER LX", price:485000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=IMPALER+LX", stats:[46, 38, 51, 34]},
    {name:"TULIP", price:540000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=TULIP", stats:[46, 38, 51, 34]},
    {name:"DUKES", price:580000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=DUKES", stats:[46, 38, 51, 34]},
    {name:"BUCCANEER", price:618000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=BUCCANEER", stats:[47, 39, 52, 35]},
    {name:"DOMINATOR GTT", price:634000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=DOMINATOR+GTT", stats:[47, 39, 52, 35]},
    {name:"VOODOO LOWRIDER", price:750000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=VOODOO+LOWRIDER", stats:[47, 39, 52, 35]},
    {name:"GAUNTLET CLASSIC", price:800000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=GAUNTLET+CLASSIC", stats:[47, 39, 52, 35]},
    {name:"DOMINATOR ASP", price:942500, img:"https://via.placeholder.com/220x100/111/ff2b45?text=DOMINATOR+ASP", stats:[48, 40, 53, 36]},
    {name:"SABRE TURBO", price:1045000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=SABRE+TURBO", stats:[48, 40, 53, 36]},
    {name:"FACTION", price:1300000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=FACTION", stats:[49, 41, 54, 37]},
    {name:"IMPALER SZ", price:1345000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=IMPALER+SZ", stats:[49, 41, 54, 37]},
    {name:"CHINO LOWRIDER", price:1500000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=CHINO+LOWRIDER", stats:[50, 42, 55, 38]},
    {name:"YOSEMITE", price:1500000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=YOSEMITE", stats:[50, 42, 55, 38]},
    {name:"VIRGO CLASSIC", price:1850000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=VIRGO+CLASSIC", stats:[51, 43, 56, 39]},
    {name:"BUCCANEER LOWRIDER", price:2000000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=BUCCANEER+LOWRIDER", stats:[51, 43, 56, 39]},
    {name:"VIRGO LOWRIDER", price:2150000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=VIRGO+LOWRIDER", stats:[52, 44, 57, 40]},
    {name:"PEYOTE2", price:2250000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=PEYOTE2", stats:[52, 44, 57, 40]},
    {name:"DOMINATOR", price:2350000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=DOMINATOR", stats:[52, 44, 57, 40]},
    {name:"LOST SLAMVAN", price:2440000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=LOST+SLAMVAN", stats:[53, 45, 58, 41]},
    {name:"HUSTLER", price:2800000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=HUSTLER", stats:[54, 46, 59, 42]},
    {name:"BUFFALO", price:3000000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=BUFFALO", stats:[55, 47, 60, 43]},
    {name:"HERMES", price:3500000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=HERMES", stats:[56, 48, 61, 44]},
    {name:"FACTION DONK", price:4120000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=FACTION+DONK", stats:[58, 50, 63, 46]},
    {name:"NIGHTSHADE", price:5000000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=NIGHTSHADE", stats:[61, 53, 66, 49]},
    {name:"GAUNTLET HELLFIRE", price:6411000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=GAUNTLET+HELLFIRE", stats:[66, 58, 71, 54]},
    {name:"TAMPA DRIFT", price:6500000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=TAMPA+DRIFT", stats:[66, 58, 71, 54]},
    {name:"DOMINATOR GTX", price:6500000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=DOMINATOR+GTX", stats:[66, 58, 71, 54]},
    {name:"SABRE GT LOWRIDER", price:6544000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=SABRE+GT+LOWRIDER", stats:[66, 58, 71, 54]},
    {name:"BUFFALO S", price:7000000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=BUFFALO+S", stats:[68, 60, 73, 56]},
    {name:"DEVIANT", price:7000000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=DEVIANT", stats:[68, 60, 73, 56]}
  ],
  "Terenowe": [
    {name:"BLAZER SPORT", price:280000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=BLAZER+SPORT", stats:[45, 37, 50, 33]},
    {name:"BIFTA", price:400000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=BIFTA", stats:[46, 38, 51, 34]},
    {name:"REBEL", price:450000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=REBEL", stats:[46, 38, 51, 34]},
    {name:"BF INJECTION", price:500000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=BF+INJECTION", stats:[46, 38, 51, 34]},
    {name:"MESA TRAIL", price:750000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=MESA+TRAIL", stats:[47, 39, 52, 35]},
    {name:"VAGRANT", price:1200000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=VAGRANT", stats:[49, 41, 54, 37]},
    {name:"DUNE BUGGY", price:1500000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=DUNE+BUGGY", stats:[50, 42, 55, 38]},
    {name:"OUTLAW", price:1800000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=OUTLAW", stats:[51, 43, 56, 39]},
    {name:"REBLAGTS", price:2000000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=REBLAGTS", stats:[51, 43, 56, 39]},
    {name:"BRAWLER", price:3000000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=BRAWLER", stats:[55, 47, 60, 43]},
    {name:"KAMACHO", price:5458796, img:"https://via.placeholder.com/220x100/111/ff2b45?text=KAMACHO", stats:[63, 55, 68, 51]},
    {name:"STREITER", price:8700000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=STREITER", stats:[74, 66, 79, 62]},
    {name:"CONTENDER", price:9870000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=CONTENDER", stats:[77, 69, 82, 65]},
    {name:"FREECRAWLER", price:11000000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=FREECRAWLER", stats:[81, 73, 86, 69]},
    {name:"CARACARA", price:12250000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=CARACARA", stats:[85, 77, 90, 73]},
    {name:"EVERON", price:14835448, img:"https://via.placeholder.com/220x100/111/ff2b45?text=EVERON", stats:[94, 86, 95, 82]},
    {name:"HELLION", price:16000000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=HELLION", stats:[95, 87, 95, 83]},
    {name:"GUARDIAN", price:18000000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=GUARDIAN", stats:[95, 87, 95, 83]},
    {name:"TROPHY TRUCK", price:21000000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=TROPHY+TRUCK", stats:[95, 87, 95, 83]},
    {name:"RIATA", price:22000000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=RIATA", stats:[95, 87, 95, 83]},
    {name:"DESERT RAID", price:22600000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=DESERT+RAID", stats:[95, 87, 95, 83]},
    {name:"DUBSTA 6X", price:66666666, img:"https://via.placeholder.com/220x100/111/ff2b45?text=DUBSTA+6X", stats:[95, 87, 95, 83]}
  ],
  "Rowery": [
    {name:"ROWER GÓRSKI", price:1500, img:"https://via.placeholder.com/220x100/111/ff2b45?text=ROWER+GÓRSKI", stats:[45, 37, 50, 33]},
    {name:"TRI BIKE", price:2000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=TRI+BIKE", stats:[45, 37, 50, 33]},
    {name:"BMX", price:5250, img:"https://via.placeholder.com/220x100/111/ff2b45?text=BMX", stats:[45, 37, 50, 33]}
  ],
  "Sedany": [
    {name:"EMPEROR", price:12500, img:"https://via.placeholder.com/220x100/111/ff2b45?text=EMPEROR", stats:[45, 37, 50, 33]},
    {name:"WASHINGTON", price:22000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=WASHINGTON", stats:[45, 37, 50, 33]},
    {name:"REGINA", price:50000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=REGINA", stats:[45, 37, 50, 33]},
    {name:"ASEA", price:55000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=ASEA", stats:[45, 37, 50, 33]},
    {name:"INTRUDER", price:85000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=INTRUDER", stats:[45, 37, 50, 33]},
    {name:"SULTAN", price:100000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=SULTAN", stats:[45, 37, 50, 33]},
    {name:"FUTO", price:260000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=FUTO", stats:[45, 37, 50, 33]},
    {name:"SUPER DIAMOND", price:350000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=SUPER+DIAMOND", stats:[46, 38, 51, 34]},
    {name:"PRIMO LOWRIDER", price:1000000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=PRIMO+LOWRIDER", stats:[48, 40, 53, 36]},
    {name:"STRETCH", price:2300000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=STRETCH", stats:[52, 44, 57, 40]},
    {name:"RAIDEN", price:2500000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=RAIDEN", stats:[53, 45, 58, 41]},
    {name:"ALPHA", price:4300000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=ALPHA", stats:[59, 51, 64, 47]},
    {name:"KOMODA", price:15000000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=KOMODA", stats:[95, 87, 95, 83]},
    {name:"JUGULAR", price:17500000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=JUGULAR", stats:[95, 87, 95, 83]}
  ],
  "Sportowe": [
{name:"VECTRE", price:125000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=VECTRE", stats:[45, 37, 50, 33]},
    {name:"VETO", price:250000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=VETO", stats:[45, 37, 50, 33]},
    {name:"VETO MODERN", price:350000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=VETO+MODERN", stats:[46, 38, 51, 34]},
    {name:"FURORE GT", price:435000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=FURORE+GT", stats:[46, 38, 51, 34]},
    {name:"BANSHEE", price:500000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=BANSHEE", stats:[46, 38, 51, 34]},
    {name:"ZR350", price:647000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=ZR350", stats:[47, 39, 52, 35]},
    {name:"LYNX", price:650000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=LYNX", stats:[47, 39, 52, 35]},
    {name:"MASSACRO RACE", price:730000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=MASSACRO+RACE", stats:[47, 39, 52, 35]},
    {name:"TYRUS", price:17000000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=TYRUS", stats:[95, 87, 95, 83]},
    {name:"ADDER", price:17500000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=ADDER", stats:[95, 87, 95, 83]},
    {name:"CYCLONE", price:19500000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=CYCLONE", stats:[95, 87, 95, 83]},
    {name:"THRAX", price:20000000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=THRAX", stats:[95, 87, 95, 83]},
    {name:"AUTARCH", price:26000000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=AUTARCH", stats:[95, 87, 95, 83]},
    {name:"NERO", price:32000000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=NERO", stats:[95, 87, 95, 83]},
    {name:"SM722", price:150000000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=SM722", stats:[95, 87, 95, 83]},
    {name:"SULTAN CLASSIC", price:800000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=SULTAN+CLASSIC", stats:[47, 39, 52, 35]},
    {name:"CALICO", price:945000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=CALICO", stats:[48, 40, 53, 36]},
    {name:"IMORGON", price:1000000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=IMORGON", stats:[48, 40, 53, 36]},
    {name:"COMET S2", price:1184000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=COMET+S2", stats:[48, 40, 53, 36]},
    {name:"EUROS", price:1234567, img:"https://via.placeholder.com/220x100/111/ff2b45?text=EUROS", stats:[49, 41, 54, 37]},
    {name:"COQUETTE", price:1450000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=COQUETTE", stats:[49, 41, 54, 37]},
    {name:"DRAFTER", price:1500000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=DRAFTER", stats:[50, 42, 55, 38]},
    {name:"NEO", price:1500000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=NEO", stats:[50, 42, 55, 38]},
    {name:"SUGOI", price:2000000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=SUGOI", stats:[51, 43, 56, 39]},
    {name:"GROWLER", price:2489644, img:"https://via.placeholder.com/220x100/111/ff2b45?text=GROWLER", stats:[53, 45, 58, 41]},
    {name:"CYPHER", price:2500000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=CYPHER", stats:[53, 45, 58, 41]},
    {name:"BESTIA GTS", price:2685000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=BESTIA+GTS", stats:[53, 45, 58, 41]},
    {name:"PARAGON", price:3000000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=PARAGON", stats:[55, 47, 60, 43]},
    {name:"JESTER RR", price:3000000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=JESTER+RR", stats:[55, 47, 60, 43]},
    {name:"KURUMA", price:3480000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=KURUMA", stats:[56, 48, 61, 44]},
    {name:"SPECTER", price:3845000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=SPECTER", stats:[57, 49, 62, 45]},
    {name:"9F", price:4000000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=9F", stats:[58, 50, 63, 46]},
    {name:"ELEGY RH8", price:4000000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=ELEGY+RH8", stats:[58, 50, 63, 46]},
    {name:"ITALI GTB", price:4158624, img:"https://via.placeholder.com/220x100/111/ff2b45?text=ITALI+GTB", stats:[58, 50, 63, 46]},
    {name:"REMUS", price:4500000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=REMUS", stats:[60, 52, 65, 48]},
    {name:"JESTER CLASSIC", price:4500000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=JESTER+CLASSIC", stats:[60, 52, 65, 48]},
    {name:"9F CABRIO", price:4500000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=9F+CABRIO", stats:[60, 52, 65, 48]},
    {name:"SENTINEL CLASSIC", price:4800000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=SENTINEL+CLASSIC", stats:[61, 53, 66, 49]},
    {name:"CARBONIZZARE", price:4953000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=CARBONIZZARE", stats:[61, 53, 66, 49]},
    {name:"FELTZER", price:9500000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=FELTZER", stats:[76, 68, 81, 64]},
    {name:"TAILGATER S", price:10005000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=TAILGATER+S", stats:[78, 70, 83, 66]},
    {name:"SENTINEL CLASSIC WIDEBODY", price:11000000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=SENTINEL+CLASSIC+WIDEBODY", stats:[81, 73, 86, 69]},
    {name:"PARIAH", price:11000000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=PARIAH", stats:[81, 73, 86, 69]},
    {name:"SCHAFTER V12", price:11750000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=SCHAFTER+V12", stats:[84, 76, 89, 72]},
    {name:"VSTR", price:12000000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=VSTR", stats:[85, 77, 90, 73]},
    {name:"COMET SR", price:13000000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=COMET+SR", stats:[88, 80, 93, 76]},
    {name:"SCHLAGEN GT", price:14750000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=SCHLAGEN+GT", stats:[94, 86, 95, 82]},
    {name:"NEON", price:19000000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=NEON", stats:[95, 87, 95, 83]},
    {name:"ITALI GTO", price:20000000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=ITALI+GTO", stats:[95, 87, 95, 83]},
{name:"TROPOS", price:5000000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=TROPOS", stats:[61, 53, 66, 49]},
    {name:"OMNIS", price:5800000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=OMNIS", stats:[64, 56, 69, 52]},
    {name:"LOCUST", price:5993527, img:"https://via.placeholder.com/220x100/111/ff2b45?text=LOCUST", stats:[64, 56, 69, 52]},
    {name:"SULTAN RS CLASSIC", price:6000000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=SULTAN+RS+CLASSIC", stats:[65, 57, 70, 53]},
    {name:"ELEGY RETRO", price:6000000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=ELEGY+RETRO", stats:[65, 57, 70, 53]},
    {name:"ISSI MODERN", price:6150000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=ISSI+MODERN", stats:[65, 57, 70, 53]},
    {name:"JESTER", price:7500000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=JESTER", stats:[70, 62, 75, 58]},
    {name:"PENETRATOR", price:8000000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=PENETRATOR", stats:[71, 63, 76, 59]}
  ],
  "Klasyki Sportowe": [
    {name:"MANANA", price:22800, img:"https://via.placeholder.com/220x100/111/ff2b45?text=MANANA", stats:[45, 37, 50, 33]},
    {name:"PIGALLE", price:100000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=PIGALLE", stats:[45, 37, 50, 33]},
    {name:"DYNASTY", price:150000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=DYNASTY", stats:[45, 37, 50, 33]},
    {name:"CHEBUREK", price:200000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=CHEBUREK", stats:[45, 37, 50, 33]},
    {name:"NEBULA", price:350000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=NEBULA", stats:[46, 38, 51, 34]},
    {name:"BTYPE LUXE", price:462000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=BTYPE+LUXE", stats:[46, 38, 51, 34]},
    {name:"BTYPE", price:595000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=BTYPE", stats:[46, 38, 51, 34]},
    {name:"MONROE", price:615000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=MONROE", stats:[47, 39, 52, 35]},
    {name:"RETINUE MK II", price:850000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=RETINUE+MK+II", stats:[47, 39, 52, 35]},
    {name:"BTYPE HOTROAD", price:1150000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=BTYPE+HOTROAD", stats:[48, 40, 53, 36]},
    {name:"ZION CLASSIC", price:1350000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=ZION+CLASSIC", stats:[49, 41, 54, 37]},
    {name:"PEYOTE LOWRIDER", price:1500000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=PEYOTE+LOWRIDER", stats:[50, 42, 55, 38]},
    {name:"TORNADO LOWRIDER", price:1750000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=TORNADO+LOWRIDER", stats:[50, 42, 55, 38]},
    {name:"GLENDALE LOWRIDER", price:2850000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=GLENDALE+LOWRIDER", stats:[54, 46, 59, 42]},
    {name:"COMET CUSTOM", price:6000000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=COMET+CUSTOM", stats:[65, 57, 70, 53]},
    {name:"SWINGER", price:14500000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=SWINGER", stats:[93, 85, 95, 81]},
    {name:"STAFFORD", price:18000000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=STAFFORD", stats:[95, 87, 95, 83]},
    {name:"MAMBA", price:23000000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=MAMBA", stats:[95, 87, 95, 83]},
    {name:"GT500", price:28000000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=GT500", stats:[95, 87, 95, 83]},
    {name:"CASCO", price:32000000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=CASCO", stats:[95, 87, 95, 83]},
    {name:"Z190", price:38000000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=Z190", stats:[95, 87, 95, 83]},
    {name:"Z-TYPE", price:100000000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=Z-TYPE", stats:[95, 87, 95, 83]}
  ],
  "Super Samochody": [
    {name:"SULTAN RS", price:16000000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=SULTAN+RS", stats:[95, 87, 95, 83]},
{name:"ITALI RSX", price:16000000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=ITALI+RSX", stats:[95, 87, 95, 83]},
    {name:"TYRUS", price:17000000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=TYRUS", stats:[95, 87, 95, 83]},
    {name:"ADDER", price:17500000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=ADDER", stats:[95, 87, 95, 83]},
    {name:"CYCLONE", price:19500000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=CYCLONE", stats:[95, 87, 95, 83]},
    {name:"THRAX", price:20000000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=THRAX", stats:[95, 87, 95, 83]},
    {name:"AUTARCH", price:26000000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=AUTARCH", stats:[95, 87, 95, 83]},
    {name:"NERO", price:32000000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=NERO", stats:[95, 87, 95, 83]},
    {name:"SM722", price:150000000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=SM722", stats:[95, 87, 95, 83]},
    {name:"ZORRUSSO", price:3500000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=ZORRUSSO", stats:[56, 48, 61, 44]},
    {name:"TEMPESTA", price:3800000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=TEMPESTA", stats:[57, 49, 62, 45]},
    {name:"FURIA", price:4000000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=FURIA", stats:[58, 50, 63, 46]},
    {name:"SPECTER CUSTOM", price:8000000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=SPECTER+CUSTOM", stats:[71, 63, 76, 59]},
    {name:"EMERUS", price:8000000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=EMERUS", stats:[71, 63, 76, 59]},
    {name:"SC1", price:10000000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=SC1", stats:[78, 70, 83, 66]},
    {name:"KRIEGER", price:12000000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=KRIEGER", stats:[85, 77, 90, 73]},
    {name:"ZENTORNO", price:12000000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=ZENTORNO", stats:[85, 77, 90, 73]},
    {name:"ENTITY XF", price:12500000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=ENTITY+XF", stats:[86, 78, 91, 74]},
    {name:"ITALI GTB CUSTOM", price:13000000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=ITALI+GTB+CUSTOM", stats:[88, 80, 93, 76]},
    {name:"TURISMO R", price:14000000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=TURISMO+R", stats:[91, 83, 95, 79]},
    {name:"OSIRIS", price:14000000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=OSIRIS", stats:[91, 83, 95, 79]},
    {name:"BANSHEE 900R", price:14000000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=BANSHEE+900R", stats:[91, 83, 95, 79]},
    {name:"REAPER", price:14500000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=REAPER", stats:[93, 85, 95, 81]},
    {name:"T20", price:15000000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=T20", stats:[95, 87, 95, 83]}
  ],
  "SUVY": [
    {name:"SEMINOLE", price:87000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=SEMINOLE", stats:[45, 37, 50, 33]},
    {name:"RADIUS", price:130000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=RADIUS", stats:[45, 37, 50, 33]},
    {name:"ROCOTO", price:147000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=ROCOTO", stats:[45, 37, 50, 33]},
    {name:"GRESLEY", price:180000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=GRESLEY", stats:[45, 37, 50, 33]},
    {name:"GRANGER", price:350000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=GRANGER", stats:[46, 38, 51, 34]},
    {name:"BALLER SPORT", price:545000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=BALLER+SPORT", stats:[46, 38, 51, 34]},
    {name:"XLS", price:650000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=XLS", stats:[47, 39, 52, 35]},
    {name:"CAVALCADE", price:755000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=CAVALCADE", stats:[47, 39, 52, 35]},
    {name:"DUBSTA LUXUARY", price:1500000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=DUBSTA+LUXUARY", stats:[50, 42, 55, 38]},
    {name:"HUNTLEY S", price:4000000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=HUNTLEY+S", stats:[58, 50, 63, 46]},
    {name:"PATRIOT LIMO", price:5000000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=PATRIOT+LIMO", stats:[61, 53, 66, 49]},
    {name:"CAVALCADE XL", price:17500000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=CAVALCADE+XL", stats:[95, 87, 95, 83]},
    {name:"NOVAK", price:18000000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=NOVAK", stats:[95, 87, 95, 83]},
    {name:"TOROS", price:22000000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=TOROS", stats:[95, 87, 95, 83]}
  ],
  "Vany": [
    {name:"YOUGA", price:70800, img:"https://via.placeholder.com/220x100/111/ff2b45?text=YOUGA", stats:[45, 37, 50, 33]},
    {name:"BOBCAT XL", price:75000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=BOBCAT+XL", stats:[45, 37, 50, 33]},
    {name:"RUMPO", price:85000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=RUMPO", stats:[45, 37, 50, 33]},
    {name:"MINIVAN", price:100000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=MINIVAN", stats:[45, 37, 50, 33]},
    {name:"SURFER", price:129998, img:"https://via.placeholder.com/220x100/111/ff2b45?text=SURFER", stats:[45, 37, 50, 33]},
    {name:"CAMPER", price:142000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=CAMPER", stats:[45, 37, 50, 33]},
    {name:"BISON", price:220000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=BISON", stats:[45, 37, 50, 33]},
    {name:"BURRITO", price:285000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=BURRITO", stats:[45, 37, 50, 33]},
    {name:"JOURNEY", price:350000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=JOURNEY", stats:[46, 38, 51, 34]},
    {name:"GANG BURRITO", price:500000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=GANG+BURRITO", stats:[46, 38, 51, 34]},
    {name:"BURRITO CUSTOM", price:500000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=BURRITO+CUSTOM", stats:[46, 38, 51, 34]},
    {name:"MOONBEAM", price:750000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=MOONBEAM", stats:[47, 39, 52, 35]},
    {name:"MOONBEAM LOWRIDER", price:2250000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=MOONBEAM+LOWRIDER", stats:[52, 44, 57, 40]},
    {name:"BENSON", price:3000000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=BENSON", stats:[55, 47, 60, 43]},
    {name:"MULE3", price:5000000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=MULE3", stats:[61, 53, 66, 49]},
    {name:"YOUGA CUSTOM", price:5845410, img:"https://via.placeholder.com/220x100/111/ff2b45?text=YOUGA+CUSTOM", stats:[64, 56, 69, 52]},
    {name:"MINIVAN LOWRIDER", price:8000000, img:"https://via.placeholder.com/220x100/111/ff2b45?text=MINIVAN+LOWRIDER", stats:[71, 63, 76, 59]}
  ]
};



// Usuwanie powtórek aut w każdej kategorii
Object.keys(data).forEach(category => {
  const seen = new Set();
  data[category] = data[category].filter(car => {
    const key = car.name.trim().toLowerCase();
    if (seen.has(key)) return false;
    seen.add(key);
    return true;
  });
});

// Poprawka kategorii Sportowe:
// auta typowo "Super Samochody" nie mają siedzieć drugi raz w Sportowe
const superNames = new Set([
  "ITALI RSX", "TYRUS", "ADDER", "CYCLONE", "THRAX", "AUTARCH", "NERO", "SM722",
  "ZORRUSSO", "TEMPESTA", "FURIA", "EMERUS", "SC1", "KRIEGER", "ZENTORNO",
  "ENTITY XF", "ITALI GTB CUSTOM", "TURISMO R", "OSIRIS", "BANSHEE 900R",
  "REAPER", "T20"
]);

if (data["Sportowe"]) {
  data["Sportowe"] = data["Sportowe"].filter(car => !superNames.has(car.name));
}

// Sortowanie aut cenowo w każdej kategorii
Object.keys(data).forEach(category => {
  data[category].sort((a, b) => a.price - b.price);
});



const categories = document.getElementById("categories");
const cars = document.getElementById("cars");
const carName = document.getElementById("carName");
const carPrice = document.getElementById("carPrice");

let currentCategory = "Kompaktowe";
let currentIndex = 0;

const defaultTune = {
  salon: 30000,
  full: 304500,
  engine: 91000,
  gear: 61000,
  turbo: 76000,
  suspension: 45500,
  brake: 61000,
  armor: 61000
};

function formatPL(value){
  return Number(value || 0).toLocaleString("pl-PL");
}

function updateTunePanel(car){

  let tune = {};

  if(car.price < 350000){
    tune = {
      full: 600000,
      engine: 100000,
      gear: 100000,
      turbo: 100000,
      suspension: 100000,
      brake: 100000,
      armor: 100000
    };
  } else {
    tune = {
      full: Math.round(car.price * 0.70),
      engine: Math.round(car.price * 0.21),
      gear: Math.round(car.price * 0.14),
      turbo: Math.round(car.price * 0.175),
      suspension: Math.round(car.price * 0.105),
      brake: Math.round(car.price * 0.14),
      armor: Math.round(car.price * 0.14)
    };
  }

  document.getElementById("fullTune").textContent = formatPL(tune.full);
  document.getElementById("engineTune").textContent = formatPL(tune.engine);
  document.getElementById("gearTune").textContent = formatPL(tune.gear);
  document.getElementById("turboTune").textContent = formatPL(tune.turbo);
  document.getElementById("suspensionTune").textContent = formatPL(tune.suspension);
  document.getElementById("brakeTune").textContent = formatPL(tune.brake);
  document.getElementById("armorTune").textContent = formatPL(tune.armor);
}


Object.keys(data).forEach(cat=>{
  const btn = document.createElement("button");
  btn.className = "cat";
  btn.textContent = cat;
  btn.dataset.category = cat;
  btn.onclick = ()=>{
    currentCategory = cat;
    currentIndex = 0;




renderCategories();
renderCars();
selectCar(0);
  };
  categories.appendChild(btn);
});

function renderCategories(){
  categories.innerHTML = "";

  Object.keys(data).forEach(cat=>{
    const btn = document.createElement("button");
    btn.className = "cat";
    btn.textContent = cat;
    btn.dataset.category = cat;

    if(cat === currentCategory){
      btn.classList.add("active");
    }

    btn.onclick = ()=>{
      currentCategory = cat;
      currentIndex = 0;
      renderCategories();
      renderCars();
      selectCar(0);
      cars.scrollLeft = 0;
    };

    categories.appendChild(btn);
  });
}

function renderCars(){
  cars.innerHTML = "";
  document.getElementById("countInfo").textContent = "Auta w kategorii: " + data[currentCategory].length;

  data[currentCategory].forEach((car,index)=>{
    const card = document.createElement("div");
    card.className = "card";
    card.onclick = ()=>selectCar(index);

    card.innerHTML = `
      <img class="car-img" src="${car.img}" alt="${car.name}">
      <div class="card-name">${car.name}</div>
      <div class="card-price">$${car.price.toLocaleString("en-US")}</div>
    `;

    cars.appendChild(card);
  });
}

function selectCar(index){
  currentIndex = index;
  const car = data[currentCategory][index];

  carName.textContent = car.name;
  carPrice.textContent = car.price.toLocaleString("en-US");
  updateTunePanel(car);

  document.querySelectorAll(".card").forEach((card,i)=>{
    card.classList.toggle("active", i === index);
  });

  updateSlider();
}



function updateSlider(){
  const max = data[currentCategory].length - 1;
  const fill = document.getElementById("sliderFill");

  if(!fill) return;

  if(max <= 0){
    fill.style.width = "100%";
    return;
  }

  const percent = ((currentIndex + 1) / (max + 1)) * 100;
  fill.style.width = percent + "%";
}

function slideCars(direction){
  const max = data[currentCategory].length - 1;

  currentIndex = currentIndex + direction;

  if(currentIndex < 0) currentIndex = 0;
  if(currentIndex > max) currentIndex = max;

  selectCar(currentIndex);

  const cards = document.querySelectorAll(".card");
  if(cards[currentIndex]){
    cards[currentIndex].scrollIntoView({
      behavior:"smooth",
      inline:"center",
      block:"nearest"
    });
  }
}

renderCategories();
renderCars();
selectCar(0);

const searchInput = document.getElementById("searchInput");

searchInput.addEventListener("input", function(){

  const value = this.value.toLowerCase();
  const cards = document.querySelectorAll(".card");

  cards.forEach(card => {

    const name = card.querySelector(".card-name").textContent.toLowerCase();

    if(name.includes(value)){
      card.style.display = "flex";
    } else {
      card.style.display = "none";
    }

  });

});

</script>

</body>
</html>

