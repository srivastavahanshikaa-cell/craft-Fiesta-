# craft-Fiesta-
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Craft Fiestá – Reel Preview</title>
<style>
*, *::before, *::after { margin:0; padding:0; box-sizing:border-box; }
:root {
  --cream:#F5EFE0; --terracotta:#C1522A; --olive:#4A5E2F;
  --blush:#E8A89C; --gold:#C89B3C; --dark:#2A1F14;
}
html, body { width:100%; min-height:100%; background:#1a1a1a; font-family:'Helvetica Neue',Arial,sans-serif; overflow-x:hidden; }
.page { display:flex; flex-direction:column; align-items:center; justify-content:center; padding:24px 0 32px; }

/* PHONE */
.phone { width:340px; height:620px; border-radius:36px; position:relative; box-shadow:0 30px 80px rgba(0,0,0,0.6),inset 0 0 0 3px #333; background:var(--cream); overflow:visible; }
.phone-inner { position:absolute; inset:0; border-radius:36px; overflow:hidden; pointer-events:none; }

/* SLIDES */
.slide { position:absolute; inset:0; border-radius:36px; opacity:0; transform:scale(1.04); transition:opacity 0.7s ease,transform 0.7s ease; display:flex; flex-direction:column; align-items:center; justify-content:center; overflow:hidden; pointer-events:none; }
.slide.active { opacity:1; transform:scale(1); pointer-events:all; }

/* SLIDE 1 */
.s1 { background:var(--cream); }
.blob { position:absolute; border-radius:50%; filter:blur(60px); opacity:0.35; pointer-events:none; }
.blob1 { width:220px;height:220px;background:var(--blush);top:-40px;right:-40px; }
.blob2 { width:180px;height:180px;background:var(--gold);bottom:-30px;left:-30px; }
.s1 .content { position:relative; text-align:center; padding:32px 28px; }
.eyebrow { font-size:11px; letter-spacing:3px; text-transform:uppercase; color:var(--terracotta); margin-bottom:12px; }
.big-title { font-family:Georgia,'Times New Roman',serif; font-size:64px; line-height:1; color:var(--olive); font-weight:900; }
.big-title span { color:var(--terracotta); display:block; font-style:italic; }
.tagline { margin-top:18px; font-size:13px; color:var(--dark); letter-spacing:1px; line-height:1.6; }
.pill { display:inline-block; margin-top:22px; background:var(--olive); color:var(--cream); font-size:11px; letter-spacing:2px; text-transform:uppercase; padding:8px 20px; border-radius:50px; }
.leaf-deco { position:absolute; font-size:42px; opacity:0.18; pointer-events:none; }
.leaf-deco.tl { top:8px; left:8px; transform:rotate(-30deg); }
.leaf-deco.br { bottom:8px; right:8px; transform:rotate(150deg); }

/* SLIDE 2 */
.s2 { background:var(--olive); }
.s2 .hdr { text-align:center; margin-bottom:18px; padding:0 24px; }
.s2 .hdr p { font-size:11px; letter-spacing:3px; color:var(--blush); text-transform:uppercase; margin-bottom:8px; }
.s2 .hdr h2 { font-family:Georgia,'Times New Roman',serif; font-size:26px; color:var(--cream); line-height:1.2; }
.act-card { background:rgba(255,255,255,0.09); border:1px solid rgba(255,255,255,0.16); border-radius:18px; padding:16px 20px; width:290px; margin-bottom:12px; display:flex; align-items:flex-start; gap:14px; }
.act-icon { font-size:30px; flex-shrink:0; }
.act-text h3 { color:var(--gold); font-size:13px; letter-spacing:1.5px; text-transform:uppercase; margin-bottom:3px; }
.act-text p { color:rgba(245,239,224,0.75); font-size:11.5px; line-height:1.5; }
.kit-btn { margin-top:6px; background:rgba(255,255,255,0.14); border:1.5px solid rgba(255,255,255,0.38); color:var(--cream); font-family:'Helvetica Neue',Arial,sans-serif; font-size:12px; font-weight:700; padding:11px 22px; border-radius:50px; cursor:pointer; display:flex; align-items:center; gap:7px; -webkit-tap-highlight-color:transparent; }
.kit-btn:active { background:rgba(255,255,255,0.3); transform:scale(0.97); }

/* SLIDE 3 */
.s3 { background:var(--cream); }
.top-band { position:absolute; top:0; left:0; right:0; height:155px; background:var(--terracotta); border-radius:0 0 55px 55px; }
.s3 .content { position:relative; text-align:center; padding:0 24px; width:100%; }
.s3-title { font-family:Georgia,'Times New Roman',serif; font-size:30px; color:var(--cream); margin-top:-76px; margin-bottom:20px; }
.info-grid { display:grid; grid-template-columns:1fr 1fr; gap:10px; width:100%; }
.ibox { background:white; border-radius:14px; padding:12px 10px; box-shadow:0 4px 16px rgba(0,0,0,0.07); text-align:center; }
.ibox .ico { font-size:20px; margin-bottom:3px; }
.ibox .lbl { font-size:10px; color:var(--terracotta); letter-spacing:1.5px; text-transform:uppercase; }
.ibox .val { font-size:12px; font-weight:700; color:var(--dark); margin-top:2px; line-height:1.3; }
.price-row { display:flex; gap:10px; margin-top:10px; width:100%; }
.price-wrap { flex:1; position:relative; }
.pbox { width:100%; border-radius:14px; padding:13px 10px; text-align:center; }
.pbox.solo { background:var(--olive); }
.pbox.couple { background:var(--terracotta); }
.pbox .pl { font-size:10px; letter-spacing:1.5px; text-transform:uppercase; color:rgba(255,255,255,0.72); }
.pbox .pa { font-family:Georgia,'Times New Roman',serif; font-size:26px; color:white; font-weight:900; }
.pbox .ps { font-size:10px; color:rgba(255,255,255,0.6); }
.ibtn { position:absolute; top:7px; right:7px; width:22px; height:22px; border-radius:50%; background:rgba(255,255,255,0.28); border:1.5px solid rgba(255,255,255,0.65); color:white; font-size:11px; font-weight:900; cursor:pointer; display:flex; align-items:center; justify-content:center; font-family:serif; padding:0; line-height:1; -webkit-tap-highlight-color:transparent; }
.ibtn:active { background:rgba(255,255,255,0.5); }

/* SLIDE 4 */
.s4 { background:var(--dark); }
.sparkle-bg { position:absolute; inset:0; pointer-events:none; overflow:hidden; }
.sparkle { position:absolute; width:4px; height:4px; border-radius:50%; background:var(--gold); opacity:0; animation:twinkle 3s infinite; }
@keyframes twinkle { 0%,100%{opacity:0;transform:scale(0.5);}50%{opacity:0.8;transform:scale(1.5);} }
.s4 .content { position:relative; text-align:center; padding:24px; }
.gift-badge { width:68px; height:68px; border-radius:50%; background:linear-gradient(135deg,var(--gold),var(--terracotta)); display:flex; align-items:center; justify-content:center; font-size:30px; margin:0 auto 16px; box-shadow:0 0 30px rgba(200,155,60,0.4); }
.s4 h2 { font-family:Georgia,'Times New Roman',serif; font-size:28px; color:var(--cream); line-height:1.2; margin-bottom:10px; }
.s4 h2 span { color:var(--gold); font-style:italic; }
.s4 p { color:rgba(245,239,224,0.65); font-size:12px; line-height:1.6; margin-bottom:20px; }
.cta-btn { display:block; width:100%; text-align:center; background:linear-gradient(135deg,var(--terracotta),var(--gold)); color:white; font-family:'Helvetica Neue',Arial,sans-serif; font-size:13px; letter-spacing:2px; text-transform:uppercase; font-weight:700; padding:15px; border-radius:50px; border:none; cursor:pointer; text-decoration:none; box-shadow:0 8px 24px rgba(193,82,42,0.4); animation:pulse 2s ease-in-out infinite; -webkit-tap-highlight-color:transparent; }
@keyframes pulse { 0%,100%{box-shadow:0 8px 24px rgba(193,82,42,0.4);}50%{box-shadow:0 12px 36px rgba(193,82,42,0.7);} }
.winners-row { display:flex; justify-content:center; gap:6px; margin-top:14px; flex-wrap:wrap; }
.w-chip { background:rgba(255,255,255,0.07); border:1px solid rgba(255,255,255,0.12); border-radius:50px; padding:5px 11px; font-size:10px; color:var(--cream); letter-spacing:1px; }
.contact-row { margin-top:14px; color:rgba(245,239,224,0.45); font-size:10.5px; letter-spacing:0.5px; line-height:1.6; }
.contact-row strong { color:var(--blush); }

/* ANIMATIONS */
.slide.active .animate-up { animation:slideUp 0.6s ease forwards; }
.slide.active .animate-up:nth-child(2) { animation-delay:0.13s; }
.slide.active .animate-up:nth-child(3) { animation-delay:0.26s; }
.slide.active .animate-up:nth-child(4) { animation-delay:0.39s; }
.slide.active .animate-up:nth-child(5) { animation-delay:0.52s; }
@keyframes slideUp { from{opacity:0;transform:translateY(20px);}to{opacity:1;transform:translateY(0);} }
.animate-up { opacity:0; }

/* DOTS & CONTROLS */
.dots { display:flex; gap:7px; margin-top:18px; }
.dot { width:7px; height:7px; border-radius:50%; background:rgba(255,255,255,0.25); transition:background 0.3s,transform 0.3s; }
.dot.active { background:var(--terracotta); transform:scale(1.35); }
.controls { margin-top:14px; display:flex; align-items:center; gap:16px; }
.ctrl-btn { background:rgba(255,255,255,0.1); border:1px solid rgba(255,255,255,0.2); color:white; font-size:18px; width:44px; height:44px; border-radius:50%; cursor:pointer; display:flex; align-items:center; justify-content:center; -webkit-tap-highlight-color:transparent; }
.ctrl-btn:active { background:rgba(255,255,255,0.25); }
.play-btn { width:54px; height:54px; font-size:22px; background:var(--terracotta); border-color:var(--terracotta); }
.caption { color:rgba(255,255,255,0.35); font-size:11px; margin-top:10px; letter-spacing:1px; }

/* MODALS - fixed to viewport, z-index max, works everywhere */
.moverlay { display:none; position:fixed; top:0; left:0; right:0; bottom:0; width:100%; height:100%; z-index:99999; background:rgba(0,0,0,0.7); -webkit-backdrop-filter:blur(4px); backdrop-filter:blur(4px); align-items:center; justify-content:center; padding:20px; }
.moverlay.open { display:flex; }
.mbox { background:var(--cream); border-radius:22px; width:100%; max-width:340px; max-height:88vh; overflow-y:auto; box-shadow:0 28px 70px rgba(0,0,0,0.5); animation:popIn 0.3s cubic-bezier(.22,.68,0,1.2) forwards; }
@keyframes popIn { from{opacity:0;transform:scale(0.88) translateY(20px);}to{opacity:1;transform:scale(1) translateY(0);} }
.mhead { padding:18px 20px 14px; border-radius:22px 22px 0 0; position:relative; }
.mhead.tc { background:var(--terracotta); }
.mhead.ol { background:var(--olive); }
.mhead h3 { font-family:Georgia,'Times New Roman',serif; font-size:19px; color:var(--cream); line-height:1.25; }
.mhead p { font-size:11px; color:rgba(245,239,224,0.8); margin-top:3px; }
.mclose { position:absolute; top:13px; right:14px; background:rgba(255,255,255,0.22); border:none; color:white; width:30px; height:30px; border-radius:50%; font-size:16px; cursor:pointer; display:flex; align-items:center; justify-content:center; -webkit-tap-highlight-color:transparent; }
.mclose:active { background:rgba(255,255,255,0.45); }
.mbody { padding:16px 16px 22px; }
.vrow { display:flex; justify-content:space-between; align-items:center; padding:9px 12px; border-radius:10px; margin-bottom:7px; background:white; box-shadow:0 2px 8px rgba(0,0,0,0.05); }
.vitm { display:flex; align-items:center; gap:8px; }
.vico { font-size:17px; }
.vnm { font-size:11.5px; color:var(--dark); font-weight:600; max-width:160px; line-height:1.3; }
.vprc { font-size:11px; color:var(--terracotta); font-weight:700; background:rgba(193,82,42,0.1); padding:3px 9px; border-radius:20px; white-space:nowrap; }
.vtotal { background:var(--olive); border-radius:12px; padding:13px 16px; margin-top:10px; display:flex; justify-content:space-between; align-items:center; }
.vtl { color:var(--cream); font-size:12px; letter-spacing:1px; text-transform:uppercase; }
.vta { font-family:Georgia,'Times New Roman',serif; font-size:24px; color:var(--gold); font-weight:900; }
.vnote { margin-top:10px; text-align:center; font-size:11px; color:var(--terracotta); font-weight:700; background:rgba(193,82,42,0.08); padding:9px 12px; border-radius:10px; }
.krow { display:flex; align-items:flex-start; gap:11px; padding:10px 12px; border-radius:10px; margin-bottom:7px; background:white; box-shadow:0 2px 8px rgba(0,0,0,0.05); }
.kico { font-size:20px; flex-shrink:0; margin-top:1px; }
.knm { font-size:12px; font-weight:700; color:var(--dark); }
.kdc { font-size:10.5px; color:#888; margin-top:2px; }
.knote { margin-top:10px; text-align:center; font-size:11px; color:var(--olive); font-weight:700; background:rgba(74,94,47,0.09); padding:9px 12px; border-radius:10px; }
</style>
</head>
<body>
<div class="page">

  <div class="phone">
    <div class="phone-inner"></div>

    <!-- SLIDE 1 -->
    <div class="slide s1 active" id="slide-0">
      <div class="blob blob1"></div><div class="blob blob2"></div>
      <div class="leaf-deco tl">🌿</div><div class="leaf-deco br">🌿</div>
      <div class="content">
        <div class="eyebrow animate-up">✦ A Creative Experience ✦</div>
        <div class="big-title animate-up">craft<span>fiestá</span></div>
        <div class="tagline animate-up">A Clay &amp; Mirror Painting<br>Workshop in Prayagraj</div>
        <div class="pill animate-up">Create · Reflect · Take It Home</div>
      </div>
    </div>

    <!-- SLIDE 2 -->
    <div class="slide s2" id="slide-1">
      <div class="hdr animate-up"><p>What you'll do</p><h2>Two crafts,<br>one unforgettable evening</h2></div>
      <div class="act-card animate-up">
        <div class="act-icon">🏺</div>
        <div class="act-text"><h3>Air Dry Clay</h3><p>Mold, shape and sculpt your very own masterpiece from scratch.</p></div>
      </div>
      <div class="act-card animate-up">
        <div class="act-icon">🪞</div>
        <div class="act-text"><h3>Mirror Painting</h3><p>Paint floral designs on a mirror — a piece that brightens your space.</p></div>
      </div>
      <button class="kit-btn animate-up" onclick="showM('kitModal')">📦 View Your Physical Material Kit</button>
    </div>

    <!-- SLIDE 3 -->
    <div class="slide s3" id="slide-2">
      <div class="top-band"></div>
      <div class="content">
        <h2 class="s3-title animate-up">📍 Mark Your Calendar</h2>
        <div class="info-grid">
          <div class="ibox animate-up"><div class="ico">📅</div><div class="lbl">Date</div><div class="val">21 June<br>Sunday</div></div>
          <div class="ibox animate-up"><div class="ico">🕓</div><div class="lbl">Time</div><div class="val">4:00 PM –<br>7:00 PM</div></div>
          <div class="ibox animate-up" style="grid-column:span 2"><div class="ico">☕</div><div class="lbl">Venue</div><div class="val">Cannington Cafe (near Pizza Hut), Prayagraj</div></div>
        </div>
        <div class="price-row">
          <div class="price-wrap animate-up">
            <div class="pbox solo"><div class="pl">Solo</div><div class="pa">₹549</div><div class="ps">1 Person</div></div>
            <button class="ibtn" onclick="showM('valueModal')">ⓘ</button>
          </div>
          <div class="price-wrap animate-up">
            <div class="pbox couple"><div class="pl">Couple</div><div class="pa">₹999</div><div class="ps">2 People</div></div>
            <button class="ibtn" onclick="showM('valueModal')">ⓘ</button>
          </div>
        </div>
      </div>
    </div>

    <!-- SLIDE 4 -->
    <div class="slide s4" id="slide-3">
      <div class="sparkle-bg" id="sparkles"></div>
      <div class="content">
        <div class="gift-badge animate-up">🎁</div>
        <h2 class="animate-up">Win a <span>Surprise Gift</span> for the best creation!</h2>
        <p class="animate-up">Judged on creativity, originality, craftsmanship &amp; presentation. Featured on Instagram too!</p>
        <a href="https://wa.me/919580181758?text=Hey!%20I%20saw%20your%20interactive%20reel%20and%20want%20to%20book%20a%20spot%20for%20Craft%20Fiesta%20this%20Sunday." target="_blank" class="cta-btn animate-up">📲 Book Your Spot Now</a>
        <div class="winners-row animate-up">
          <div class="w-chip">🏆 Surprise Gift</div>
          <div class="w-chip">📸 Featured on Instagram</div>
        </div>
        <div class="contact-row animate-up">
          <strong>@saahil_0704 · @thepriyanshiagarwal · @hanshika_srivastava18</strong><br>
          9580181758 / 808183822
        </div>
      </div>
    </div>
  </div>

  <div class="dots" id="dots">
    <div class="dot active"></div><div class="dot"></div><div class="dot"></div><div class="dot"></div>
  </div>
  <div class="controls">
    <button class="ctrl-btn" id="prevBtn">&#8249;</button>
    <button class="ctrl-btn play-btn" id="playBtn">&#9654;</button>
    <button class="ctrl-btn" id="nextBtn">&#8250;</button>
  </div>
  <div class="caption">TAP ARROWS OR AUTO-PLAY</div>
</div>

<!-- KIT MODAL -->
<div class="moverlay" id="kitModal">
  <div class="mbox">
    <div class="mhead ol">
      <button class="mclose" onclick="hideM('kitModal')">&#10005;</button>
      <h3>📦 Your Material Kit</h3>
      <p>Everything is provided — bring only yourself!</p>
    </div>
    <div class="mbody">
      <div class="krow"><div class="kico">🪞</div><div><div class="knm">1 × Custom Wavy-Edge Mirror</div><div class="kdc">Aesthetic frame, ready to paint</div></div></div>
      <div class="krow"><div class="kico">🏺</div><div><div class="knm">2 × Packets of Air-Dry Sculpting Clay</div><div class="kdc">Non-toxic, premium quality</div></div></div>
      <div class="krow"><div class="kico">🎨</div><div><div class="knm">1 × Set of 6 Acrylic Paints</div><div class="kdc">Premium pigmented colors</div></div></div>
      <div class="krow"><div class="kico">🖌️</div><div><div class="knm">2 × Professional Paintbrushes</div><div class="kdc">Fine tip &amp; flat tip included</div></div></div>
      <div class="krow"><div class="kico">🔧</div><div><div class="knm">1 × Clay Sculpting Tool</div><div class="kdc">For fine detailing &amp; shaping</div></div></div>
      <div class="krow"><div class="kico">✨</div><div><div class="knm">1 × High-Gloss Varnish</div><div class="kdc">To seal &amp; protect your finished mirror</div></div></div>
      <div class="knote">✅ No supplies needed — we've got it all covered!</div>
    </div>
  </div>
</div>

<!-- VALUE MODAL -->
<div class="moverlay" id="valueModal">
  <div class="mbox">
    <div class="mhead tc">
      <button class="mclose" onclick="hideM('valueModal')">&#10005;</button>
      <h3>💎 What's Included?</h3>
      <p>See the real value packed into your ticket</p>
    </div>
    <div class="mbody">
      <div class="vrow"><div class="vitm"><span class="vico">🪞</span><span class="vnm">Premium Wavy Mirror</span></div><span class="vprc">₹150 value</span></div>
      <div class="vrow"><div class="vitm"><span class="vico">🏺</span><span class="vnm">Fevicryl Mouldit Clay &amp; Tools</span></div><span class="vprc">₹100 value</span></div>
      <div class="vrow"><div class="vitm"><span class="vico">🎨</span><span class="vnm">Acrylic Paint Palette &amp; Brush Set</span></div><span class="vprc">₹80 value</span></div>
      <div class="vrow"><div class="vitm"><span class="vico">☕</span><span class="vnm">Welcome Drink &amp; Cafe Space</span></div><span class="vprc">₹120 value</span></div>
      <div class="vrow"><div class="vitm"><span class="vico">🎁</span><span class="vnm">Surprise Gift Pool &amp; Certificate</span></div><span class="vprc">₹100 value</span></div>
      <div class="vtotal"><span class="vtl">Total Value</span><span class="vta">₹550+</span></div>
      <div class="vnote">🎉 Expert instruction &amp; experience — included FREE!</div>
    </div>
  </div>
</div>

<script>
function showM(id) {
  var el = document.getElementById(id);
  el.classList.add('open');
}
function hideM(id) {
  document.getElementById(id).classList.remove('open');
}
document.querySelectorAll('.moverlay').forEach(function(o) {
  o.addEventListener('click', function(e) { if(e.target===o) hideM(o.id); });
});

var slides=document.querySelectorAll('.slide'), dots=document.querySelectorAll('.dot');
var playBtn=document.getElementById('playBtn'), total=slides.length;
var current=0, playing=false, timer=null;

var sb=document.getElementById('sparkles');
for(var i=0;i<28;i++){var s=document.createElement('div');s.className='sparkle';s.style.left=(Math.random()*100)+'%';s.style.top=(Math.random()*100)+'%';s.style.animationDelay=(Math.random()*3)+'s';s.style.animationDuration=(2+Math.random()*2)+'s';sb.appendChild(s);}

function goTo(n){
  slides[current].classList.remove('active'); dots[current].classList.remove('active');
  current=(n+total)%total;
  slides[current].classList.add(('active'); dots[current].classList.add('active');
  slides[current].querySelectorAll('.animate-up').forEach(function(el){el.style.animation='none';el.offsetHeight;el.style.animation='';});
}
document.getElementById('nextBtn').addEventListener('click',function(){goTo(current+1);});
document.getElementById('prevBtn').addEventListener('click',function(){goTo(current-1);});
function startPlay(){playing=true;playBtn.innerHTML='&#9646;&#9646;';timer=setInterval(function(){goTo(current+1);},2800);}
function stopPlay(){playing=false;playBtn.innerHTML='&#9654;';clearInterval(timer);}
playBtn.addEventListener('click',function(){playing?stopPlay():startPlay();});
startPlay();
</script>
</body>
</html>