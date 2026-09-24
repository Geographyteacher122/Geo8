<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
<meta name="theme-color" content="#0a607f">
<title>بوصلة الكنز — معالجة البيانات الجغرافية</title>

<style>
:root{
  --navy:#0b2638;
  --deep:#0a4b67;
  --sea:#1588ad;
  --sky:#79d0df;
  --sand:#e6c989;
  --sand2:#f5e5bd;
  --green:#3b916c;
  --green2:#7ac77f;
  --gold:#f2c94c;
  --gold2:#ffe99b;
  --cream:#fffaf0;
  --ink:#163242;
  --danger:#df6b62;
  --success:#3aa579;
  --panel:rgba(10,35,49,.92);
  --shadow:0 20px 60px rgba(2,17,27,.30);
}

*{box-sizing:border-box}

html,body{
  margin:0;
  width:100%;
  min-height:100%;
  font-family:"Segoe UI",Tahoma,Arial,sans-serif;
  background:var(--navy);
  color:#fff;
  -webkit-user-select:none;
  user-select:none;
  -webkit-touch-callout:none;
  overscroll-behavior:none;
}

button,input,select{font:inherit}
button{cursor:pointer;border:0}
.hidden{display:none!important}

.screen{
  height:100svh;
  min-height:100vh;
  width:100%;
  display:none;
  position:relative;
  overflow:hidden;
}

.screen.active{display:flex}

/* =========================================================
   MOTION SYSTEM
========================================================= */

@keyframes floatSoft{
  0%,100%{transform:translateY(0)}
  50%{transform:translateY(-9px)}
}

@keyframes floatSoft2{
  0%,100%{transform:translateY(0) rotate(0)}
  50%{transform:translateY(-7px) rotate(2deg)}
}

@keyframes glowPulse{
  0%,100%{
    box-shadow:0 0 0 0 rgba(242,201,76,0);
  }
  50%{
    box-shadow:0 0 0 12px rgba(242,201,76,.08);
  }
}

@keyframes shineMove{
  0%{background-position:-250px 0}
  100%{background-position:250px 0}
}

@keyframes routeDash{
  to{stroke-dashoffset:-70}
}

@keyframes unlockPop{
  0%{
    transform:translate(-50%,-50%) scale(.65) rotate(-8deg);
    opacity:.3;
  }
  55%{
    transform:translate(-50%,-50%) scale(1.15) rotate(3deg);
    opacity:1;
  }
  100%{
    transform:translate(-50%,-50%) scale(1) rotate(0);
    opacity:1;
  }
}

@keyframes questionIn{
  0%{
    opacity:0;
    transform:translate(50%,45px) scale(.96);
  }
  100%{
    opacity:1;
    transform:translate(50%,0) scale(1);
  }
}

@keyframes answerIn{
  0%{
    opacity:0;
    transform:translateY(12px);
  }
  100%{
    opacity:1;
    transform:translateY(0);
  }
}

@keyframes correctPop{
  0%{transform:scale(1)}
  35%{transform:scale(1.05)}
  65%{transform:scale(.98)}
  100%{transform:scale(1)}
}

@keyframes wrongShake{
  0%,100%{transform:translateX(0)}
  20%{transform:translateX(7px)}
  40%{transform:translateX(-7px)}
  60%{transform:translateX(5px)}
  80%{transform:translateX(-4px)}
}

@keyframes rolePop{
  0%{
    opacity:0;
    transform:scale(.7) translateY(10px);
  }
  65%{
    opacity:1;
    transform:scale(1.07) translateY(-2px);
  }
  100%{
    transform:scale(1) translateY(0);
  }
}

@keyframes compassFloat{
  0%,100%{
    transform:rotate(-4deg) translateY(0);
  }
  50%{
    transform:rotate(7deg) translateY(-8px);
  }
}

@keyframes palmWind{
  0%,100%{transform:rotate(-2deg)}
  50%{transform:rotate(4deg)}
}

@keyframes boatFloat{
  0%,100%{transform:translateY(0) rotate(-1deg)}
  50%{transform:translateY(-8px) rotate(2deg)}
}

@keyframes waterMove{
  0%{background-position:0 0}
  100%{background-position:120px 55px}
}

@keyframes treasureLight{
  0%,100%{opacity:.25;transform:scale(.85)}
  50%{opacity:.85;transform:scale(1.12)}
}

@keyframes gemFloat{
  0%{
    opacity:0;
    transform:translateY(20px) scale(.3) rotate(45deg);
  }
  30%{
    opacity:1;
  }
  100%{
    opacity:0;
    transform:translateY(-95px) scale(1) rotate(225deg);
  }
}

@keyframes chestOpen{
  0%{transform:rotateX(0)}
  70%{transform:rotateX(-78deg)}
  100%{transform:rotateX(-72deg)}
}

@keyframes resultIn{
  0%{
    opacity:0;
    transform:translateY(20px) scale(.94);
  }
  100%{
    opacity:1;
    transform:translateY(0) scale(1);
  }
}

@keyframes timerPulse{
  50%{transform:scale(1.1)}
}

@keyframes cloudMove{
  from{transform:translateX(0)}
  to{transform:translateX(130vw)}
}

@keyframes waveShift{
  from{background-position:0 0}
  to{background-position:100px 45px}
}

@keyframes sway{
  50%{transform:rotate(4deg)}
}

@keyframes pop{
  0%{
    transform:scale(.3);
    opacity:0
  }
  70%{
    transform:scale(1.08);
    opacity:1
  }
  100%{
    transform:scale(1)
  }
}

@keyframes rise{
  from{
    opacity:0;
    transform:translate(50%,25px)
  }
  to{
    opacity:1;
    transform:translate(50%,0)
  }
}

@keyframes nodePulse{
  50%{
    box-shadow:
      0 0 0 11px rgba(255,255,255,.08),
      0 12px 22px rgba(0,0,0,.26)
  }
}

@keyframes flash{
  0%{opacity:0}
  25%{opacity:1}
  100%{opacity:0}
}

@keyframes confettiFall{
  0%{
    opacity:1;
    transform:translateY(0) rotate(0)
  }
  100%{
    opacity:1;
    transform:translateY(105vh) rotate(780deg)
  }
}

/* =========================================================
   INTRO
========================================================= */

.intro{
  overflow:hidden;
  align-items:center;
  justify-content:center;
  background:
    linear-gradient(
      180deg,
      #73cddf 0 33%,
      #2797b1 50%,
      #0c6b89 100%
    );
}

.intro:before{
  content:"";
  position:absolute;
  inset:0;
  background:
    radial-gradient(
      circle at 50% 30%,
      rgba(255,255,255,.26),
      transparent 32%
    ),
    linear-gradient(
      160deg,
      transparent 62%,
      rgba(255,255,255,.07)
    );
  pointer-events:none;
}

.cloud{
  position:absolute;
  width:180px;
  height:42px;
  background:#ffffffb8;
  border-radius:99px;
  filter:blur(.6px);
  top:13%;
  left:-220px;
  animation:cloudMove 23s linear infinite;
}

.cloud:before,
.cloud:after{
  content:"";
  position:absolute;
  background:inherit;
  border-radius:50%;
}

.cloud:before{
  width:72px;
  height:72px;
  left:33px;
  top:-34px;
}

.cloud:after{
  width:96px;
  height:96px;
  right:18px;
  top:-51px;
}

.cloud.c2{
  top:25%;
  animation-duration:29s;
  animation-delay:8s;
}

.ocean-sheen{
  position:absolute;
  bottom:0;
  left:0;
  right:0;
  height:58%;
  background:
    repeating-linear-gradient(
      -8deg,
      transparent 0 15px,
      rgba(255,255,255,.08) 16px 18px
    );
  opacity:.45;
  animation:waveShift 7s linear infinite;
}

.introIsland{
  position:absolute;
  bottom:-13vh;
  left:50%;
  transform:translateX(-50%) rotate(-5deg);
  width:min(1100px,120vw);
  height:48vh;
  filter:drop-shadow(0 25px 40px rgba(0,0,0,.25));
}

.introIsland svg{
  display:block;
  width:100%;
  height:100%;
  overflow:visible;
}

.introTrail{
  position:absolute;
  z-index:1;
  inset:0;
  width:100%;
  height:100%;
  pointer-events:none;
}

.introTrail path{
  fill:none;
  stroke:#ffe799;
  stroke-width:4;
  stroke-linecap:round;
  stroke-dasharray:2 14;
  opacity:.55;
  animation:routeDash 4s linear infinite;
}

.introCompass{
  position:absolute;
  top:6%;
  left:8%;
  font-size:54px;
  z-index:3;
  opacity:.85;
  filter:drop-shadow(0 8px 10px rgba(0,0,0,.25));
  animation:compassFloat 5s ease-in-out infinite;
}

.introBoat{
  position:absolute;
  left:0;
  bottom:20%;
  font-size:46px;
  z-index:2;
  filter:drop-shadow(0 6px 8px rgba(0,0,0,.25));
  animation:sailDrift 17s linear infinite;
}

@keyframes sailDrift{
  0%{transform:translate(-15vw,0) rotate(-2deg)}
  50%{transform:translate(55vw,-10px) rotate(2deg)}
  100%{transform:translate(125vw,0) rotate(-2deg)}
}

.introBird{
  position:absolute;
  left:0;
  font-size:22px;
  z-index:3;
  opacity:.85;
  animation:birdDrift 13s linear infinite;
}

.introBird.b2{
  animation-duration:16s;
  animation-delay:3s;
  font-size:18px;
}

@keyframes birdDrift{
  0%{transform:translate(-10vw,0)}
  100%{transform:translate(120vw,-40px)}
}

.introPeople{
  position:absolute;
  bottom:12%;
  z-index:2;
  font-size:36px;
  filter:drop-shadow(0 6px 6px rgba(0,0,0,.28));
  animation:floatSoft 3.4s ease-in-out infinite;
}

.introPeople.p2{
  font-size:30px;
  animation-delay:.6s;
}

.sparkle{
  position:absolute;
  font-size:22px;
  z-index:5;
  animation:twinkle 2.4s ease-in-out infinite;
}

@keyframes twinkle{
  0%,100%{opacity:.2;transform:scale(.7)}
  50%{opacity:1;transform:scale(1.15)}
}

.palm{
  position:absolute;
  bottom:20%;
  font-size:86px;
  filter:drop-shadow(0 10px 6px rgba(0,0,0,.28));
  animation:palmWind 3.2s ease-in-out infinite;
  z-index:2;
  transform-origin:bottom center;
}

.palm.p1{left:9%}
.palm.p2{
  right:9%;
  animation-delay:1.2s;
}

.introCard{
  position:relative;
  z-index:4;
  width:min(820px,92vw);
  padding:46px 34px;
  border-radius:32px;
  background:
    linear-gradient(
      145deg,
      rgba(7,34,47,.88),
      rgba(10,51,68,.74)
    );
  backdrop-filter:blur(14px);
  border:1px solid rgba(255,255,255,.18);
  box-shadow:var(--shadow);
  text-align:center;
  animation:introCardIn .9s cubic-bezier(.2,.8,.2,1);
}

@keyframes introCardIn{
  from{
    opacity:0;
    transform:translateY(30px) scale(.97);
  }
  to{
    opacity:1;
    transform:translateY(0) scale(1);
  }
}

.eyebrow{
  display:inline-flex;
  align-items:center;
  gap:8px;
  padding:8px 15px;
  border-radius:99px;
  color:#f9e7a4;
  border:1px solid rgba(242,200,75,.35);
  background:rgba(242,200,75,.10);
  font-weight:700;
}

h1{
  font-size:clamp(42px,7vw,76px);
  margin:16px 0 4px;
  line-height:1.05;
  text-shadow:0 8px 24px rgba(0,0,0,.3);
  animation:titleFloat 4s ease-in-out infinite;
}

@keyframes titleFloat{
  0%,100%{transform:translateY(0)}
  50%{transform:translateY(-4px)}
}

.sub{
  font-size:clamp(19px,3vw,29px);
  color:#d9f2f5;
}

.credit{
  margin:24px 0 8px;
  line-height:1.9;
  color:#d1e8ec;
}

.tease{
  font-size:19px;
  color:#f4f9fa;
  margin:18px auto 28px;
  max-width:600px;
}

.btnPrimary{
  padding:15px 30px;
  border-radius:17px;
  background:
    linear-gradient(
      110deg,
      #ffe57c 0%,
      #eab634 45%,
      #ffe57c 65%,
      #eab634 100%
    );
  background-size:300% 100%;
  color:#173040;
  font-weight:900;
  box-shadow:
    0 8px 0 #9f741b,
    0 17px 30px rgba(0,0,0,.23);
  transition:
    transform .18s,
    box-shadow .18s;
  animation:
    shineButton 4s linear infinite,
    buttonBreath 2.5s ease-in-out infinite;
}

@keyframes shineButton{
  0%{background-position:100% 0}
  100%{background-position:-100% 0}
}

@keyframes buttonBreath{
  0%,100%{transform:scale(1)}
  50%{transform:scale(1.025)}
}

.btnPrimary:hover{
  transform:translateY(-3px) scale(1.02);
}

.btnPrimary:active{
  transform:translateY(4px);
  box-shadow:0 4px 0 #9f741b;
}

.btnSecondary{
  padding:12px 20px;
  border-radius:15px;
  background:#254d5f;
  color:#fff;
  border:1px solid rgba(255,255,255,.12);
  transition:.2s;
}

.btnSecondary:hover{
  transform:translateY(-2px);
  background:#2d6175;
}

/* =========================================================
   SETUP
========================================================= */

.setup{
  align-items:center;
  justify-content:center;
  padding:clamp(12px,3vw,26px);
  background:
    radial-gradient(circle at top,#2c687c,#081a28 70%);
}

.setupPanel{
  width:min(980px,95vw);
  max-height:94svh;
  overflow:auto;
  background:rgba(9,37,52,.95);
  border:1px solid rgba(255,255,255,.12);
  border-radius:29px;
  padding:30px;
  box-shadow:var(--shadow);
  animation:introCardIn .55s ease;
}

.setupPanel h2{
  margin:0 0 18px;
  font-size:34px;
}

.setupGrid{
  display:grid;
  grid-template-columns:repeat(2,1fr);
  gap:14px;
}

.field{
  background:#123b4f;
  border-radius:17px;
  padding:14px;
}

.field label{
  display:block;
  font-size:13px;
  color:#b9d8df;
  margin-bottom:7px;
}

.field input,
.field select{
  width:100%;
  background:#082536;
  border:1px solid #355f70;
  color:#fff;
  border-radius:11px;
  padding:11px;
  outline:none;
}

.field input:focus,
.field select:focus{
  border-color:#6ed1df;
  box-shadow:0 0 0 3px rgba(110,209,223,.1);
}

.switchRow{
  display:flex;
  gap:10px;
  flex-wrap:wrap;
  margin-top:14px;
}

.switch{
  display:flex;
  align-items:center;
  gap:8px;
  background:#0c2d3d;
  padding:10px 13px;
  border-radius:12px;
  color:#dceff2;
  transition:.2s;
}

.switch:hover{
  transform:translateY(-2px);
}

.switch input{
  accent-color:#f2c84b;
}

.teamFields{
  display:grid;
  grid-template-columns:repeat(4,1fr);
  gap:10px;
}

.teamField{
  padding:11px;
  border-radius:14px;
  background:#0b2c3c;
  border-top:4px solid;
}

.setupActions{
  display:flex;
  justify-content:center;
  gap:10px;
  margin-top:22px;
}

/* =========================================================
   ROUTE MAP
========================================================= */

.route{
  flex-direction:column;
  gap:18px;
  padding:clamp(14px,2.5vw,28px);
  background:
    radial-gradient(circle at 50% 5%,#2f778b,#071b2a 78%);
  overflow:hidden;
}

.routeHeader{
  width:min(1250px,96vw);
  margin:0 auto;
  display:flex;
  align-items:center;
  justify-content:space-between;
  gap:18px;
  animation:introCardIn .6s ease;
}

.routeKicker{
  color:#f5d77a;
  font-weight:900;
  font-size:13px;
}

.routeHeader h2{
  margin:4px 0;
  font-size:clamp(28px,4vw,46px);
}

.routeHeader p{
  margin:0;
  color:#bfe0e6;
  line-height:1.7;
}

.routeBadge{
  white-space:nowrap;
  background:#123b4f;
  border:1px solid #ffffff18;
  padding:12px 16px;
  border-radius:15px;
  color:#ffe69a;
  font-weight:800;
  box-shadow:0 10px 26px #0003;
  animation:floatSoft 3s ease-in-out infinite;
}

.routeMap{
  position:relative;
  flex:1;
  width:min(1250px,96vw);
  min-height:0;
  margin:0 auto;
  border-radius:30px;
  overflow:hidden;
  background:linear-gradient(150deg,#56b7c7,#1d849e);
  box-shadow:
    inset 0 0 0 1px #ffffff25,
    0 22px 55px #0005;
  animation:mapAppear .8s ease;
}

@keyframes mapAppear{
  from{
    opacity:0;
    transform:scale(.97);
  }
  to{
    opacity:1;
    transform:scale(1);
  }
}

.routeOcean{
  position:absolute;
  inset:0;
  background:
    repeating-radial-gradient(
      ellipse at 18% 18%,
      transparent 0 28px,
      #ffffff09 30px 32px
    );
  opacity:.8;
  animation:waterMove 9s linear infinite;
}

.routeIsland{
  position:absolute;
  animation:islandFloat 6s ease-in-out infinite;
  filter:drop-shadow(0 16px 22px rgba(4,20,28,.28));
}

.routeIsland svg{
  display:block;
  width:100%;
  height:100%;
  overflow:visible;
}

@keyframes islandFloat{
  0%,100%{transform:rotate(-5deg) translateY(0)}
  50%{transform:rotate(-4deg) translateY(-3px)}
}

.islandA{
  width:72%;
  height:66%;
  left:14%;
  top:19%;
  transform:rotate(-5deg);
}

.islandB{
  width:24%;
  height:22%;
  left:3%;
  top:8%;
  transform:rotate(7deg);
  animation-delay:1s;
  opacity:.92;
}

.treasureMark{
  position:absolute;
  width:56px;
  height:50px;
  transform:translate(-50%,-50%);
  pointer-events:none;
  z-index:3;
  filter:drop-shadow(0 10px 14px rgba(0,0,0,.35));
  animation:floatSoft 3.6s ease-in-out infinite;
}

.routeFeature{
  position:absolute;
  z-index:2;
  filter:drop-shadow(0 9px 6px #0004);
  user-select:none;
}

.palmR{
  right:7%;
  bottom:12%;
  font-size:76px;
  animation:palmWind 3.4s ease-in-out infinite;
  transform-origin:bottom center;
}

.palmL{
  left:5%;
  bottom:23%;
  font-size:68px;
  animation:palmWind 3.8s ease-in-out infinite reverse;
  transform-origin:bottom center;
}

.mountainR{
  right:17%;
  top:14%;
  font-size:72px;
  animation:floatSoft2 5s ease-in-out infinite;
}

.caveL{
  left:15%;
  bottom:14%;
  font-size:65px;
  animation:floatSoft 4.5s ease-in-out infinite;
}

.routePath{
  position:absolute;
  z-index:4;
  inset:0;
  width:100%;
  height:100%;
  pointer-events:none;
}

.routePath path{
  fill:none;
  stroke:#ffe799;
  stroke-width:11;
  stroke-linecap:round;
  stroke-dasharray:10 17;
  filter:drop-shadow(0 0 7px #9e772a77);
  animation:routeDash 3s linear infinite;
}

.routeStation{
  position:absolute;
  z-index:8;
  width:82px;
  height:82px;
  border-radius:25px;
  transform:translate(-50%,-50%);
  display:flex;
  align-items:center;
  justify-content:center;
  color:#fff;
  font-weight:1000;
  background:linear-gradient(145deg,#123e51,#0b2839);
  border:4px solid #d9eef1;
  box-shadow:
    0 14px 24px #0005,
    inset 0 1px #fff3;
  transition:
    transform .35s cubic-bezier(.2,.8,.2,1),
    filter .35s,
    opacity .35s,
    box-shadow .35s;
}

.routeStation:hover{
  transform:translate(-50%,-50%) scale(1.07);
}

.routeStation span{
  font-size:23px;
}

.routeStation small{
  position:absolute;
  top:88px;
  white-space:nowrap;
  background:#092637e8;
  padding:7px 10px;
  border-radius:9px;
  font-size:11px;
  box-shadow:0 7px 17px #0003;
  transition:.25s;
}

.routeStation.active{
  background:linear-gradient(145deg,#2ba17e,#17695d);
  animation:
    nodePulse 2s infinite,
    floatSoft 3.2s ease-in-out infinite;
}

.routeStation.done{
  background:linear-gradient(145deg,#d1a72c,#8f6810);
  border-color:#ffe58b;
}

.routeStation.done:after{
  content:"✓";
  position:absolute;
  inset:-9px;
  border:2px solid rgba(255,233,155,.5);
  border-radius:30px;
  animation:glowPulse 2s infinite;
}

.routeStation.locked{
  opacity:.58;
  filter:saturate(.4);
}

.routeStation.unlocking{
  animation:unlockPop .75s cubic-bezier(.2,.8,.2,1);
}

.rs1{left:82%;top:71%}
.rs2{left:67%;top:52%}
.rs3{left:53%;top:69%}
.rs4{left:38%;top:49%}
.rs5{left:23%;top:61%}

.treasureStation{
  left:12%;
  top:28%;
  border-color:#ffe38b;
  background:linear-gradient(145deg,#bd8f25,#6f4d10);
}

.routeCompass{
  position:absolute;
  right:4%;
  top:7%;
  z-index:7;
  font-size:53px;
  animation:compassFloat 4s ease-in-out infinite;
  filter:drop-shadow(0 8px 4px #0004);
}

.routeHint{
  position:absolute;
  z-index:9;
  left:50%;
  bottom:18px;
  transform:translateX(-50%);
  background:#092637dc;
  border:1px solid #ffffff1a;
  color:#ffe89a;
  padding:10px 16px;
  border-radius:13px;
  backdrop-filter:blur(7px);
  white-space:nowrap;
  box-shadow:0 10px 25px #0004;
  animation:floatSoft 3s ease-in-out infinite;
}

.routeActions{
  display:flex;
  justify-content:center;
  gap:12px;
}

/* =========================================================
   COUNTDOWN
========================================================= */

.countdown{
  align-items:center;
  justify-content:center;
  text-align:center;
  background:
    radial-gradient(circle at 50% 45%,#173f52,#071b28 70%);
}

.countNo{
  font-size:clamp(110px,20vw,220px);
  font-weight:1000;
  line-height:1;
  text-shadow:0 15px 35px #000;
  animation:pop .75s ease;
}

.countHint{
  font-size:24px;
  color:#cdebf0;
}

/* =========================================================
   GAME
========================================================= */

.game{
  flex-direction:column;
  background:#0f748f;
  overflow:hidden;
}

.game.active{
  display:flex;
}

.topHud{
  position:fixed;
  z-index:30;
  top:12px;
  left:12px;
  right:12px;
  display:flex;
  justify-content:space-between;
  align-items:flex-start;
  gap:10px;
  pointer-events:none;
}

.hudGroup{
  display:flex;
  gap:8px;
  flex-wrap:wrap;
}

.hudBox{
  pointer-events:auto;
  padding:9px 13px;
  border-radius:14px;
  background:rgba(7,30,42,.88);
  backdrop-filter:blur(10px);
  border:1px solid rgba(255,255,255,.10);
  box-shadow:0 8px 25px rgba(0,0,0,.20);
  font-size:13px;
  transition:.25s;
}

.hudBox b{
  color:#ffe492;
}

.hudBtn{
  cursor:pointer;
  color:#fff;
}

.hudBtn:hover{
  transform:translateY(-2px);
}

.timerBox b{
  color:#ffe08b;
  min-width:48px;
  display:inline-block;
  text-align:center;
}

.timerBox.warning b{
  color:#ff9e7f;
  animation:timerPulse .65s infinite;
}

.world{
  position:relative;
  flex:1;
  min-height:0;
  overflow:hidden;
  background:
    linear-gradient(
      180deg,
      #7acbda 0 34%,
      #1684a4 34% 100%
    );
}

.world:after{
  content:"";
  position:absolute;
  inset:0;
  background:
    radial-gradient(
      circle at 55% 30%,
      rgba(255,255,255,.15),
      transparent 40%
    );
  pointer-events:none;
}

.mapViewport{
  position:absolute;
  inset:60px 24px 22px;
  border-radius:30px;
  overflow:hidden;
  box-shadow:
    inset 0 0 0 1px rgba(255,255,255,.16),
    0 25px 65px rgba(3,24,33,.25);
  background:linear-gradient(155deg,#3fa9ba,#1f8198);
}

.mapScene{
  position:absolute;
  inset:0;
  transform-origin:center;
  transition:transform 1s cubic-bezier(.2,.8,.2,1);
}

.waterRipples{
  position:absolute;
  inset:0;
  background:
    repeating-radial-gradient(
      ellipse at 30% 25%,
      transparent 0 28px,
      rgba(255,255,255,.05) 30px 32px
    );
  opacity:.65;
  animation:waterMove 8s linear infinite;
}

.islandShape{
  position:absolute;
  width:82%;
  height:76%;
  left:9%;
  top:12%;
  transform:rotate(-7deg);
  filter:drop-shadow(0 20px 26px rgba(4,20,28,.30));
  animation:islandFloatGame 7s ease-in-out infinite;
}

.islandShape svg{
  display:block;
  width:100%;
  height:100%;
  overflow:visible;
}

@keyframes islandFloatGame{
  0%,100%{transform:rotate(-7deg) translateY(0)}
  50%{transform:rotate(-6.5deg) translateY(-3px)}
}

.islandShadow{
  position:absolute;
  width:70%;
  height:16%;
  left:15%;
  top:69%;
  background:rgba(54,77,40,.18);
  filter:blur(19px);
  transform:rotate(-6deg);
  border-radius:50%;
}

.river{
  position:absolute;
  width:35%;
  height:13%;
  right:16%;
  top:46%;
  background:linear-gradient(180deg,#2aa5bb,#187f9e);
  border-radius:65% 35% 45% 55%;
  transform:rotate(-19deg);
  box-shadow:inset 0 0 20px rgba(0,0,0,.14);
  animation:riverFlow 5s linear infinite;
}

@keyframes riverFlow{
  0%,100%{filter:brightness(1)}
  50%{filter:brightness(1.12)}
}

.feature{
  position:absolute;
  z-index:2;
  filter:drop-shadow(0 8px 5px rgba(0,0,0,.20));
  user-select:none;
}

.mountains{
  left:65%;
  top:17%;
  font-size:78px;
  animation:floatSoft2 5s ease-in-out infinite;
}

.treesA{
  left:17%;
  top:22%;
  font-size:60px;
  animation:palmWind 3.4s ease-in-out infinite;
  transform-origin:bottom center;
}

.treesB{
  left:25%;
  top:38%;
  font-size:64px;
  animation:floatSoft 4.2s ease-in-out infinite;
}

.treesC{
  right:24%;
  bottom:21%;
  font-size:61px;
  animation:palmWind 4s ease-in-out infinite reverse;
  transform-origin:bottom center;
}

.caveF{
  right:20%;
  bottom:12%;
  font-size:70px;
  animation:floatSoft2 4.7s ease-in-out infinite;
}

.boatF{
  left:9%;
  bottom:13%;
  font-size:62px;
  animation:boatFloat 3.5s ease-in-out infinite;
}

.bridgeF{
  left:46%;
  top:50%;
  font-size:70px;
  animation:floatSoft 4s ease-in-out infinite;
}

.compassF{
  right:8%;
  top:10%;
  font-size:62px;
  animation:compassFloat 4s ease-in-out infinite;
}

.routeGlow{
  position:absolute;
  z-index:3;
  left:14%;
  top:38%;
  width:69%;
  height:27%;
  border-bottom:8px dashed rgba(255,231,139,.82);
  border-radius:50%;
  transform:rotate(-7deg);
  filter:drop-shadow(0 0 8px rgba(255,227,112,.32));
  animation:routeDash 3s linear infinite;
}

.station{
  position:absolute;
  z-index:8;
  width:92px;
  height:92px;
  transform:translate(-50%,-50%);
  border-radius:27px;
  background:linear-gradient(145deg,#163f52,#0b2637);
  border:4px solid #d3eef0;
  box-shadow:
    0 12px 22px rgba(0,0,0,.26),
    inset 0 1px rgba(255,255,255,.15);
  color:#fff;
  display:flex;
  align-items:center;
  justify-content:center;
  font-weight:900;
  transition:
    transform .35s,
    filter .35s,
    opacity .35s,
    box-shadow .35s;
}

.station:hover{
  transform:translate(-50%,-50%) scale(1.07);
}

.station .num{
  font-size:25px;
}

.station .label{
  position:absolute;
  top:98px;
  white-space:nowrap;
  background:rgba(7,29,41,.88);
  padding:6px 10px;
  border-radius:9px;
  font-size:11px;
  box-shadow:0 6px 14px rgba(0,0,0,.15);
}

.station.available{
  background:linear-gradient(145deg,#2b9b7a,#176d62);
  animation:
    nodePulse 2s infinite,
    floatSoft 3.3s ease-in-out infinite;
}

.station.done{
  background:linear-gradient(145deg,#d1a72c,#8f6810);
  border-color:#ffe58b;
}

.station.locked{
  opacity:.52;
  filter:grayscale(.55);
}

.station.unlocking{
  animation:unlockPop .8s cubic-bezier(.2,.8,.2,1);
}

.s1{left:82%;top:70%}
.s2{left:67%;top:49%}
.s3{left:53%;top:67%}
.s4{left:38%;top:47%}
.s5{left:23%;top:59%}
.s6{left:13%;top:27%}

.token{
  position:absolute;
  z-index:12;
  width:49px;
  height:49px;
  transform:translate(-50%,-50%);
  border-radius:17px;
  background:linear-gradient(145deg,#fff,#d7eaf0);
  border:4px solid #123b4e;
  box-shadow:
    0 10px 20px rgba(0,0,0,.3),
    0 0 0 0 rgba(255,255,255,0);
  display:flex;
  align-items:center;
  justify-content:center;
  color:#0c3142;
  font-weight:1000;
  transition:
    left 1.15s cubic-bezier(.2,.8,.2,1),
    top 1.15s cubic-bezier(.2,.8,.2,1),
    box-shadow .3s;
}

.token.moving{
  animation:tokenMoving .65s ease-in-out infinite alternate;
}

@keyframes tokenMoving{
  from{
    transform:translate(-50%,-50%) translateY(0) rotate(-2deg);
  }
  to{
    transform:translate(-50%,-50%) translateY(-9px) rotate(2deg);
  }
}

/* =========================================================
   QUESTION PANEL
========================================================= */

.questionPanel{
  position:fixed;
  z-index:40;
  inset:auto 50% 18px auto;
  transform:translateX(50%);
  width:min(820px,94vw);
  display:none;
}

.questionPanel.show{
  display:block;
  animation:questionIn .42s cubic-bezier(.2,.8,.2,1);
}

.qCard{
  background:
    linear-gradient(
      145deg,
      rgba(10,35,49,.97),
      rgba(13,50,67,.97)
    );
  border:1px solid rgba(255,255,255,.13);
  border-radius:26px;
  box-shadow:
    0 25px 65px rgba(0,0,0,.38),
    0 0 0 1px rgba(255,255,255,.02);
  padding:22px;
  backdrop-filter:blur(12px);
  position:relative;
  overflow:hidden;
}

.qCard:before{
  content:"";
  position:absolute;
  top:0;
  left:-100%;
  width:70%;
  height:2px;
  background:linear-gradient(
    90deg,
    transparent,
    rgba(255,226,133,.9),
    transparent
  );
  animation:qShine 4s linear infinite;
}

@keyframes qShine{
  0%{left:-100%}
  100%{left:150%}
}

.qHead{
  display:flex;
  align-items:center;
  justify-content:space-between;
  gap:12px;
  margin-bottom:10px;
}

.qTitle{
  color:#ffe495;
  font-weight:900;
}

.qHint{
  font-size:12px;
  color:#a7cbd2;
  animation:rolePop .35s ease;
}

.questionText{
  font-size:20px;
  line-height:1.75;
  margin-bottom:13px;
}

.answers{
  display:grid;
  grid-template-columns:1fr 1fr;
  gap:10px;
}

.answer{
  padding:13px 15px;
  border-radius:14px;
  background:#173f52;
  color:#fff;
  border:1px solid #386173;
  text-align:right;
  transition:
    transform .2s,
    background .2s,
    border-color .2s,
    box-shadow .2s;
  box-shadow:inset 0 1px rgba(255,255,255,.05);
  animation:answerIn .4s both;
}

.answer:nth-child(1){animation-delay:.04s}
.answer:nth-child(2){animation-delay:.10s}
.answer:nth-child(3){animation-delay:.16s}
.answer:nth-child(4){animation-delay:.22s}

.answer:hover{
  transform:translateY(-3px);
  background:#20586e;
  box-shadow:0 8px 18px rgba(0,0,0,.16);
}

.answer:active{
  transform:translateY(2px) scale(.98);
}

.answer.correct{
  background:linear-gradient(145deg,#2e9f79,#1c6e58);
  border-color:#7ee3bb;
  animation:correctPop .5s ease;
  box-shadow:0 0 25px rgba(62,202,154,.25);
}

.answer.wrong{
  background:linear-gradient(145deg,#9a514d,#6e3734);
  border-color:#ffb0a7;
  animation:wrongShake .45s ease;
}

.answer:disabled{
  cursor:default;
}

.feedback{
  text-align:center;
  min-height:26px;
  font-weight:900;
  margin:12px 0 0;
  animation:rolePop .35s ease;
}

.qActions{
  display:flex;
  justify-content:center;
  margin-top:12px;
}

.mini{
  padding:10px 18px;
  border-radius:13px;
  background:#2a5667;
  color:#fff;
}

.successFlash{
  position:fixed;
  inset:0;
  z-index:35;
  pointer-events:none;
  background:
    radial-gradient(
      circle at center,
      rgba(255,231,137,.25),
      transparent 34%
    );
  opacity:0;
}

.successFlash.on{
  animation:flash .8s ease;
}

/* =========================================================
   FINAL
========================================================= */

.final{
  align-items:center;
  justify-content:center;
  text-align:center;
  background:
    radial-gradient(circle at 50% 44%,#24566b,#061a28 75%);
}

.finalInner{
  width:min(700px,92vw);
  padding:40px 28px;
  border-radius:30px;
  background:rgba(10,35,49,.88);
  border:1px solid rgba(255,255,255,.12);
  box-shadow:var(--shadow);
  animation:introCardIn .8s ease;
}

.treasure{
  position:relative;
  margin:0 auto 10px;
  width:190px;
  height:150px;
  perspective:700px;
}

.chest{
  position:absolute;
  left:22px;
  right:22px;
  bottom:5px;
  height:78px;
  background:linear-gradient(#ad7830,#6c431f);
  border:6px solid #4d311e;
  border-radius:10px;
  box-shadow:
    0 18px 30px rgba(0,0,0,.35),
    0 0 35px rgba(242,200,75,.2);
}

.lid{
  position:absolute;
  left:18px;
  right:18px;
  bottom:71px;
  height:45px;
  background:linear-gradient(#d9a74a,#9c682b);
  border:6px solid #4d311e;
  border-bottom:0;
  border-radius:38px 38px 8px 8px;
  transform-origin:bottom;
  transition:transform .8s;
  z-index:3;
}

.treasure.open .lid{
  animation:chestOpen .9s forwards;
}

.treasure:after{
  content:"";
  position:absolute;
  width:150px;
  height:100px;
  left:20px;
  top:0;
  background:radial-gradient(
    ellipse,
    rgba(255,235,124,.8),
    rgba(255,210,65,.25),
    transparent 70%
  );
  filter:blur(8px);
  opacity:0;
  pointer-events:none;
}

.treasure.open:after{
  animation:treasureLight 1.5s ease-in-out infinite;
}

.gem{
  position:absolute;
  width:13px;
  height:13px;
  background:#6ee7ff;
  transform:rotate(45deg);
  box-shadow:0 0 18px #6ee7ff;
  opacity:0;
  z-index:5;
}

.treasure.open .gem{
  animation:gemFloat 1.5s forwards;
}

.g1{
  top:10px;
  left:30px;
}

.g2{
  top:2px;
  right:28px;
  animation-delay:.15s!important;
}

.g3{
  top:-8px;
  left:91px;
  animation-delay:.3s!important;
}

.final h2{
  font-size:52px;
  margin:10px 0;
  animation:titleFloat 3s ease-in-out infinite;
}

.final p{
  color:#cce8ee;
  font-size:18px;
  line-height:1.8;
}

.results{
  display:grid;
  grid-template-columns:repeat(3,1fr);
  gap:10px;
  margin:22px 0;
}

.result{
  padding:14px;
  border-radius:15px;
  background:#123a4d;
  animation:resultIn .5s both;
}

.result:nth-child(1){animation-delay:.1s}
.result:nth-child(2){animation-delay:.2s}
.result:nth-child(3){animation-delay:.3s}

.result b{
  display:block;
  color:#ffe390;
  font-size:25px;
  margin-bottom:4px;
}

/* =========================================================
   TOAST
========================================================= */

.toast{
  position:fixed;
  z-index:60;
  top:76px;
  left:50%;
  transform:translateX(-50%) translateY(-18px) scale(.96);
  padding:11px 17px;
  border-radius:13px;
  background:#163e51;
  border:1px solid rgba(255,255,255,.1);
  box-shadow:0 12px 30px rgba(0,0,0,.24);
  opacity:0;
  pointer-events:none;
  transition:.35s;
}

.toast.show{
  opacity:1;
  transform:translateX(-50%) translateY(0) scale(1);
  animation:rolePop .35s ease;
}

.confetti{
  position:fixed;
  z-index:70;
  width:10px;
  height:16px;
  top:-20px;
  opacity:0;
  pointer-events:none;
  animation:confettiFall 1.8s linear forwards;
}

/* =========================================================
   RESPONSIVE
========================================================= */

@media(max-width:750px){

  .route{
    padding:20px 10px 16px;
  }

  .routeHeader{
    align-items:flex-start;
    flex-direction:column;
  }

  .routeBadge{
    display:none;
  }

  .routeMap{
    min-height:0;
    flex:1;
  }

  .routeStation{
    width:62px;
    height:62px;
  }

  .routeStation small{
    top:67px;
    font-size:9px;
  }

  .routeHint{
    font-size:11px;
    max-width:90vw;
    overflow:hidden;
    text-overflow:ellipsis;
  }

  .setupGrid,
  .answers{
    grid-template-columns:1fr;
  }

  .teamFields{
    grid-template-columns:1fr 1fr;
  }

  .mapViewport{
    inset:64px 8px max(8px,28vh);
  }

  .station{
    width:62px;
    height:62px;
    border-radius:19px;
  }

  .station .num{
    font-size:19px;
  }

  .station .label{
    top:67px;
    font-size:9px;
  }

  .token{
    width:39px;
    height:39px;
  }

  .questionText{
    font-size:17px;
  }

  .answer{
    padding:11px;
  }

  .topHud{
    top:7px;
    left:7px;
    right:7px;
  }

  .hudBox{
    font-size:11px;
    padding:7px 9px;
  }

  .results{
    grid-template-columns:1fr;
  }
}

@media(max-width:460px){

  .introCard{
    padding:34px 20px;
  }

  .sub{
    font-size:18px;
  }

  .credit{
    font-size:14px;
  }

  .tease{
    font-size:16px;
  }

  .palm{
    font-size:62px;
  }

  .questionPanel{
    bottom:6px;
  }

  .qCard{
    padding:16px;
  }

  .qHead{
    align-items:flex-start;
  }

  .hudGroup{
    gap:5px;
  }

  .hudBox{
    padding:6px 8px;
  }

  .station{
    transform:translate(-50%,-50%) scale(.9);
  }
}

@media(max-width:520px){

  .route{
    gap:8px;
    padding:10px 8px;
  }

  .routeHeader{
    gap:4px;
  }

  .routeHeader h2{
    font-size:25px;
  }

  .routeHeader p{
    font-size:12px;
    line-height:1.45;
  }

  .routeMap{
    border-radius:22px;
  }

  .routeActions{
    gap:7px;
  }

  .routeActions button{
    padding:10px 12px;
    font-size:13px;
  }

  .setupPanel{
    padding:18px;
    border-radius:22px;
  }

  .setupPanel h2{
    font-size:26px;
  }

  .setupGrid{
    gap:9px;
  }

  .field{
    padding:11px;
  }

  .switchRow{
    margin-top:9px;
  }

  .setupActions{
    margin-top:12px;
  }

  .topHud{
    gap:5px;
  }

  .hudGroup{
    gap:5px;
  }

  .hudBox{
    font-size:10px;
    padding:6px 7px;
  }

  .hudGroup:first-child .hudBox:first-child{
    max-width:105px;
    overflow:hidden;
    text-overflow:ellipsis;
    white-space:nowrap;
  }

  .questionPanel{
    width:calc(100vw - 10px);
    bottom:5px;
  }

  .qCard{
    padding:13px;
    border-radius:20px;
  }

  .qHead{
    margin-bottom:6px;
  }

  .questionText{
    font-size:15px;
    line-height:1.55;
    margin-bottom:9px;
  }

  .answers{
    gap:6px;
  }

  .answer{
    padding:10px;
    font-size:14px;
  }

  .feedback{
    font-size:13px;
    margin-top:7px;
  }

  .btnPrimary{
    padding:11px 18px;
  }

  .qActions{
    margin-top:8px;
  }
}

@media(max-height:620px){

  .introCard{
    padding:22px 20px;
  }

  .introCard h1{
    font-size:38px;
  }

  .credit{
    margin:10px 0 5px;
    font-size:13px;
  }

  .tease{
    margin:10px auto 16px;
    font-size:14px;
  }

  .setupPanel{
    max-height:96svh;
  }

  .setupGrid{
    grid-template-columns:1fr 1fr;
  }

  .teamFields{
    grid-template-columns:repeat(2,1fr);
  }

  .routeHeader p{
    display:none;
  }

  .routeMap{
    min-height:0;
  }

  .routeHint{
    bottom:8px;
    font-size:10px;
  }
}

@media(prefers-reduced-motion:reduce){

  *,
  *:before,
  *:after{
    animation-duration:.01ms!important;
    animation-iteration-count:1!important;
    scroll-behavior:auto!important;
    transition-duration:.01ms!important;
  }

}

</style>
</head>

<body>

<svg width="0" height="0" style="position:absolute" aria-hidden="true">
<defs>
<radialGradient id="sandGrad" cx="35%" cy="30%" r="75%">
<stop offset="0%" stop-color="#fdf1cf"/>
<stop offset="60%" stop-color="#e6c989"/>
<stop offset="100%" stop-color="#b8935a"/>
</radialGradient>
<radialGradient id="greenGrad" cx="40%" cy="25%" r="80%">
<stop offset="0%" stop-color="#7ac77f"/>
<stop offset="70%" stop-color="#3b916c"/>
<stop offset="100%" stop-color="#256b4d"/>
</radialGradient>
<radialGradient id="hillGrad" cx="35%" cy="30%" r="70%">
<stop offset="0%" stop-color="#5fae6f"/>
<stop offset="100%" stop-color="#2f6b45"/>
</radialGradient>
</defs>
<symbol id="islandArt" viewBox="0 0 400 300">
<path d="M60,150 C40,90 110,40 200,35 C290,30 365,70 370,150 C375,230 300,275 205,270 C110,265 45,225 60,150 Z" fill="url(#sandGrad)"/>
<path d="M60,150 C40,90 110,40 200,35 C290,30 365,70 370,150 C375,230 300,275 205,270 C110,265 45,225 60,150 Z" fill="none" stroke="rgba(255,255,255,.55)" stroke-width="4" stroke-dasharray="1 12" stroke-linecap="round"/>
<path d="M85,150 C70,100 130,65 200,62 C280,58 345,90 345,150 C345,215 285,248 205,245 C130,242 78,205 85,150 Z" fill="url(#greenGrad)"/>
<ellipse cx="230" cy="118" rx="40" ry="27" fill="url(#hillGrad)"/>
<ellipse cx="158" cy="162" rx="32" ry="21" fill="url(#hillGrad)" opacity=".92"/>
<ellipse cx="102" cy="205" rx="13" ry="9" fill="#8b8f92"/>
<ellipse cx="300" cy="198" rx="11" ry="8" fill="#787d80"/>
<ellipse cx="318" cy="112" rx="9" ry="7" fill="#9a9ea1"/>
</symbol>
<symbol id="treasureChestArt" viewBox="0 0 70 64">
<line x1="14" y1="8" x2="14" y2="46" stroke="#6b4a2b" stroke-width="3" stroke-linecap="round"/>
<path d="M14 8 L34 14 L14 20 Z" fill="#e0553f"/>
<ellipse cx="42" cy="54" rx="24" ry="6" fill="rgba(0,0,0,.18)"/>
<rect x="20" y="34" rx="4" ry="4" width="44" height="22" fill="#8a5a2b" stroke="#5c3a1a" stroke-width="2"/>
<path d="M20 34 Q42 14 64 34 Z" fill="#caa23e" stroke="#8a6a1e" stroke-width="2"/>
<rect x="38" y="30" width="8" height="10" rx="2" fill="#f2c94c" stroke="#8a6a1e" stroke-width="1.5"/>
<rect x="20" y="42" width="44" height="4" fill="#5c3a1a" opacity=".5"/>
</symbol>
</svg>

<!-- =====================================================
     INTRO
===================================================== -->

<section id="intro" class="screen intro active">

  <div class="cloud"></div>
  <div class="cloud c2"></div>
  <div class="ocean-sheen"></div>

  <svg class="introTrail" viewBox="0 0 1000 600" preserveAspectRatio="none" aria-hidden="true">
    <path d="M120 560 C 260 480, 340 430, 430 380 S 560 300, 620 250"></path>
  </svg>

  <div class="introIsland"><svg viewBox="0 0 400 300" preserveAspectRatio="none"><use href="#islandArt"></use></svg></div>

  <div class="introBoat">⛵</div>

  <div class="introPeople" style="left:47%">🧑‍🎓</div>
  <div class="introPeople p2" style="left:56%">🧍‍♀️</div>

  <div class="introBird" style="top:10%">🕊️</div>
  <div class="introBird b2" style="top:18%">🕊️</div>

  <div class="introCompass">🧭</div>

  <div class="sparkle" style="top:8%;left:6%">✨</div>
  <div class="sparkle" style="bottom:14%;right:9%;animation-delay:1.1s">✨</div>

  <div class="palm p1">🌴</div>
  <div class="palm p2">🌴</div>

  <div class="introCard">

    <h1>بوصلة الكنز</h1>

    <div class="sub">
      الصف الثامن · معالجة البيانات الجغرافية
    </div>

    <div class="credit">
      إعداد: أ. عهود العبرية<br>
      مدرسة وادي غول للتعليم الأساسي (1-9)
    </div>

    <div class="tease">
      مغامرة جديدة تبدأ هنا… حلّ التحديات، اجمع المفاتيح، وافتح طريقك نحو الكنز.
    </div>

    <button class="btnPrimary" onclick="openSetup()">
      ابدأ المغامرة
    </button>

  </div>

</section>


<!-- =====================================================
     SETUP
===================================================== -->

<section id="setup" class="screen setup">

  <div class="setupPanel">

    <h2>⚓ إعداد الرحلة</h2>

    <div class="setupGrid">

      <div class="field">
        <label>المادة</label>
        <input id="subject" value="الدراسات الاجتماعية">
      </div>

      <div class="field">
        <label>عنوان الدرس</label>
        <input id="lesson" value="معالجة البيانات الجغرافية">
      </div>

      <div class="field">
        <label>الصف</label>
        <input id="grade" value="الثامن">
      </div>

      <div class="field">
        <label>عدد الفرق</label>

        <select id="teamCount" onchange="renderTeams()">
          <option value="1">فردي / فريق واحد</option>
          <option value="2">فريقان</option>
          <option value="3">3 فرق</option>
          <option value="4">4 فرق</option>
        </select>

      </div>

    </div>

    <div class="field" style="margin-top:14px">

      <label>أسماء الفرق</label>

      <div id="teamFields" class="teamFields"></div>

    </div>

    <div class="switchRow">

      <label class="switch">
        <input id="soundToggle" type="checkbox" checked>
        تشغيل المؤثرات الصوتية
      </label>

      <label class="switch">
        <input id="autoAdvance" type="checkbox" checked>
        انتقال تلقائي بعد الإجابة الصحيحة
      </label>

    </div>

    <div class="setupActions">

      <button class="btnSecondary" onclick="showScreen('intro')">
        عودة
      </button>

      <button class="btnPrimary" onclick="launchGame()">
        ابدأ الرحلة
      </button>

    </div>

  </div>

</section>


<!-- =====================================================
     ROUTE
===================================================== -->

<section id="route" class="screen route">

  <div class="routeHeader">

    <div>

      <div class="routeKicker">
        خريطة المغامرة
      </div>

      <h2>
        مخطط رحلة الكنز
      </h2>

      <p>
        اتبع المسار من المحطة الأولى حتى جزيرة الكنز.
        كل محطة تحمل تحديًا جديدًا.
      </p>

    </div>

    <div class="routeBadge">
      6 محطات · كنز واحد
    </div>

  </div>


  <div class="routeMap">

    <div class="routeOcean"></div>

    <div class="routeIsland islandA"><svg viewBox="0 0 400 300" preserveAspectRatio="none"><use href="#islandArt"></use></svg></div>
    <div class="routeIsland islandB"><svg viewBox="0 0 400 300" preserveAspectRatio="none"><use href="#islandArt"></use></svg></div>

    <svg class="treasureMark" viewBox="0 0 70 64" style="left:12%;top:15%"><use href="#treasureChestArt"></use></svg>

    <div class="routeFeature palmR">🌴</div>
    <div class="routeFeature palmL">🌴</div>
    <div class="routeFeature mountainR">⛰️</div>
    <div class="routeFeature caveL">🪨</div>

    <svg
      class="routePath"
      viewBox="0 0 1000 600"
      preserveAspectRatio="none"
      aria-hidden="true"
    >
      <path d="
        M835 425
        C745 310, 650 470, 540 385
        S350 295, 245 385
        S160 295, 120 155
      " />
    </svg>

    <div class="routeStation rs1 active">
      <span>01</span>
      <small>بوابة البداية</small>
    </div>

    <div class="routeStation rs2 locked">
      <span>02</span>
      <small>غابة المعرفة</small>
    </div>

    <div class="routeStation rs3 locked">
      <span>03</span>
      <small>جسر التحدي</small>
    </div>

    <div class="routeStation rs4 locked">
      <span>04</span>
      <small>وادي GIS</small>
    </div>

    <div class="routeStation rs5 locked">
      <span>05</span>
      <small>كهف الرموز</small>
    </div>

    <div class="routeStation treasureStation locked">
      <span>06</span>
      <small>جزيرة الكنز</small>
    </div>

    <div class="routeCompass">
      🧭
    </div>

    <div class="routeHint">
      ابدأ من اليمين… واتبع الآثار حتى الكنز
    </div>

  </div>


  <div class="routeActions">

    <button
      class="btnSecondary"
      onclick="showScreen('setup')"
    >
      تعديل الإعدادات
    </button>

    <button
      class="btnPrimary"
      onclick="beginRoute()"
    >
      ابدأ البحث عن الكنز
    </button>

  </div>

</section>


<!-- =====================================================
     COUNTDOWN
===================================================== -->

<section id="countdown" class="screen countdown">

  <div>

    <div id="countNo" class="countNo">
      3
    </div>

    <div class="countHint">
      استعد للانطلاق…
    </div>

  </div>

</section>


<!-- =====================================================
     GAME
===================================================== -->

<section id="game" class="screen game">

  <div class="topHud">

    <div class="hudGroup">

      <div class="hudBox">
        الدور الآن:
        <b id="hudTeam">—</b>
      </div>

      <div class="hudBox">
        المحطة:
        <b id="hudStation">1 / 6</b>
      </div>

      <div class="hudBox timerBox">
        الوقت:
        <b id="hudTimer">00:60</b>
      </div>

    </div>

    <div class="hudGroup">

      <div class="hudBox">
        ⭐
        <b id="hudScore">0</b>
      </div>

      <div class="hudBox">
        🔑
        <b id="hudKeys">0</b>
      </div>

      <button
        id="soundButton"
        class="hudBox hudBtn"
        onclick="toggleSound()"
      >
        🔊
      </button>

    </div>

  </div>


  <div class="world">

    <div class="mapViewport">

      <div id="mapScene" class="mapScene">

        <div class="waterRipples"></div>

        <div class="islandShadow"></div>

        <div class="islandShape"><svg viewBox="0 0 400 300" preserveAspectRatio="none"><use href="#islandArt"></use></svg></div>

        <svg class="treasureMark" viewBox="0 0 70 64" style="left:13%;top:14%"><use href="#treasureChestArt"></use></svg>

        <div class="river"></div>

        <div class="feature mountains">
          ⛰️
        </div>

        <div class="feature treesA">
          🌴
        </div>

        <div class="feature treesB">
          🌳
        </div>

        <div class="feature treesC">
          🌲
        </div>

        <div class="feature caveF">
          🪨
        </div>

        <div class="feature boatF">
          ⛵
        </div>

        <div class="feature bridgeF">
          🪵
        </div>

        <div class="feature compassF">
          🧭
        </div>

        <div class="routeGlow"></div>


        <button
          class="station available s1"
          data-index="0"
          onclick="openStation(0)"
        >
          <span class="num">01</span>
          <span class="label">بوابة البداية</span>
        </button>


        <button
          class="station locked s2"
          data-index="1"
          onclick="openStation(1)"
        >
          <span class="num">02</span>
          <span class="label">غابة المعرفة</span>
        </button>


        <button
          class="station locked s3"
          data-index="2"
          onclick="openStation(2)"
        >
          <span class="num">03</span>
          <span class="label">جسر التحدي</span>
        </button>


        <button
          class="station locked s4"
          data-index="3"
          onclick="openStation(3)"
        >
          <span class="num">04</span>
          <span class="label">وادي GIS</span>
        </button>


        <button
          class="station locked s5"
          data-index="4"
          onclick="openStation(4)"
        >
          <span class="num">05</span>
          <span class="label">كهف الرموز</span>
        </button>


        <button
          class="station locked s6"
          data-index="5"
          onclick="openStation(5)"
        >
          <span class="num">06</span>
          <span class="label">جزيرة الكنز</span>
        </button>


        <div id="tokens"></div>

      </div>

    </div>

  </div>


  <div id="questionPanel" class="questionPanel">

    <div class="qCard">

      <div class="qHead">

        <div id="qTitle" class="qTitle">
          المحطة
        </div>

        <div id="qHint" class="qHint">
          اختر الإجابة الصحيحة
        </div>

      </div>


      <div
        id="questionText"
        class="questionText"
      ></div>


      <div
        id="answers"
        class="answers"
      ></div>


      <div
        id="feedback"
        class="feedback"
      ></div>


      <div class="qActions">

        <button
          id="continueBtn"
          class="btnPrimary hidden"
          onclick="continueAfterAnswer()"
        >
          متابعة الرحلة
        </button>

      </div>

    </div>

  </div>


  <div id="flash" class="successFlash"></div>

  <div id="toast" class="toast"></div>

</section>


<!-- =====================================================
     FINAL
===================================================== -->

<section id="final" class="screen final">

  <div class="finalInner">

    <div id="treasure" class="treasure">

      <div class="gem g1"></div>
      <div class="gem g2"></div>
      <div class="gem g3"></div>

      <div class="lid"></div>
      <div class="chest"></div>

    </div>


    <h2>
      مبروك!
    </h2>

    <p>
      لقد وصلت إلى كنز المعرفة.<br>
      اكتملت رحلة معالجة البيانات الجغرافية.
    </p>


    <div
      id="results"
      class="results"
    ></div>


    <button
      class="btnPrimary"
      onclick="location.reload()"
    >
      إعادة المغامرة
    </button>


    <div
      style="
        margin-top:17px;
        color:#a8cbd2;
        font-size:13px
      "
    >
      إعداد: أ. عهود العبرية ·
      مدرسة وادي غول للتعليم الأساسي (1-9)
    </div>

  </div>

</section>


<script>

/* =====================================================
   QUESTIONS
===================================================== */

const QUESTIONS = [

  {
    q:"المرحلة الأولى في معالجة البيانات الجغرافية هي:",
    options:[
      "تنظيم البيانات",
      "تصحيح البيانات",
      "تمثيل البيانات",
      "تحليل البيانات"
    ],
    correct:1
  },

  {
    q:"ما الهدف من تصحيح البيانات الجغرافية؟",
    options:[
      "زيادة حجم البيانات",
      "ترتيب الصور والبيانات",
      "إزالة الأخطاء لتطابق الواقع",
      "تحويل البيانات إلى جداول"
    ],
    correct:2
  },

  {
    q:"ما أقسام البيانات في نظم المعلومات الجغرافية (GIS)؟",
    options:[
      "بيانات قديمة وحديثة",
      "بيانات ورقية ورقمية",
      "بيانات طبيعية وبشرية",
      "بيانات مكانية ووصفية"
    ],
    correct:3
  },

  {
    q:"أي مما يأتي يُعد وصفًا يعبر عن بيانات مكانية؟",
    options:[
      "موقع الشجرة",
      "عمر الشجرة",
      "اسم الشجرة",
      "نوع الشجرة"
    ],
    correct:0
  },

  {
    q:"ما النموذج الذي يعتمد على الخلايا أو المربعات في تمثيل الظواهر الجغرافية؟",
    options:[
      "النقطي",
      "الخطي",
      "الشبكي",
      "الوصفي"
    ],
    correct:2
  },

  {
    q:"ما العبارة الصحيحة جغرافيًا لتمثيل ظاهرة الطريق في نموذج البيانات الخطية؟",
    options:[
      "على شكل خلايا شبكية بصفوف وأعمدة متساوية.",
      "على شكل نقطة منفردة ذات إحداثي واحد.",
      "على شكل خطوط متصلة باستخدام شبكة الإحداثيات.",
      "على شكل جدول نصي وصفي بحت."
    ],
    correct:2
  }

];


/* =====================================================
   STATIONS
===================================================== */

const STATIONS = [
  "بوابة البداية",
  "غابة المعرفة",
  "جسر التحدي",
  "وادي GIS",
  "كهف الرموز",
  "جزيرة الكنز"
];


/* =====================================================
   POSITIONS
===================================================== */

const POSITIONS = [
  [82,70],
  [67,49],
  [53,67],
  [38,47],
  [23,59],
  [13,27]
];


/* =====================================================
   COLORS
===================================================== */

const TEAM_COLORS = [
  "#5cc8ff",
  "#ff9278",
  "#b698ff",
  "#65d4a0"
];


/* =====================================================
   VARIABLES
===================================================== */

let teams = [];

let currentTeam = 0;

let currentStation = 0;

let selectedQuestion = null;

let soundOn = true;

let autoAdvance = true;

let lockedTurn = false;

let canContinue = false;

let questionTime = 60;

let timerId = null;

let timerEnd = 0;

let currentQuestionIndex = null;


/* =====================================================
   HELPERS
===================================================== */

function qs(id){
  return document.getElementById(id);
}


function showScreen(id){

  document
    .querySelectorAll(".screen")
    .forEach(x =>
      x.classList.remove("active")
    );

  qs(id).classList.add("active");

}


/* =====================================================
   SETUP
===================================================== */

function openSetup(){

  showScreen("setup");

  renderTeams();

}


function renderTeams(){

  const n =
    Number(qs("teamCount").value);

  const box =
    qs("teamFields");

  box.innerHTML = "";


  for(let i=0;i<n;i++){

    box.insertAdjacentHTML(
      "beforeend",

      `
      <div
        class="teamField"
        style="border-color:${TEAM_COLORS[i]}"
      >
        <input
          id="teamName${i}"
          value="فريق ${i+1}"
          aria-label="اسم الفريق ${i+1}"
        >
      </div>
      `
    );

  }

}


renderTeams();


/* =====================================================
   LAUNCH
===================================================== */

function launchGame(){

  const n =
    Number(qs("teamCount").value);

  teams = [];

  currentTeam = 0;

  currentStation = 0;

  soundOn =
    qs("soundToggle").checked;

  autoAdvance =
    qs("autoAdvance").checked;

  lockedTurn = false;

  currentQuestionIndex = null;

  clearQuestionTimer();


  for(let i=0;i<n;i++){

    teams.push({

      name:
        qs("teamName"+i).value.trim()
        ||
        `فريق ${i+1}`,

      score:0,

      keys:0,

      correct:0,

      wrong:0

    });

  }


  buildTokens();

  showRoutePreview();

}


/* =====================================================
   ROUTE PREVIEW
===================================================== */

function showRoutePreview(){

  updateRouteStations();

  showScreen("route");

}


/* =====================================================
   BEGIN ROUTE
===================================================== */

function beginRoute(){

  showScreen("countdown");

  runCountdown();

}


/* =====================================================
   COUNTDOWN
===================================================== */

function runCountdown(){

  const el =
    qs("countNo");

  const vals = [
    "3",
    "2",
    "1",
    "انطلق!"
  ];

  let i = 0;

  el.textContent =
    vals[i];


  const timer =
    setInterval(() => {

      i++;


      if(i >= vals.length){

        clearInterval(timer);

        setTimeout(() => {

          showScreen("game");

          updateHUD();

          toast(
            `الدور الآن لـ ${teams[0].name}`
          );


          setTimeout(
            () => openStation(0),
            650
          );

        },350);

        return;

      }


      el.textContent =
        vals[i];

      el.style.animation =
        "none";

      void el.offsetWidth;

      el.style.animation =
        "pop .75s ease";


      if(soundOn){

        tone(
          i === 3
          ? "go"
          : "tick"
        );

      }

    },750);

}


/* =====================================================
   TOKENS
===================================================== */

function buildTokens(){

  const wrap =
    qs("tokens");

  wrap.innerHTML = "";


  teams.forEach((t,i) => {

    const d =
      document.createElement("div");

    d.className =
      "token";

    d.id =
      "token"+i;

    d.textContent =
      i+1;

    d.style.background =
      `linear-gradient(
        145deg,
        #fff,
        ${TEAM_COLORS[i]}
      )`;

    wrap.appendChild(d);

    setTokenPosition(i,0);

  });

}


function setTokenPosition(
  teamIndex,
  stationIndex
){

  const el =
    qs("token"+teamIndex);

  if(!el)return;


  el.style.left =
    POSITIONS[stationIndex][0]+"%";

  el.style.top =
    POSITIONS[stationIndex][1]+"%";

}


/* =====================================================
   HUD
===================================================== */

function updateHUD(){

  const t =
    teams[currentTeam];

  if(!t)return;


  qs("hudTeam").textContent =
    t.name;

  qs("hudStation").textContent =
    `${currentStation+1} / ${STATIONS.length}`;

  qs("hudScore").textContent =
    t.score;

  qs("hudKeys").textContent =
    t.keys;

}


/* =====================================================
   OPEN STATION
===================================================== */

function openStation(index){

  if(lockedTurn)return;


  if(index !== currentStation){

    toast(
      index < currentStation
      ? "هذه المحطة مكتملة بالفعل."
      : "هذه المحطة ما زالت مغلقة."
    );

    return;

  }


  lockedTurn = true;

  canContinue = false;

  selectedQuestion =
    QUESTIONS[index];

  currentQuestionIndex =
    index;


  qs("qTitle").textContent =
    "🗺️ " + STATIONS[index];

  qs("qHint").textContent =
    `دور ${teams[currentTeam].name}`;

  qs("questionText").textContent =
    selectedQuestion.q;

  qs("feedback").textContent = "";

  qs("continueBtn")
    .classList
    .add("hidden");


  const box =
    qs("answers");

  box.innerHTML = "";


  const letters = [
    "أ",
    "ب",
    "ج",
    "د"
  ];


  selectedQuestion.options
    .forEach((opt,i) => {

      const b =
        document.createElement("button");

      b.className =
        "answer";

      b.innerHTML =
        `${letters[i]}) ${escapeHtml(opt)}`;

      b.onclick =
        () => submitAnswer(i,b);

      box.appendChild(b);

    });


  qs("questionPanel")
    .classList
    .add("show");


  startQuestionTimer();

}


/* =====================================================
   ANSWER
===================================================== */

function submitAnswer(
  index,
  button
){

  if(
    !lockedTurn ||
    !selectedQuestion
  )return;


  clearQuestionTimer();


  document
    .querySelectorAll(".answer")
    .forEach(
      b => b.disabled = true
    );


  const team =
    teams[currentTeam];


  if(
    index === selectedQuestion.correct
  ){

    button.classList.add("correct");

    team.score += 100;

    team.keys += 1;

    team.correct += 1;


    qs("feedback").textContent =
      "✨ أحسنت! لقد وجدت دليلًا جديدًا للكنز.";

    qs("feedback").style.color =
      "#7ee3bb";


    if(soundOn)
      tone("success");


    flashSuccess();

    confetti(22);

    moveToken();


    qs("continueBtn").textContent =
      "متابعة الرحلة";

    qs("continueBtn")
      .classList
      .remove("hidden");


    canContinue = true;


    if(autoAdvance){

      setTimeout(() => {

        if(canContinue)
          continueAfterAnswer();

      },1400);

    }

  }

  else{

    button.classList.add("wrong");

    team.wrong += 1;


    qs("feedback").textContent =
      teams.length > 1
      ? "🔄 لم تُفتح المحطة بعد… ينتقل نفس التحدي إلى الفريق التالي."
      : "🧭 اقتربت من الحل! حاول مرة أخرى.";


    qs("feedback").style.color =
      "#ffb2a9";


    if(soundOn)
      tone("wrong");


    setTimeout(
      () => passQuestionToNextTeam(),
      1100
    );

  }


  updateHUD();

}


/* =====================================================
   TOKEN MOVEMENT
===================================================== */

function moveToken(){

  const el =
    qs("token"+currentTeam);

  if(!el)return;


  const next =
    Math.min(
      currentStation+1,
      POSITIONS.length-1
    );


  el.classList.add("moving");


  setTimeout(() => {

    setTokenPosition(
      currentTeam,
      next
    );

  },100);


  setTimeout(() => {

    el.classList.remove("moving");

  },1300);


  const current =
    document.querySelector(
      `.station[data-index="${currentStation}"]`
    );


  if(current){

    current.classList.remove(
      "available"
    );

    current.classList.add(
      "done"
    );

  }


  if(currentStation+1 < 6){

    const nextStation =
      document.querySelector(
        `.station[data-index="${currentStation+1}"]`
      );


    if(nextStation){

      nextStation.classList.remove(
        "locked"
      );

      nextStation.classList.add(
        "available",
        "unlocking"
      );


      setTimeout(() => {

        nextStation.classList.remove(
          "unlocking"
        );

      },900);

    }

  }

}


/* =====================================================
   CONTINUE
===================================================== */

function continueAfterAnswer(){

  if(!canContinue)return;


  canContinue = false;

  clearQuestionTimer();


  qs("continueBtn")
    .classList
    .add("hidden");


  qs("questionPanel")
    .classList
    .remove("show");


  if(currentStation >= 5){

    endGame();

    return;

  }


  currentStation += 1;


  currentTeam =
    (currentTeam + 1)
    % teams.length;


  lockedTurn = false;

  selectedQuestion = null;

  currentQuestionIndex = null;


  updateRouteStations();

  updateHUD();


  toast(
    `تم فتح: ${STATIONS[currentStation]} — الدور الآن لـ ${teams[currentTeam].name}`
  );


  setTimeout(
    () => openStation(currentStation),
    650
  );

}


/* =====================================================
   PASS QUESTION TO NEXT TEAM
===================================================== */

function passQuestionToNextTeam(){

  if(
    !lockedTurn ||
    !selectedQuestion
  )return;


  clearQuestionTimer();


  qs("questionPanel")
    .classList
    .remove("show");


  lockedTurn = false;

  canContinue = false;


  if(teams.length === 1){

    toast(
      "سيبقى التحدي مع الفريق نفسه. حاول من جديد."
    );


    setTimeout(
      () => openStation(currentStation),
      650
    );

    return;

  }


  currentTeam =
    (currentTeam + 1)
    % teams.length;


  updateHUD();


  toast(
    `نفس التحدي الآن لـ ${teams[currentTeam].name}`
  );


  setTimeout(
    () => openStation(currentStation),
    650
  );

}


/* =====================================================
   TIMER
===================================================== */

function startQuestionTimer(){

  clearQuestionTimer();


  timerEnd =
    Date.now()
    + questionTime * 1000;


  updateTimerUI();


  timerId =
    setInterval(() => {

      const left =
        Math.max(
          0,
          Math.ceil(
            (timerEnd - Date.now()) / 1000
          )
        );


      updateTimerUI(left);


      if(left <= 0){

        clearQuestionTimer();

        handleTimeUp();

      }

    },250);

}


function updateTimerUI(value){

  const left =
    typeof value === "number"
    ? value
    : Math.max(
        0,
        Math.ceil(
          (timerEnd - Date.now()) / 1000
        )
      );


  qs("hudTimer").textContent =
    `00:${String(left).padStart(2,"0")}`;


  qs("hudTimer")
    .parentElement
    .classList
    .toggle(
      "warning",
      left <= 10
    );

}


function clearQuestionTimer(){

  if(timerId){

    clearInterval(timerId);

    timerId = null;

  }


  const timer =
    qs("hudTimer");

  if(timer){

    timer.parentElement
      .classList
      .remove("warning");

  }

}


/* =====================================================
   TIME UP
===================================================== */

function handleTimeUp(){

  if(
    !lockedTurn ||
    !selectedQuestion
  )return;


  document
    .querySelectorAll(".answer")
    .forEach(
      b => b.disabled = true
    );


  teams[currentTeam].wrong += 1;


  qs("feedback").textContent =
    teams.length > 1
    ? "⏰ انتهى الوقت. ينتقل نفس التحدي إلى الفريق التالي."
    : "⏰ انتهى الوقت. حاول التحدي مرة أخرى.";


  qs("feedback").style.color =
    "#ffb2a9";


  if(soundOn)
    tone("wrong");


  setTimeout(
    () => passQuestionToNextTeam(),
    1000
  );

}


/* =====================================================
   ROUTE STATIONS UPDATE
===================================================== */

function updateRouteStations(){

  document
    .querySelectorAll(".routeStation")
    .forEach((el,i) => {

      el.classList.remove(
        "active",
        "locked",
        "done"
      );


      if(i < currentStation){

        el.classList.add("done");

      }

      else if(i === currentStation){

        el.classList.add("active");

      }

      else{

        el.classList.add("locked");

      }

    });

}


/* =====================================================
   END GAME
===================================================== */

function endGame(){

  clearQuestionTimer();


  qs("treasure")
    .classList
    .add("open");


  const totalScore =
    teams.reduce(
      (a,t) => a + t.score,
      0
    );


  const totalKeys =
    teams.reduce(
      (a,t) => a + t.keys,
      0
    );


  const totalCorrect =
    teams.reduce(
      (a,t) => a + t.correct,
      0
    );


  qs("results").innerHTML = `

    <div class="result">
      <b>${totalScore}</b>
      إجمالي النقاط
    </div>

    <div class="result">
      <b>${totalCorrect}</b>
      إجابة صحيحة
    </div>

    <div class="result">
      <b>${totalKeys}</b>
      مفاتيح الكنز
    </div>

  `;


  showScreen("final");


  if(soundOn)
    tone("treasure");


  confetti(65);

}


/* =====================================================
   SOUND
===================================================== */

function toggleSound(){

  soundOn = !soundOn;


  qs("soundButton").textContent =
    soundOn
    ? "🔊"
    : "🔇";


  if(soundOn)
    tone("tick");

}


/* =====================================================
   TOAST
===================================================== */

function toast(msg){

  const t =
    qs("toast");

  t.textContent =
    msg;

  t.classList.add(
    "show"
  );


  clearTimeout(
    window.__toast
  );


  window.__toast =
    setTimeout(
      () =>
        t.classList.remove("show"),
      1900
    );

}


/* =====================================================
   SUCCESS FLASH
===================================================== */

function flashSuccess(){

  const f =
    qs("flash");

  f.classList.remove(
    "on"
  );

  void f.offsetWidth;

  f.classList.add(
    "on"
  );

}


/* =====================================================
   CONFETTI
===================================================== */

function confetti(count=28){

  for(
    let i=0;
    i<count;
    i++
  ){

    const e =
      document.createElement("div");

    e.className =
      "confetti";


    e.style.left =
      Math.random()*100+"vw";


    e.style.background =
      TEAM_COLORS[
        i % TEAM_COLORS.length
      ];


    e.style.animationDelay =
      Math.random()*.5+"s";


    document.body.appendChild(e);


    setTimeout(
      () => e.remove(),
      2400
    );

  }

}


/* =====================================================
   ESCAPE HTML
===================================================== */

function escapeHtml(s){

  return String(s).replace(
    /[&<>"]/g,

    c => ({
      "&":"&amp;",
      "<":"&lt;",
      ">":"&gt;",
      '"':"&quot;"
    }[c])

  );

}


/* =====================================================
   AUDIO
===================================================== */

let audioCtx = null;


function tone(kind){

  try{

    if(!soundOn)return;


    audioCtx =
      audioCtx ||

      new (
        window.AudioContext ||
        window.webkitAudioContext
      )();


    const now =
      audioCtx.currentTime;


    let seq =

      kind === "success"

      ? [523.25,659.25,783.99]

      : kind === "wrong"

      ? [220,185]

      : kind === "treasure"

      ? [523.25,659.25,783.99,1046.5]

      : kind === "go"

      ? [392,523.25,659.25]

      : [330];


    seq.forEach(
      (freq,i) => {

        const o =
          audioCtx.createOscillator();

        const g =
          audioCtx.createGain();


        o.type =
          "sine";

        o.frequency.value =
          freq;


        g.gain.setValueAtTime(
          0.0001,
          now + i*.10
        );


        g.gain.exponentialRampToValueAtTime(
          kind === "wrong"
          ? .035
          : .055,

          now + i*.10 + .01
        );


        g.gain.exponentialRampToValueAtTime(
          .0001,

          now + i*.10 + .16
        );


        o.connect(g);

        g.connect(
          audioCtx.destination
        );


        o.start(
          now + i*.10
        );


        o.stop(
          now + i*.10 + .18
        );

      }
    );

  }

  catch(e){}

}


/* =====================================================
   BASIC COPY / SOURCE DETERRENTS
===================================================== */

(() => {

  const blockedKeys =
    new Set([
      "c",
      "x",
      "s",
      "u",
      "a"
    ]);


  document.addEventListener(
    "contextmenu",
    e => e.preventDefault(),
    {capture:true}
  );


  document.addEventListener(
    "copy",
    e => e.preventDefault(),
    {capture:true}
  );


  document.addEventListener(
    "cut",
    e => e.preventDefault(),
    {capture:true}
  );


  document.addEventListener(
    "dragstart",
    e => e.preventDefault(),
    {capture:true}
  );


  document.addEventListener(
    "selectstart",
    e => e.preventDefault(),
    {capture:true}
  );


  document.addEventListener(
    "keydown",

    e => {

      const k =
        (e.key || "").toLowerCase();


      if(

        k === "f12"

        ||

        (
          e.ctrlKey &&
          blockedKeys.has(k)
        )

        ||

        (
          e.metaKey &&
          blockedKeys.has(k)
        )

        ||

        (
          e.ctrlKey &&
          e.shiftKey &&
          ["i","j","c"].includes(k)
        )

        ||

        (
          e.metaKey &&
          e.altKey &&
          k === "i"
        )

      ){

        e.preventDefault();

        e.stopPropagation();

      }

    },

    {capture:true}

  );


  window.addEventListener(
    "beforeprint",
    () => {
      document.body.style.display =
        "none";
    }
  );


  window.addEventListener(
    "afterprint",
    () => {
      document.body.style.display =
        "";
    }
  );

})();

</script>

</body>
</html>
