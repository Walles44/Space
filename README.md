<!DOCTYPE html>
<html lang="ru">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, viewport-fit=cover">
<title>ASTRELION // PRO EDITION</title>
<style>
  *, *::before, *::after { box-sizing:border-box; -webkit-tap-highlight-color:transparent; }
  html, body { margin:0; padding:0; background:#050508; color:#f4f4f6; font-family:system-ui,-apple-system,sans-serif; scroll-behavior:smooth; overflow-x:hidden; }
  .nav { position:sticky; top:0; z-index:50; background:rgba(5,5,8,0.82); backdrop-filter:blur(14px); border-bottom:1px solid #1a1a24; padding:14px 20px; display:flex; justify-content:space-between; align-items:center; }
  .logo { display:flex; align-items:center; gap:10px; font-weight:900; letter-spacing:2px; font-size:14px; }
  .orb { width:26px; height:26px; border-radius:50%; background:radial-gradient(circle at 30% 30%,#fff,#7c3aed 55%,#1e1b4b); box-shadow:0 0 18px #7c3aed; }
  .mbtn { background:none; color:#d4d4d8; border:1px solid #27273a; padding:7px 16px; border-radius:99px; font-size:12px; cursor:pointer; }
  .wrap { max-width:1100px; margin:0 auto; padding:24px 18px 60px; }
  .pill { display:inline-flex; align-items:center; gap:8px; border:1px solid #232334; background:#0c0c14; padding:7px 14px; border-radius:99px; font-size:10px; letter-spacing:2px; color:#a1a1aa; margin-bottom:18px; }
  .pill i { width:7px; height:7px; border-radius:50%; background:#a78bfa; box-shadow:0 0 8px #a78bfa; }
  .h1 { font-size:clamp(38px, 9vw, 76px); font-weight:900; line-height:0.95; letter-spacing:-2px; margin:0; }
  .stroke { -webkit-text-stroke:1.2px rgba(255,255,255,0.75); color:transparent; display:block; margin-top:4px; }
  .lead { color:#9ca3af; font-size:clamp(15px, 2vw, 19px); line-height:1.55; max-width:620px; margin:20px 0 26px; }
  .btns { display:flex; gap:12px; flex-wrap:wrap; margin-bottom:32px; }
  .b-w { background:#fff; color:#000; border:0; padding:13px 22px; border-radius:99px; font-weight:800; font-size:13px; text-decoration:none; cursor:pointer; }
  .b-g { background:rgba(255,255,255,0.03); color:#e4e4e7; border:1px solid #27273a; padding:13px 22px; border-radius:99px; font-weight:600; font-size:13px; text-decoration:none; cursor:pointer; }
  .gbox { position:relative; background:radial-gradient(circle,#111022 0%,#07070c 75%); border:1px solid #1f1f2e; border-radius:26px; height:390px; overflow:hidden; margin-bottom:48px; touch-action:none; }
  canvas { width:100%; height:100%; display:block; cursor:grab; }
  .ghint { position:absolute; bottom:14px; left:14px; right:14px; display:flex; justify-content:space-between; pointer-events:none; }
  .ghint span { background:rgba(8,8,14,0.75); border:1px solid #262638; padding:6px 12px; border-radius:99px; font-size:10px; letter-spacing:1px; color:#9ca3af; backdrop-filter:blur(6px); }
  .sec-t { font-size:11px; letter-spacing:2.5px; color:#71717a; text-transform:uppercase; margin-bottom:10px; }
  .h2 { font-size:clamp(28px, 6vw, 48px); font-weight:900; line-height:1.05; letter-spacing:-1px; margin:0 0 16px; }
  .grid { display:grid; grid-template-columns:repeat(auto-fit, minmax(280px, 1fr)); gap:18px; margin:28px 0 50px; }
  .card { position:relative; height:380px; border-radius:24px; overflow:hidden; border:1px solid #232334; display:flex; flex-direction:column; justify-content:flex-end; padding:24px; background-size:cover; background-position:center; cursor:pointer; transition:transform 0.25s, border-color 0.25s; }
  .card:hover { transform:translateY(-5px); border-color:#8b5cf6; }
  .card::before { content:''; position:absolute; inset:0; background:linear-gradient(to top, rgba(4,4,8,0.96) 15%, rgba(4,4,8,0.2) 70%); }
  .c-tag { position:absolute; top:16px; right:16px; background:rgba(10,10,18,0.75); border:1px solid #2e2e42; padding:5px 11px; border-radius:99px; font-size:10px; color:#d4d4d8; backdrop-filter:blur(6px); }
  .c-body { position:relative; z-index:2; }
  .c-sub { font-size:10px; letter-spacing:2px; color:#a78bfa; text-transform:uppercase; margin-bottom:6px; }
  .c-ttl { font-size:28px; font-weight:900; margin:0 0 8px; }
  .c-txt { font-size:13px; color:#a1a1aa; line-height:1.45; margin:0; }
  .stats { border:1px solid #1f1f2e; border-radius:24px; background:#090910; overflow:hidden; display:grid; grid-template-columns:repeat(auto-fit, minmax(220px, 1fr)); }
  .st { padding:26px; border-bottom:1px solid #181824; border-right:1px solid #181824; }
  .st b { font-size:36px; font-weight:900; display:block; margin-bottom:6px; }
  .st span { font-size:13px; color:#9ca3af; }
  .modal { position:fixed; inset:0; background:rgba(0,0,0,0.82); backdrop-filter:blur(10px); z-index:99; display:none; align-items:center; justify-content:center; padding:18px; }
  .modal.on { display:flex; }
  .mbox { background:#0e0e18; border:1px solid #2e2e44; border-radius:24px; max-width:520px; width:100%; padding:26px; }
</style>
</head>
<body>
<nav class="nav">
  <div class="logo"><div class="orb"></div>ASTRELION</div>
  <button class="mbtn" onclick="location.href='#atlas'" id="u-menu"></button>
</nav>
<div class="wrap">
  <div class="pill"><i></i> BEYOND THE KNOWN // 3D WEBGL ENGINE</div>
  <h1 class="h1">ASTRELION<span class="stroke" id="u-sub"></span></h1>
  <p class="lead" id="u-lead"></p>
  <div class="btns">
    <a href="#galaxy" class="b-w" id="u-b1"></a>
    <a href="#atlas" class="b-g" id="u-b2"></a>
  </div>

  <!-- ИНТЕРАКТИВНАЯ 3D ГАЛАКТИКА -->
  <div class="gbox" id="galaxy">
    <canvas id="cv"></canvas>
    <div class="ghint">
      <span>DRAG · 3D ВРАЩЕНИЕ</span>
      <span>PINCH / WHEEL · ЗУМ</span>
    </div>
  </div>

  <div id="atlas">
    <div class="sec-t">01 · АТЛАС</div>
    <h2 class="h2" id="u-h2"></h2>
    <p class="lead" id="u-p2"></p>
    <div class="grid" id="cards"></div>
  </div>

  <div id="scale">
    <div class="sec-t">02 · МАСШТАБ</div>
    <h2 class="h2" id="u-h3"></h2>
    <div class="stats" id="st-box"></div>
  </div>
</div>

<!-- МОДАЛЬНОЕ ОКНО ОБЪЕКТА -->
<div class="modal" id="mdl" onclick="this.classList.remove('on')">
  <div class="mbox" onclick="event.stopPropagation()">
    <div class="c-sub" id="m-sub"></div>
    <h3 class="c-ttl" id="m-ttl" style="margin-bottom:12px"></h3>
    <p class="lead" id="m-desc" style="font-size:14px;margin:0 0 20px"></p>
    <button class="b-w" onclick="document.getElementById('mdl').classList.remove('on')">Закрыть досье ✕</button>
  </div>
</div>

<script>
const TXT = JSON.parse('{"menu":"\u041c\u0435\u043d\u044e","sub":"\u041a\u0410\u0420\u0422\u0410 \u041d\u0415\u0418\u0417\u0412\u0415\u0421\u0422\u041d\u041e\u0413\u041e","lead":"\u0418\u043d\u0442\u0435\u0440\u0430\u043a\u0442\u0438\u0432\u043d\u044b\u0439 \u043f\u0443\u0442\u0435\u0432\u043e\u0434\u0438\u0442\u0435\u043b\u044c \u043f\u043e \u0433\u0430\u043b\u0430\u043a\u0442\u0438\u043a\u0430\u043c, \u044d\u043a\u0437\u043e\u043f\u043b\u0430\u043d\u0435\u0442\u0430\u043c \u0438 \u0433\u043b\u0430\u0432\u043d\u043e\u043c\u0443 \u0432\u043e\u043f\u0440\u043e\u0441\u0443 \u0430\u0441\u0442\u0440\u043e\u0431\u0438\u043e\u043b\u043e\u0433\u0438\u0438: \u043c\u043e\u0436\u0435\u0442 \u043b\u0438 \u0436\u0438\u0437\u043d\u044c \u0441\u0443\u0449\u0435\u0441\u0442\u0432\u043e\u0432\u0430\u0442\u044c \u0433\u0434\u0435-\u0442\u043e \u0435\u0449\u0451?","b1":"\u0412\u043e\u0439\u0442\u0438 \u0432 \u043a\u043e\u0441\u043c\u043e\u0441 \u2197","b2":"\u042d\u043a\u0437\u043e\u043f\u043b\u0430\u043d\u0435\u0442\u044b","h2":"\u041d\u0435 \u043e\u0434\u043d\u0430 \u0441\u0442\u0440\u0430\u043d\u0438\u0446\u0430. \u0426\u0435\u043b\u0430\u044f \u043a\u0430\u0440\u0442\u0430 \u043a\u043e\u0441\u043c\u043e\u0441\u0430.","p2":"\u041d\u0430\u0436\u043c\u0438 \u043d\u0430 \u043b\u044e\u0431\u043e\u0439 \u043c\u0430\u0440\u0448\u0440\u0443\u0442, \u0447\u0442\u043e\u0431\u044b \u043e\u0442\u043a\u0440\u044b\u0442\u044c \u043f\u043e\u043b\u043d\u0443\u044e \u0442\u0435\u043b\u0435\u043c\u0435\u0442\u0440\u0438\u044e \u043e\u0431\u044a\u0435\u043a\u0442\u0430 NASA.","h3":"\u041a\u043e\u0441\u043c\u043e\u0441 \u043f\u043e\u0447\u0442\u0438 \u043d\u0435\u0432\u043e\u0437\u043c\u043e\u0436\u043d\u043e \u043f\u0440\u0435\u0434\u0441\u0442\u0430\u0432\u0438\u0442\u044c. \u041f\u043e\u044d\u0442\u043e\u043c\u0443 \u0435\u0433\u043e \u043d\u0443\u0436\u043d\u043e \u043f\u043e\u043a\u0430\u0437\u0430\u0442\u044c."}');
['menu','sub','lead','b1','b2','h2','p2','h3'].forEach(k=>document.getElementById('u-'+k).textContent=TXT[k]);

const CARDS = [
  {sub:'ГАЛАКТИКА', ttl:'Млечный Путь', tag:'NASA / ESA / CSA', txt:'Структура нашей галактики, её центр Sagittarius A*, рукава и место Солнечной системы.', img:'https://images.unsplash.com/photo-1462331940025-496dfbfc7564?w=800&q=80', full:'Диаметр диска составляет около 100 000 световых лет и содержит от 100 до 400 миллиардов звёзд. В самом центре скрывается сверхмассивная чёрная дыра Стрелец A*.'},
  {sub:'СОСЕДНЯЯ ГАЛАКТИКА', ttl:'Андромеда', tag:'NASA Hubble', txt:'Будущее сближение оказалось менее предсказуемым, чем считалось раньше.', img:'https://images.unsplash.com/photo-1543722530-d2c3201371e7?w=800&q=80', full:'Крупнейшая галактика Местной группы, содержащая около триллиона звёзд. Находится в 2,5 млн световых лет от Земли.'},
  {sub:'ЭКЗОПЛАНЕТА', ttl:'TRAPPIST-1e', tag:'NASA / Webb', txt:'Один из наиболее интересных каменных миров в обитаемой зоне.', img:'https://images.unsplash.com/photo-1614730321146-b6fa6a46bcb4?w=800&q=80', full:'Каменная экзопланета земного типа на расстоянии 40 световых лет в созвездии Водолея. Главный кандидат на наличие жидкого океана.'},
  {sub:'БОЛЬШОЙ ВОПРОС', ttl:'Где искать жизнь?', tag:'NASA Webb', txt:'Жидкая вода, атмосфера, звезда, химия и время — почему одной «обитаемой зоны» недостаточно.', img:'https://images.unsplash.com/photo-1451187580459-43490279c0fa?w=800&q=80', full:'Телескоп Джеймс Уэбб анализирует спектры атмосфер экзопланет в поисках биосигнатур: метана, кислорода, углекислого газа и водяного пара.'}
];
document.getElementById('cards').innerHTML = CARDS.map((c,i)=>`<div class="card" style="background-image:url('${c.img}')" onclick="openM(${i})">
  <span class="c-tag">${c.tag}</span>
  <div class="c-body"><div class="c-sub">${c.sub}</div><h3 class="c-ttl">${c.ttl}</h3><p class="c-txt">${c.txt}</p></div>
</div>`).join('');

function openM(i){
  document.getElementById('m-sub').textContent = CARDS[i].sub + ' // ' + CARDS[i].tag;
  document.getElementById('m-ttl').textContent = CARDS[i].ttl;
  document.getElementById('m-desc').textContent = CARDS[i].full;
  document.getElementById('mdl').classList.add('on');
}

const STATS = [
  ['≈100 000', 'световых лет — диаметр диска Млечного Пути'],
  ['≈2,5 млн', 'световых лет до Андромеды'],
  ['7', 'каменных планет в системе TRAPPIST-1'],
  ['6 000+', 'подтверждённых экзопланет по данным NASA к 2026 году']
];
document.getElementById('st-box').innerHTML = STATS.map(s=>`<div class="st"><b>${s[0]}</b><span>${s[1]}</span></div>`).join('');

// 3D ДВИЖОК СПИРАЛЬНОЙ ГАЛАКТИКИ
const cv = document.getElementById('cv'), ctx = cv.getContext('2d');
let pts = [], rx = 0.55, ry = 0, zm = 1, drag = false, lx = 0, ly = 0;
for(let i=0; i<750; i++){
  let arm = i % 3, r = Math.pow(Math.random(), 0.7) * 150, ang = r * 0.045 + arm * (Math.PI*2/3) + (Math.random()-0.5)*0.5;
  pts.push({x:Math.cos(ang)*r, y:(Math.random()-0.5)*14*(1-r/180), z:Math.sin(ang)*r, s:Math.random()*1.8+0.6, c:r<28?'#ffffff':(arm===0?'#c4b5fd':arm===1?'#93c5fd':'#e2e8f0')});
}
function rsz(){ cv.width = cv.clientWidth; cv.height = cv.clientHeight; }
window.onresize = rsz; rsz();
cv.onpointerdown = e=>{ drag=true; lx=e.clientX; ly=e.clientY; cv.setPointerCapture(e.pointerId); };
cv.onpointermove = e=>{ if(!drag)return; ry+=(e.clientX-lx)*0.01; rx+=(e.clientY-ly)*0.01; lx=e.clientX; ly=e.clientY; };
cv.onpointerup = ()=>drag=false;
cv.onwheel = e=>{ e.preventDefault(); zm = Math.min(2.2, Math.max(0.5, zm - e.deltaY*0.001)); };
function loop(){
  if(!drag) ry += 0.004;
  ctx.clearRect(0,0,cv.width,cv.height);
  let cx = cv.width/2, cy = cv.height/2, sy = Math.sin(ry), cy_ = Math.cos(ry), sx = Math.sin(rx), cx_ = Math.cos(rx);
  pts.forEach(p=>{
    let x1 = p.x*cy_ - p.z*sy, z1 = p.z*cy_ + p.x*sy, y2 = p.y*cx_ - z1*sx, z2 = z1*cx_ + p.y*sx;
    let scale = (320 / (320 + z2)) * zm;
    ctx.fillStyle = p.c; ctx.beginPath();
    ctx.arc(cx + x1*scale, cy + y2*scale, p.s*scale, 0, Math.PI*2); ctx.fill();
  });
  requestAnimationFrame(loop);
}
loop();
</script>
</body>
</html>
