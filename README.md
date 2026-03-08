<!DOCTYPE html>
<html lang="it">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>VIVET° — We Design Culture</title>
<link href="https://fonts.googleapis.com/css2?family=Barlow+Condensed:ital,wght@0,400;0,600;0,700;0,800;0,900;1,800;1,900&family=Share+Tech+Mono&family=Barlow:wght@300;400;500;600;700&display=swap" rel="stylesheet">
<style>
:root{
  --black:#0a0a0a;--dark:#111;--card:#161616;--card2:#1a1a1a;
  --lime:#c8ff00;--orange:#e84c1e;--white:#f0ece3;
  --border:rgba(255,255,255,.07);
  --mono:'Share Tech Mono',monospace;
  --cond:'Barlow Condensed',sans-serif;
  --body:'Barlow',sans-serif;
}
*,*::before,*::after{box-sizing:border-box;margin:0;padding:0;}
html{scroll-behavior:smooth;}
body{background:var(--black);color:var(--white);font-family:var(--body);overflow-x:hidden;cursor:none;}

/* CURSOR */
#cur{width:10px;height:10px;background:var(--lime);border-radius:50%;position:fixed;top:0;left:0;pointer-events:none;z-index:9999;mix-blend-mode:difference;}
#cur-ring{width:32px;height:32px;border:1px solid rgba(200,255,0,.4);border-radius:50%;position:fixed;top:0;left:0;pointer-events:none;z-index:9998;transition:width .25s,height .25s;}

/* NAV */
nav{position:fixed;top:0;left:0;right:0;z-index:500;display:flex;justify-content:space-between;align-items:center;padding:0 2.5rem;height:60px;background:rgba(10,10,10,.96);backdrop-filter:blur(20px);border-bottom:1px solid var(--border);}
.nav-logo{font-family:var(--cond);font-size:2rem;font-weight:900;color:var(--lime);text-decoration:none;letter-spacing:.08em;display:flex;align-items:center;gap:0;text-transform:uppercase;line-height:1;}
.nav-logo-icon{display:none;}
.nav-logo sup{font-size:.7rem;color:var(--orange);vertical-align:super;font-weight:900;margin-left:.05em;}
nav ul{display:flex;gap:2rem;list-style:none;}
nav a{font-family:var(--mono);font-size:.62rem;letter-spacing:.18em;color:rgba(240,236,227,.45);text-decoration:none;text-transform:uppercase;transition:color .2s;}
nav a:hover{color:var(--lime);}
.nav-btn{background:var(--lime)!important;color:var(--black)!important;font-family:var(--mono)!important;font-size:.65rem!important;letter-spacing:.15em!important;font-weight:700!important;padding:.55rem 1.4rem!important;text-decoration:none;text-transform:uppercase;transition:background .2s!important;}
.nav-btn:hover{background:var(--orange)!important;color:var(--white)!important;}
.nav-btn::after{content:' →';}

/* HERO */
#hero{min-height:100vh;padding:0 2.5rem 5rem;display:flex;flex-direction:column;justify-content:flex-end;position:relative;overflow:hidden;background:var(--black);}
.hero-bg-text{position:absolute;font-family:var(--cond);font-size:clamp(14rem,30vw,28rem);font-weight:900;font-style:italic;color:rgba(200,255,0,.022);top:50%;left:-2%;transform:translateY(-50%);line-height:1;pointer-events:none;white-space:nowrap;letter-spacing:-.04em;}
.hero-eyebrow{font-family:var(--mono);font-size:.65rem;letter-spacing:.22em;color:rgba(240,236,227,.5);text-transform:uppercase;display:flex;align-items:center;gap:.8rem;margin-bottom:1.2rem;animation:fup .7s .2s both;}
.hero-eyebrow::before{content:'——';color:var(--orange);margin-right:.2rem;}
.hero-h1{font-family:var(--cond);font-weight:900;text-transform:uppercase;line-height:.88;letter-spacing:-.01em;animation:fup .8s .3s both;margin-bottom:3rem;}
.hero-h1 .line1{font-size:clamp(6rem,18vw,17rem);color:var(--white);display:block;}
.hero-h1 .line2{font-size:clamp(6rem,18vw,17rem);color:var(--lime);display:block;}
.hero-h1 .line3{font-size:clamp(6rem,18vw,17rem);display:block;-webkit-text-stroke:2px var(--orange);color:transparent;font-style:italic;}

/* HERO FLOATING STATS */
.hero-float-row{display:flex;gap:1px;animation:fup .9s .5s both;margin-bottom:2rem;}
.hfloat{background:rgba(22,22,22,.92);backdrop-filter:blur(12px);border:1px solid var(--border);padding:1.4rem 2.5rem;text-align:center;flex:1;}
.hfloat-num{font-family:var(--cond);font-size:2rem;font-weight:900;color:var(--lime);line-height:1;}
.hfloat-label{font-family:var(--mono);font-size:.52rem;letter-spacing:.18em;color:rgba(240,236,227,.35);text-transform:uppercase;margin-top:.3rem;}

/* HERO CTA BUTTONS */
.hero-cta-row{display:flex;gap:1px;animation:fup .9s .65s both;}
.hero-btn-main{background:var(--lime);color:var(--black);font-family:var(--mono);font-size:.72rem;letter-spacing:.15em;font-weight:700;padding:1.1rem 2.2rem;text-decoration:none;text-transform:uppercase;transition:background .2s;}
.hero-btn-main:hover{background:var(--orange);color:var(--white);}
.hero-btn-sec{background:transparent;color:var(--white);font-family:var(--mono);font-size:.72rem;letter-spacing:.15em;font-weight:700;padding:1.1rem 2.2rem;text-decoration:none;text-transform:uppercase;border:1px solid rgba(200,255,0,.3);transition:border-color .2s,color .2s;}
.hero-btn-sec:hover{border-color:var(--lime);color:var(--lime);}

/* TICKER */
.ticker-outer{overflow:hidden;background:var(--lime);padding:.55rem 0;}
.ticker-inner{display:flex;animation:ticker 22s linear infinite;white-space:nowrap;}
.t-item{font-family:var(--mono);font-size:.7rem;letter-spacing:.15em;color:var(--black);padding:0 1.8rem;text-transform:uppercase;}
.t-dot{color:rgba(0,0,0,.3);}

/* SECTION BASE */
section{padding:6rem 2.5rem;}
.s-label{font-family:var(--mono);font-size:.6rem;letter-spacing:.25em;color:var(--orange);text-transform:uppercase;display:flex;align-items:center;gap:.6rem;margin-bottom:.8rem;}
.s-title{font-family:var(--cond);font-weight:900;text-transform:uppercase;font-size:clamp(2.5rem,6vw,5rem);line-height:.9;letter-spacing:-.01em;margin-bottom:1.5rem;}
.acc{color:var(--lime);}
.acc-o{color:var(--orange);}

/* MANIFESTO */
#manifesto{background:var(--white);}
.manifesto-grid{display:grid;grid-template-columns:1fr 1fr;gap:6rem;align-items:start;max-width:1280px;margin:0 auto;}
.manifesto-left .s-label,.manifesto-left .s-title{color:var(--black);}
.manifesto-left .s-title .acc-o{color:var(--orange);}
.manifesto-quote{font-family:var(--cond);font-size:clamp(1.4rem,2.5vw,2rem);font-weight:800;font-style:italic;line-height:1.2;color:var(--black);border-left:3px solid var(--orange);padding-left:1.5rem;margin-bottom:2rem;text-transform:uppercase;}
.manifesto-text{font-size:.9rem;color:rgba(0,0,0,.6);line-height:1.85;margin-bottom:1rem;}
.manifesto-text strong{color:var(--black);font-weight:700;}
.manifesto-right{display:flex;flex-direction:column;gap:1px;}
.pillar{display:flex;gap:1.5rem;align-items:flex-start;padding:2rem 1.8rem;background:var(--black);border-left:2px solid transparent;transition:border-color .3s,background .3s;}
.pillar:hover{border-color:var(--lime);background:#111;}
.pillar-icon{font-size:1.4rem;flex-shrink:0;}
.pillar-title{font-family:var(--cond);font-size:1.1rem;font-weight:800;text-transform:uppercase;color:var(--white);margin-bottom:.4rem;}
.pillar-desc{font-size:.78rem;color:rgba(240,236,227,.42);line-height:1.7;}

/* COLLEZIONI */
#collezioni{background:var(--black);padding-bottom:0;}
.coll-header{max-width:1280px;margin:0 auto 3rem;}
.coll-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:1px;max-width:1280px;margin:0 auto;background:var(--border);}
.coll-card{background:var(--card);padding:2.5rem 2rem;display:flex;flex-direction:column;justify-content:space-between;position:relative;overflow:hidden;cursor:pointer;min-height:220px;transition:background .3s;}
.coll-card:hover{background:var(--card2);}
.coll-card::after{content:'';position:absolute;bottom:0;left:0;right:0;height:2px;background:var(--lime);transform:scaleX(0);transform-origin:left;transition:transform .4s cubic-bezier(.2,.8,.2,1);}
.coll-card:hover::after{transform:scaleX(1);}
.coll-card.featured{grid-column:span 2;}
.coll-badge{position:absolute;top:1rem;right:1rem;font-family:var(--mono);font-size:.5rem;letter-spacing:.15em;padding:.25rem .6rem;text-transform:uppercase;background:var(--orange);color:var(--white);}
.coll-tag{font-family:var(--mono);font-size:.55rem;letter-spacing:.2em;color:var(--orange);text-transform:uppercase;margin-bottom:.3rem;}
.coll-name{font-family:var(--cond);font-size:2.2rem;font-weight:900;text-transform:uppercase;color:var(--white);line-height:1;margin-bottom:.4rem;}
.coll-card.featured .coll-name{font-size:3.5rem;}
.coll-desc{font-size:.78rem;color:rgba(240,236,227,.4);line-height:1.6;}
.coll-price{font-family:var(--mono);font-size:.65rem;letter-spacing:.1em;color:var(--lime);margin-top:1.2rem;}

/* BESTSELLER — come screenshot con foto */
#bestseller{background:var(--dark);padding-top:5rem;padding-bottom:0;}
#bestseller .s-label{color:var(--orange);}
.bs-section-head{padding-bottom:2.5rem;}
.bs-grid{display:grid;grid-template-columns:repeat(4,1fr);gap:1px;max-width:100%;background:var(--border);}
.bs-card{background:var(--card);display:flex;flex-direction:column;cursor:pointer;transition:background .3s;}
.bs-card:hover{background:var(--card2);}
.bs-img{aspect-ratio:3/4;overflow:hidden;position:relative;background:var(--black);}
.bs-img img{width:100%;height:100%;object-fit:cover;display:block;transition:transform .6s cubic-bezier(.2,.8,.2,1);}
.bs-card:hover .bs-img img{transform:scale(1.04);}
.bs-img-placeholder{width:100%;height:100%;display:flex;align-items:center;justify-content:center;font-size:6rem;background:linear-gradient(135deg,#1a1a1a,#0f0f0f);}
.bs-badge{position:absolute;top:.8rem;left:.8rem;font-family:var(--mono);font-size:.52rem;letter-spacing:.12em;padding:.25rem .6rem;text-transform:uppercase;z-index:1;}
.bs-badge.best{background:var(--white);color:var(--black);}
.bs-badge.new{background:var(--lime);color:var(--black);}
.bs-badge.top{background:var(--lime);color:var(--black);}
.bs-badge.lim{background:var(--orange);color:var(--white);}
.bs-colors{display:flex;gap:.4rem;padding:.8rem 1rem .5rem;}
.bs-dot{width:14px;height:14px;border-radius:50%;border:1.5px solid rgba(255,255,255,.15);cursor:pointer;}
.bs-dot.active{border-color:var(--lime);}
.bs-body{padding:.5rem 1rem 1.5rem;flex:1;}
.bs-line{font-family:var(--mono);font-size:.52rem;letter-spacing:.18em;color:rgba(240,236,227,.35);text-transform:uppercase;margin-bottom:.3rem;}
.bs-name{font-family:var(--cond);font-size:1.2rem;font-weight:900;text-transform:uppercase;color:var(--white);line-height:1.1;margin-bottom:.4rem;}
.bs-desc{font-size:.72rem;color:rgba(240,236,227,.38);line-height:1.6;}
.bs-hover-link{font-family:var(--mono);font-size:.6rem;letter-spacing:.1em;color:var(--orange);margin-top:.5rem;display:none;}
.bs-card:hover .bs-hover-link{display:block;}
.bs-price-row{display:flex;justify-content:space-between;align-items:center;padding:.8rem 1rem;border-top:1px solid var(--border);}
.bs-price{font-family:var(--cond);font-size:1.4rem;font-weight:900;color:var(--lime);}
.bs-add{width:28px;height:28px;background:var(--lime);color:var(--black);font-size:1.1rem;display:flex;align-items:center;justify-content:center;cursor:pointer;font-weight:700;transition:background .2s;}
.bs-add:hover{background:var(--orange);color:var(--white);}

/* CUSTOM PROGRAM — come screenshot */
#custom{background:var(--black);padding:8rem 2.5rem;}
.custom-layout{display:grid;grid-template-columns:1fr 1fr;gap:6rem;max-width:1280px;margin:0 auto;}
.custom-left{padding-right:2rem;}
.custom-left .s-title{font-size:clamp(3rem,7vw,6rem);}
.custom-left p{font-size:.9rem;color:rgba(240,236,227,.5);line-height:1.9;margin-bottom:1.4rem;}
.custom-left p strong{color:var(--white);}
.custom-left .solo-tuo{font-style:italic;font-weight:700;color:var(--white);}
.custom-bullets{margin:2.2rem 0;background:rgba(200,255,0,.04);border:1px solid rgba(200,255,0,.12);padding:2rem 2rem;}
.custom-bullet{font-family:var(--mono);font-size:.65rem;letter-spacing:.08em;color:rgba(240,236,227,.55);padding:.55rem 0;border-bottom:1px solid rgba(255,255,255,.04);display:flex;align-items:center;gap:.8rem;}
.custom-bullet:last-child{border-bottom:none;}
.custom-bullet::before{content:'✦';color:var(--lime);flex-shrink:0;font-size:.6rem;}
.custom-right{display:flex;flex-direction:column;gap:2px;}
.custom-step{background:var(--card);padding:2.5rem 2.2rem;display:flex;gap:1.8rem;align-items:flex-start;border-left:3px solid transparent;transition:border-color .25s,background .25s;}
.custom-step:hover{border-color:var(--lime);background:var(--card2);}
.step-num-box{min-width:40px;height:40px;background:var(--orange);color:var(--white);font-family:var(--cond);font-size:1.5rem;font-weight:900;display:flex;align-items:center;justify-content:center;flex-shrink:0;}
.step-sub-tag{font-family:var(--mono);font-size:.52rem;letter-spacing:.12em;color:var(--black);background:var(--lime);padding:.25rem .7rem;display:inline-block;margin-bottom:.7rem;text-transform:uppercase;}
.step-title{font-family:var(--cond);font-size:1.3rem;font-weight:900;text-transform:uppercase;color:var(--white);margin-bottom:.5rem;}
.step-desc{font-size:.8rem;color:rgba(240,236,227,.4);line-height:1.75;}
/* Regole */
.custom-rules{max-width:1280px;margin:4rem auto 0;}
.rules-head{display:flex;align-items:center;gap:1rem;margin-bottom:1.5rem;}
.rules-head-icon{font-size:1rem;}
.rules-head-title{font-family:var(--mono);font-size:.65rem;letter-spacing:.22em;color:var(--lime);text-transform:uppercase;}
.rules-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:1px;background:var(--border);}
.rule-card{background:var(--card);padding:2rem 1.8rem;transition:background .3s;}
.rule-card:hover{background:var(--card2);}
.rule-icon{font-size:1.2rem;margin-bottom:.8rem;}
.rule-title{font-family:var(--mono);font-size:.6rem;letter-spacing:.18em;text-transform:uppercase;color:var(--white);margin-bottom:.5rem;}
.rule-text{font-size:.75rem;color:rgba(240,236,227,.38);line-height:1.65;}

/* COMPETITION — come screenshot */
#competition{background:var(--dark);}
.comp-top{max-width:1280px;margin:0 auto;display:grid;grid-template-columns:1fr auto;gap:3rem;align-items:start;margin-bottom:2rem;}
.comp-top-left p{font-size:.88rem;color:rgba(240,236,227,.5);line-height:1.75;max-width:680px;margin-bottom:.8rem;}
.comp-top-left p strong{color:var(--white);}
/* 4 prize cards */
.comp-prizes{display:grid;grid-template-columns:repeat(4,1fr);gap:1px;max-width:1280px;margin:0 auto 2rem;background:var(--border);}
.prize-card{background:var(--card);padding:2.5rem 1.5rem;text-align:center;position:relative;overflow:hidden;transition:background .3s;}
.prize-card:first-child{background:#1e0f0a;}
.prize-card:hover{background:var(--card2);}
.prize-card:first-child:hover{background:#2a1510;}
.prize-icon{font-size:2rem;margin-bottom:1rem;display:block;}
.prize-name{font-family:var(--cond);font-size:1.8rem;font-weight:900;text-transform:uppercase;color:var(--white);line-height:1;margin-bottom:.3rem;}
.prize-sub{font-family:var(--mono);font-size:.5rem;letter-spacing:.2em;color:var(--orange);text-transform:uppercase;margin-bottom:.8rem;}
.prize-desc{font-size:.72rem;color:rgba(240,236,227,.38);line-height:1.6;}
.prize-card:first-child .prize-name{color:var(--orange);}
/* steps + timer */
.comp-bottom{max-width:1280px;margin:0 auto;display:grid;grid-template-columns:1fr auto;gap:3rem;}
.comp-steps-row{display:grid;grid-template-columns:repeat(4,1fr);gap:1px;background:var(--border);flex:1;}
.comp-step-card{background:var(--card);padding:2rem 1.5rem;transition:background .3s;}
.comp-step-card:hover{background:var(--card2);}
.comp-step-icon{font-size:1rem;margin-bottom:.8rem;}
.comp-step-title{font-family:var(--cond);font-size:.95rem;font-weight:900;text-transform:uppercase;color:var(--white);margin-bottom:.3rem;}
.comp-step-desc{font-size:.72rem;color:rgba(240,236,227,.35);line-height:1.65;}
/* timer box */
.comp-timer{background:var(--orange);padding:2rem 2.5rem;text-align:center;min-width:180px;align-self:start;}
.timer-label{font-family:var(--mono);font-size:.52rem;letter-spacing:.2em;color:rgba(240,236,227,.7);text-transform:uppercase;margin-bottom:.5rem;}
.timer-num{font-family:var(--cond);font-size:5rem;font-weight:900;color:var(--white);line-height:1;}
.timer-sub{font-family:var(--mono);font-size:.5rem;letter-spacing:.1em;color:rgba(240,236,227,.55);margin-top:.3rem;text-transform:uppercase;}
/* past winners */
.past-winners-row{display:flex;align-items:stretch;gap:1px;max-width:1280px;margin:2rem auto 0;background:var(--border);}
.pw-label{background:var(--card);padding:.8rem 1.5rem;display:flex;align-items:center;gap:.8rem;min-width:160px;}
.pw-label-icon{font-size:1rem;}
.pw-label-txt{font-family:var(--mono);font-size:.58rem;letter-spacing:.18em;color:rgba(240,236,227,.4);text-transform:uppercase;}
.pw-item{background:var(--card);padding:.8rem 1.5rem;flex:1;display:flex;gap:.8rem;align-items:center;transition:background .3s;}
.pw-item:hover{background:var(--card2);}
.pw-medal{font-size:1rem;}
.pw-month{font-family:var(--mono);font-size:.5rem;letter-spacing:.15em;color:var(--orange);text-transform:uppercase;}
.pw-name{font-size:.78rem;color:var(--white);font-weight:600;}
.pw-design{font-family:var(--mono);font-size:.55rem;color:rgba(240,236,227,.3);}
/* comp CTA buttons */
.comp-cta-row{display:flex;gap:1px;max-width:1280px;margin:1.5rem auto 0;}
.comp-btn-lime{background:var(--orange);color:var(--white);font-family:var(--mono);font-size:.65rem;letter-spacing:.15em;padding:1rem 2rem;text-decoration:none;text-transform:uppercase;transition:background .2s;display:inline-flex;align-items:center;gap:.6rem;}
.comp-btn-lime:hover{background:var(--lime);color:var(--black);}
.comp-btn-out{border:1px solid rgba(240,236,227,.2);color:var(--white);font-family:var(--mono);font-size:.65rem;letter-spacing:.15em;padding:1rem 2rem;text-decoration:none;text-transform:uppercase;transition:border-color .2s,color .2s;display:inline-block;}
.comp-btn-out:hover{border-color:var(--lime);color:var(--lime);}

/* PROCESSO — layout orizzontale cream come screenshot */
#processo{background:var(--white);padding:5rem 2.5rem;}
#processo .s-label{color:var(--orange);}
#processo .s-title{color:var(--black);}
#processo .s-title .acc-o{color:var(--orange);}
.proc-steps{display:flex;gap:1px;max-width:1280px;margin:3rem auto 0;background:rgba(0,0,0,.12);}
.proc-step{flex:1;background:#f5f0e8;padding:2.5rem 1.8rem;position:relative;overflow:hidden;transition:background .3s;}
.proc-step:hover{background:#ede8df;}
.proc-n{font-family:var(--cond);font-size:4.5rem;font-weight:900;color:rgba(0,0,0,.06);position:absolute;top:.5rem;right:1rem;line-height:1;pointer-events:none;}
.proc-icon{font-size:1.4rem;margin-bottom:1.2rem;display:block;}
.proc-title{font-family:var(--cond);font-size:1.1rem;font-weight:900;text-transform:uppercase;color:var(--black);margin-bottom:.4rem;letter-spacing:.04em;}
.proc-desc{font-size:.75rem;color:rgba(0,0,0,.45);line-height:1.65;}

/* SOSTENIBILITÀ — layout orizzontale come screenshot */
#sostenibilita{background:var(--black);padding:5rem 2.5rem;}
.sost-layout{display:grid;grid-template-columns:1fr 1fr;gap:5rem;align-items:center;max-width:1280px;margin:0 auto;}
.sost-metrics{display:grid;grid-template-columns:1fr 1fr;gap:1px;background:var(--border);}
.metric-card{background:var(--card);padding:2.5rem 2rem;transition:background .3s;}
.metric-card:hover{background:var(--card2);}
.metric-num{font-family:var(--cond);font-size:3rem;font-weight:900;color:var(--lime);line-height:1;margin-bottom:.4rem;}
.metric-label{font-family:var(--mono);font-size:.55rem;letter-spacing:.16em;color:rgba(240,236,227,.35);text-transform:uppercase;line-height:1.5;}
.sost-text p{font-size:.9rem;color:rgba(240,236,227,.5);line-height:1.85;margin-bottom:1rem;}
.sost-text p strong{color:var(--white);}
.sost-big{font-family:var(--cond);font-size:clamp(2.5rem,5vw,4.5rem);font-weight:900;text-transform:uppercase;color:var(--white);line-height:.9;margin-bottom:1.5rem;}
.sost-big .acc{color:var(--lime);}

/* PREZZI — come screenshot con card lime */
#prezzi{background:var(--dark);padding:5rem 0 0;}
.prezzi-head{padding:0 2.5rem 3rem;}
.price-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:0;max-width:100%;background:var(--border);}
.price-card{background:var(--card);padding:3.5rem 3rem 3rem;position:relative;border-top:3px solid transparent;transition:background .3s;}
.price-card:hover{background:var(--card2);}
.price-card.hot{background:var(--lime);border-top-color:transparent;}
.price-card.hot:hover{background:#d4ff00;}
.price-card.hot::before{content:'🔥 PIÙ VENDUTO';position:absolute;top:-.7rem;left:50%;transform:translateX(-50%);font-family:var(--mono);font-size:.52rem;letter-spacing:.15em;background:var(--orange);color:var(--white);padding:.3rem 1rem;white-space:nowrap;text-transform:uppercase;}
.price-tier{font-family:var(--mono);font-size:.58rem;letter-spacing:.22em;color:var(--orange);text-transform:uppercase;margin-bottom:1.5rem;}
.price-card.hot .price-tier{color:rgba(0,0,0,.5);}
.price-from{font-family:var(--cond);font-size:5rem;font-weight:900;line-height:1;color:var(--white);}
.price-card.hot .price-from{color:var(--black);}
.price-from sup{font-size:1.4rem;vertical-align:super;}
.price-sub{font-family:var(--mono);font-size:.6rem;color:rgba(240,236,227,.35);letter-spacing:.1em;margin-bottom:1.5rem;display:block;}
.price-card.hot .price-sub{color:rgba(0,0,0,.4);}
.price-desc{font-size:.85rem;color:rgba(240,236,227,.55);line-height:1.7;margin-bottom:1.5rem;}
.price-card.hot .price-desc{color:rgba(0,0,0,.6);}
.price-list{list-style:none;display:flex;flex-direction:column;gap:.4rem;}
.price-list li{font-family:var(--mono);font-size:.62rem;letter-spacing:.04em;color:rgba(240,236,227,.45);display:flex;align-items:center;gap:.5rem;}
.price-list li::before{content:'→';color:var(--orange);flex-shrink:0;}
.price-card.hot .price-list li{color:rgba(0,0,0,.55);}
.price-card.hot .price-list li::before{color:rgba(0,0,0,.4);}
.price-cta{display:block;margin-top:2.5rem;font-family:var(--mono);font-size:.65rem;letter-spacing:.12em;text-transform:uppercase;text-decoration:none;border:1px solid rgba(240,236,227,.2);color:var(--white);padding:.9rem 1.5rem;text-align:center;transition:border-color .2s,color .2s,background .2s;}
.price-cta:hover{border-color:var(--lime);color:var(--lime);}
.price-card.hot .price-cta{border:none;background:var(--black);color:var(--lime);text-align:center;}
.price-card.hot .price-cta:hover{background:#111;color:var(--lime);}
/* inline payments bar */
.pay-bar{background:var(--card);padding:1.2rem 2.5rem;display:flex;gap:2rem;align-items:center;flex-wrap:wrap;}
.pay-bar-label{font-family:var(--mono);font-size:.55rem;letter-spacing:.2em;color:rgba(240,236,227,.3);text-transform:uppercase;}
.pay-chip{display:flex;align-items:center;gap:.4rem;font-family:var(--mono);font-size:.58rem;letter-spacing:.06em;color:rgba(240,236,227,.45);text-transform:uppercase;}
.pay-chip-dot{width:8px;height:8px;border-radius:50%;}

/* REWARDS */
#rewards{background:var(--black);}
.rewards-grid{display:grid;grid-template-columns:repeat(3,1fr);max-width:1280px;margin:3rem auto 0;}
.reward-card{padding:3rem 2.5rem;border-top:3px solid transparent;}
.reward-card:nth-child(1){border-top-color:#cd7f32;}
.reward-card:nth-child(2){border-top-color:#a0aab0;border-left:1px solid var(--border);border-right:1px solid var(--border);}
.reward-card.gold{border-top-color:var(--lime);}
.reward-tier{font-family:var(--mono);font-size:.58rem;letter-spacing:.22em;color:rgba(240,236,227,.35);text-transform:uppercase;margin-bottom:.4rem;}
.reward-name{font-family:var(--cond);font-size:3rem;font-weight:900;text-transform:uppercase;line-height:1;margin-bottom:.3rem;}
.reward-card:nth-child(1) .reward-name{color:#cd7f32;}
.reward-card:nth-child(2) .reward-name{color:#a0aab0;}
.reward-card.gold .reward-name{color:var(--lime);}
.reward-threshold{font-family:var(--mono);font-size:.58rem;letter-spacing:.15em;color:rgba(240,236,227,.25);text-transform:uppercase;margin-bottom:1.5rem;padding-bottom:1.5rem;border-bottom:1px solid var(--border);}
.reward-perks{list-style:none;}
.reward-perks li{font-size:.82rem;color:rgba(240,236,227,.5);padding:.4rem 0;display:flex;align-items:center;gap:.5rem;border-bottom:1px solid rgba(255,255,255,.04);}
.reward-perks li:last-child{border-bottom:none;}
.reward-perks li::before{content:'·';color:var(--lime);font-size:1.2rem;flex-shrink:0;}

/* ORARI */
#orari{background:var(--dark);}
.orari-layout{display:grid;grid-template-columns:1fr 1fr;gap:5rem;max-width:1280px;margin:3rem auto 0;}
.orari-table{display:flex;flex-direction:column;gap:1px;}
.orari-row{display:flex;justify-content:space-between;align-items:center;padding:1rem 1.5rem;background:var(--card);}
.orari-day{font-family:var(--mono);font-size:.65rem;letter-spacing:.15em;color:rgba(240,236,227,.35);text-transform:uppercase;}
.orari-time{font-family:var(--cond);font-size:1.1rem;font-weight:700;color:var(--white);display:flex;align-items:center;gap:.8rem;}
.orari-row.special .orari-day{color:var(--lime);}
.drop-badge{background:var(--lime);color:var(--black);font-family:var(--mono);font-size:.5rem;letter-spacing:.15em;padding:.25rem .55rem;text-transform:uppercase;}
.orari-online{margin-top:1px;background:var(--card);padding:1.2rem 1.5rem;border-left:2px solid var(--lime);}
.online-dot{width:8px;height:8px;border-radius:50%;background:#4ade80;display:inline-block;margin-right:.6rem;animation:pulse 2s infinite;}
.online-text{font-family:var(--mono);font-size:.6rem;letter-spacing:.12em;color:rgba(240,236,227,.4);text-transform:uppercase;line-height:1.7;}
.servizi-list2{display:flex;flex-direction:column;gap:1px;}
.servizio2{background:var(--card);padding:1.4rem 1.8rem;display:flex;gap:1.2rem;align-items:flex-start;border-left:2px solid transparent;transition:border-color .2s,background .2s;}
.servizio2:hover{border-color:var(--lime);background:var(--card2);}
.s2-icon{font-size:1.2rem;flex-shrink:0;}
.s2-title{font-family:var(--cond);font-size:1rem;font-weight:800;text-transform:uppercase;color:var(--white);margin-bottom:.2rem;}
.s2-tag{font-family:var(--mono);font-size:.58rem;letter-spacing:.12em;color:var(--lime);text-transform:uppercase;}

/* APP */
#app{background:var(--lime);padding:4rem 2.5rem;}
.app-inner{max-width:1280px;margin:0 auto;display:flex;justify-content:space-between;align-items:center;gap:3rem;}
.app-big{font-family:var(--cond);font-size:clamp(2.5rem,6vw,5rem);font-weight:900;text-transform:uppercase;color:var(--black);line-height:.9;margin-bottom:.5rem;}
.app-big span{color:var(--orange);}
.app-desc{font-size:.85rem;color:rgba(0,0,0,.55);line-height:1.7;max-width:380px;}
.app-btns{display:flex;gap:1px;}
.app-btn{background:var(--black);color:var(--white);display:flex;align-items:center;gap:.8rem;padding:1rem 1.8rem;text-decoration:none;transition:background .2s;}
.app-btn:hover{background:#222;}
.app-btn-icon{font-size:1.4rem;}
.app-btn-sub{font-family:var(--mono);font-size:.5rem;letter-spacing:.15em;color:rgba(240,236,227,.4);text-transform:uppercase;}
.app-btn-name{font-family:var(--cond);font-size:1rem;font-weight:700;text-transform:uppercase;color:var(--white);}

/* DEMO */
#demo{background:var(--dark);padding:5rem 2.5rem;text-align:center;}
.demo-inner{max-width:800px;margin:0 auto;}
.demo-tag{font-family:var(--mono);font-size:.6rem;letter-spacing:.25em;color:rgba(240,236,227,.35);text-transform:uppercase;background:var(--card);padding:.4rem 1.2rem;display:inline-block;margin-bottom:2rem;border:1px solid var(--border);}
.demo-title{font-family:var(--cond);font-size:clamp(3rem,8vw,7rem);font-weight:900;text-transform:uppercase;font-style:italic;line-height:.9;color:var(--white);margin-bottom:1.5rem;}
.demo-sub{font-size:.92rem;color:rgba(240,236,227,.5);line-height:1.75;margin-bottom:2.5rem;}
.demo-sub strong{color:var(--white);}
.demo-ig{display:inline-flex;align-items:center;gap:.8rem;background:var(--lime);padding:1rem 2rem;font-family:var(--mono);font-size:.75rem;letter-spacing:.12em;color:var(--black);text-decoration:none;font-weight:700;text-transform:uppercase;transition:background .2s;}
.demo-ig:hover{background:var(--orange);color:var(--white);}

/* FOOTER */
footer{background:var(--dark);border-top:1px solid var(--border);padding:4rem 2.5rem 2rem;}
.footer-top{display:grid;grid-template-columns:2fr 1fr 1fr 1fr;gap:3rem;max-width:1280px;margin:0 auto 3rem;}
.f-logo{font-family:var(--cond);font-size:2rem;font-weight:900;color:var(--lime);text-decoration:none;letter-spacing:.06em;display:block;margin-bottom:1rem;}
.f-logo sup{font-size:.5rem;color:var(--orange);}
.f-desc{font-size:.78rem;color:rgba(240,236,227,.28);line-height:1.7;max-width:240px;font-style:italic;margin-bottom:1rem;}
.f-col-title{font-family:var(--mono);font-size:.58rem;letter-spacing:.25em;color:var(--orange);text-transform:uppercase;margin-bottom:1.5rem;}
.f-links{list-style:none;display:flex;flex-direction:column;gap:.5rem;}
.f-links a{font-size:.8rem;color:rgba(240,236,227,.3);text-decoration:none;transition:color .2s;}
.f-links a:hover{color:var(--lime);}
.demo-warning{background:rgba(200,255,0,.05);border:1px solid rgba(200,255,0,.1);padding:1.2rem 2rem;max-width:1280px;margin:0 auto 2rem;text-align:center;}
.demo-w-txt{font-family:var(--mono);font-size:.6rem;letter-spacing:.12em;color:rgba(200,255,0,.55);line-height:1.6;}
.footer-bottom{display:flex;justify-content:space-between;align-items:center;padding-top:2rem;border-top:1px solid var(--border);max-width:1280px;margin:0 auto;}
.f-copy{font-family:var(--mono);font-size:.55rem;letter-spacing:.12em;color:rgba(240,236,227,.18);text-transform:uppercase;}
.f-socials{display:flex;gap:1.5rem;}
.f-socials a{font-family:var(--mono);font-size:.55rem;letter-spacing:.15em;color:rgba(240,236,227,.25);text-decoration:none;text-transform:uppercase;transition:color .2s;}
.f-socials a:hover{color:var(--lime);}

/* ANIMATIONS */
@keyframes fup{from{opacity:0;transform:translateY(28px);}to{opacity:1;transform:translateY(0);}}
@keyframes ticker{from{transform:translateX(0);}to{transform:translateX(-50%);}}
@keyframes pulse{0%,100%{opacity:1;}50%{opacity:.3;}}
.reveal{opacity:0;transform:translateY(32px);transition:opacity .75s cubic-bezier(.2,.8,.2,1),transform .75s cubic-bezier(.2,.8,.2,1);}
.reveal.visible{opacity:1;transform:translateY(0);}
.d1{transition-delay:.1s;}.d2{transition-delay:.2s;}.d3{transition-delay:.3s;}.d4{transition-delay:.4s;}

@media(max-width:960px){
  nav{padding:0 1.5rem;}nav ul{display:none;}
  section{padding:4rem 1.5rem;}
  .manifesto-grid,.custom-layout,.sost-layout,.orari-layout,.app-inner{grid-template-columns:1fr;gap:3rem;}
  .coll-grid,.bs-grid{grid-template-columns:1fr 1fr;}
  .coll-card.featured{grid-column:auto;}
  .proc-steps{flex-direction:column;}
  .footer-top{grid-template-columns:1fr 1fr;}
  .comp-prizes,.comp-steps-row{grid-template-columns:1fr 1fr;}
  .comp-top,.comp-bottom{grid-template-columns:1fr;}
  .past-winners-row{flex-wrap:wrap;}
  .price-grid,.rewards-grid{grid-template-columns:1fr;}
  .custom-rules .rules-grid{grid-template-columns:1fr 1fr;}
  .hero-float-row{flex-wrap:wrap;}
}
</style>
</head>
<body>

<div id="cur"></div>
<div id="cur-ring"></div>

<!-- NAV -->
<nav>
  <a href="#" class="nav-logo"><span class="nav-logo-icon"></span>VIVET<sup>°</sup></a>
  <ul>
    <li><a href="#collezioni">Collezioni</a></li>
    <li><a href="#custom">Custom Program</a></li>
    <li><a href="#competition">Competition</a></li>
    <li><a href="#prezzi">Prezzi</a></li>
    <li><a href="#rewards">Loyalty</a></li>
    <li><a href="#custom" class="nav-btn">Shop Now</a></li>
  </ul>
</nav>

<!-- HERO -->
<section id="hero">
  <div class="hero-bg-text">VIVET</div>
  <div class="hero-eyebrow">Brand italiano — Fondato a Milano 2024</div>
  <h1 class="hero-h1">
    <span class="line1">WE</span>
    <span class="line2">DESIGN</span>
    <span class="line3">CULTURE</span>
  </h1>
  <!-- FLOATING STATS -->
  <div class="hero-float-row">
    <div class="hfloat">
      <div class="hfloat-num">100%</div>
      <div class="hfloat-label">Originale</div>
    </div>
    <div class="hfloat">
      <div class="hfloat-num">3×</div>
      <div class="hfloat-label">Custom Chance</div>
    </div>
    <div class="hfloat">
      <div class="hfloat-num">NEW</div>
      <div class="hfloat-label">Comp. Mensile</div>
    </div>
  </div>
  <!-- CTA BUTTONS -->
  <div class="hero-cta-row">
    <a href="#custom" class="hero-btn-main">✦ Custom Program</a>
    <a href="#competition" class="hero-btn-sec">Monthly Competition →</a>
  </div>
</section>

<!-- TICKER -->
<div class="ticker-outer">
  <div class="ticker-inner">
    <span class="t-item">DESIGN ORIGINALE <span class="t-dot">·</span></span>
    <span class="t-item">PRODUZIONE ETICA <span class="t-dot">·</span></span>
    <span class="t-item">MADE IN ITALIA <span class="t-dot">·</span></span>
    <span class="t-item">3 CUSTOM CHANCES <span class="t-dot">·</span></span>
    <span class="t-item">SOLO TUO — NESSUN ALTRO <span class="t-dot">·</span></span>
    <span class="t-item">MONTHLY COMPETITION <span class="t-dot">·</span></span>
    <span class="t-item">VINCI 2000 PUNTI <span class="t-dot">·</span></span>
    <span class="t-item">DROP OGNI VENERDÌ <span class="t-dot">·</span></span>
    <span class="t-item">RESO GRATUITO 30GG <span class="t-dot">·</span></span>
    <span class="t-item">DESIGN ORIGINALE <span class="t-dot">·</span></span>
    <span class="t-item">PRODUZIONE ETICA <span class="t-dot">·</span></span>
    <span class="t-item">MADE IN ITALIA <span class="t-dot">·</span></span>
    <span class="t-item">3 CUSTOM CHANCES <span class="t-dot">·</span></span>
    <span class="t-item">SOLO TUO — NESSUN ALTRO <span class="t-dot">·</span></span>
    <span class="t-item">MONTHLY COMPETITION <span class="t-dot">·</span></span>
    <span class="t-item">VINCI 2000 PUNTI <span class="t-dot">·</span></span>
    <span class="t-item">DROP OGNI VENERDÌ <span class="t-dot">·</span></span>
    <span class="t-item">RESO GRATUITO 30GG <span class="t-dot">·</span></span>
  </div>
</div>

<!-- MANIFESTO -->
<section id="manifesto">
  <div class="manifesto-grid">
    <div class="manifesto-left reveal">
      <div class="s-label">Il Nostro Manifesto</div>
      <h2 class="s-title" style="color:var(--black)">NON VENDIAMO<br>VESTITI.<br><span class="acc-o">VENDIAMO<br>IDENTITÀ.</span></h2>
      <blockquote class="manifesto-quote">«VIVET nasce da un'idea semplice: i giovani meritano un brand tutto loro, non l'ennesimo rivenditore.»</blockquote>
      <p class="manifesto-text">Tutto ciò che vedi è disegnato, sviluppato e prodotto dal nostro team di <strong>designer under-30</strong>. Ogni stagione una nuova collezione con un tema visivo preciso.</p>
      <p class="manifesto-text">Ogni capo racconta una storia. Ogni drop è un evento. E con il nostro Custom Program, <strong>la storia può essere la tua</strong>.</p>
    </div>
    <div class="manifesto-right reveal d2">
      <div class="pillar"><div class="pillar-icon">✏️</div><div><div class="pillar-title">100% Originale</div><div class="pillar-desc">Nessun logo di terze parti. Ogni grafica è firmata VIVET — progettata dal nostro team, non rivenduta.</div></div></div>
      <div class="pillar"><div class="pillar-icon">🌿</div><div><div class="pillar-title">Etico & Sostenibile</div><div class="pillar-desc">Cotone organico certificato GOTS, tinture naturali, filiera tracciata. Scansiona il QR e vedi dove è nato il tuo capo.</div></div></div>
      <div class="pillar"><div class="pillar-icon">🎨</div><div><div class="pillar-title">Custom Program</div><div class="pillar-desc">3 possibilità all'anno per creare un capo unico, solo tuo, firmato VIVET. Nessun altro al mondo lo avrà.</div></div></div>
      <div class="pillar"><div class="pillar-icon">🏆</div><div><div class="pillar-title">Monthly Competition</div><div class="pillar-desc">Il tuo design potrebbe diventare reale. Vinci il capo fisico + 1.000–1.500 punti VIVET Rewards.</div></div></div>
    </div>
  </div>
</section>

<!-- COLLEZIONI -->
<section id="collezioni" style="padding-bottom:0;">
  <div class="coll-header reveal">
    <div class="s-label">Le Nostre Linee</div>
    <h2 class="s-title">6 COLLEZIONI <span class="acc">ORIGINALI</span></h2>
  </div>
  <div class="coll-grid">
    <div class="coll-card featured reveal"><div class="coll-badge">Collezione Principale</div><div><div class="coll-tag">// Origins SS26</div><div class="coll-name">ORIGINS</div><div class="coll-desc">Hoodie · Tee · Cargo · Jacket — la collezione che definisce l'estetica VIVET.</div></div><div class="coll-price">Da €19</div></div>
    <div class="coll-card reveal d1"><div><div class="coll-tag">// Dark Series</div><div class="coll-name">VOID</div><div class="coll-desc">Toni scuri, tagli minimal, essenzialismo radicale.</div></div><div class="coll-price">Da €24</div></div>
    <div class="coll-card reveal d1"><div><div class="coll-tag">// Earth Tones</div><div class="coll-name">TERRA</div><div class="coll-desc">Beige · Sabbia · Marrone — palette terrosa, materiali naturali.</div></div><div class="coll-price">Da €22</div></div>
    <div class="coll-card reveal d2"><div><div class="coll-tag">// Workwear Rivisitato</div><div class="coll-name">RAW WORK</div><div class="coll-desc">Utility · Cargo · Overshirt — estetica cantiere reinterpretata.</div></div><div class="coll-price">Da €29</div></div>
    <div class="coll-card reveal d2"><div class="coll-badge" style="background:#8B6914">Edizione Limitata</div><div><div class="coll-tag">// Drop Limitato</div><div class="coll-name">KANTO</div><div class="coll-desc">100 pezzi numerati. Una volta sold out, non torna.</div></div><div class="coll-price">Da €59</div></div>
    <div class="coll-card reveal d3"><div><div class="coll-tag">// Sempre Disponibile</div><div class="coll-name">CLASSIC</div><div class="coll-desc">VIVET Essentials senza tempo — i pezzi fondamentali del guardaroba.</div></div><div class="coll-price">Da €17</div></div>
  </div>
</section>

<!-- BESTSELLER — con foto reali da Unsplash -->
<section id="bestseller" style="padding:5rem 0 0;">
  <div class="bs-section-head reveal" style="padding:0 2.5rem 2.5rem;">
    <div class="s-label">// Bestseller</div>
    <h2 class="s-title">I CAPI <span class="acc">PIÙ AMATI</span></h2>
  </div>
  <div class="bs-grid">
    <!-- 1 -->
    <div class="bs-card reveal">
      <div class="bs-img">
        <span class="bs-badge best">BESTSELLER</span>
        <img src="https://images.unsplash.com/photo-1556821840-3a63f15732ce?w=600&q=80" alt="VIVET Heavy Hoodie" loading="lazy">
      </div>
      <div class="bs-colors">
        <div class="bs-dot active" style="background:#1a1a1a;"></div>
        <div class="bs-dot" style="background:#3d3d3d;"></div>
        <div class="bs-dot" style="background:#5c4a38;"></div>
      </div>
      <div class="bs-body">
        <div class="bs-line">// Origins SS26</div>
        <div class="bs-name">VIVET HEAVY HOODIE</div>
        <div class="bs-desc">Felpa oversize 380gsm, cotone organico. Logo arcuato VIVET° sul petto. Grafica originale sul retro. Kangaroo pocket zip.</div>
        <div class="bs-hover-link">Passa il mouse per vedere il retro →</div>
      </div>
      <div class="bs-price-row"><div class="bs-price">€59</div><div class="bs-add">+</div></div>
    </div>
    <!-- 2 -->
    <div class="bs-card reveal d1">
      <div class="bs-img">
        <span class="bs-badge new">NEW</span>
        <img src="https://images.unsplash.com/photo-1529374255404-311a2a4f1fd9?w=600&q=80" alt="Acid Logo Tee" loading="lazy">
      </div>
      <div class="bs-colors">
        <div class="bs-dot active" style="background:#1a1a1a;"></div>
        <div class="bs-dot" style="background:#f0f0f0;border-color:rgba(0,0,0,.2);"></div>
        <div class="bs-dot" style="background:#555;"></div>
      </div>
      <div class="bs-body">
        <div class="bs-line">// Origins SS26</div>
        <div class="bs-name">ACID LOGO TEE</div>
        <div class="bs-desc">T-shirt oversize 220gsm cotone organico. Logo arcuato VIVET° sul petto. Personaggio grafico originale sul retro.</div>
        <div class="bs-hover-link">Passa il mouse per vedere il retro →</div>
      </div>
      <div class="bs-price-row"><div class="bs-price">€29</div><div class="bs-add">+</div></div>
    </div>
    <!-- 3 -->
    <div class="bs-card reveal d2">
      <div class="bs-img">
        <span class="bs-badge top">TOP 10</span>
        <img src="https://images.unsplash.com/photo-1624378439575-d8705ad7ae80?w=600&q=80" alt="Raw Cargo Pants" loading="lazy">
      </div>
      <div class="bs-colors">
        <div class="bs-dot active" style="background:#2a2a2a;"></div>
        <div class="bs-dot" style="background:#4a4a4a;"></div>
      </div>
      <div class="bs-body">
        <div class="bs-line">// Raw Work</div>
        <div class="bs-name">RAW CARGO PANTS</div>
        <div class="bs-desc">Cargo 6 tasche canvas 300gsm. Elastico caviglie, straight leg.</div>
      </div>
      <div class="bs-price-row"><div class="bs-price">€69</div><div class="bs-add">+</div></div>
    </div>
    <!-- 4 -->
    <div class="bs-card reveal d3">
      <div class="bs-img">
        <span class="bs-badge lim">LIMITED</span>
        <img src="https://images.unsplash.com/photo-1588850561407-ed78c282e89b?w=600&q=80" alt="Kanto Cap" loading="lazy">
      </div>
      <div class="bs-colors">
        <div class="bs-dot active" style="background:#1a1a1a;"></div>
        <div class="bs-dot" style="background:#3d3d3d;"></div>
      </div>
      <div class="bs-body">
        <div class="bs-line">// Kanto Limited</div>
        <div class="bs-name">KANTO° 6-PANEL CAP</div>
        <div class="bs-desc">6 pannelli twill pesante. Logo 3D ricamato. Solo 100 pezzi numerati.</div>
      </div>
      <div class="bs-price-row"><div class="bs-price">€39</div><div class="bs-add">+</div></div>
    </div>
  </div>
</section>

<!-- CUSTOM PROGRAM -->
<section id="custom">
  <div class="custom-layout">
    <div class="custom-left reveal">
      <div class="s-label">Solo per Te</div>
      <div style="font-family:var(--cond);font-size:1.1rem;font-weight:800;color:var(--lime);letter-spacing:.12em;text-transform:uppercase;margin-bottom:.5rem;">VIVET<sup style="font-size:.55rem;color:var(--orange);vertical-align:super;">°</sup></div>
      <h2 class="s-title"><span class="acc">CUSTOM</span><br>PROGRAM</h2>
      <p>Ogni cliente VIVET ha <strong>3 possibilità esclusive all'anno</strong> di creare un capo d'abbigliamento unico nel suo genere — disegnato da te, prodotto da noi, con il logo o il nome VIVET integrato nel design. Nessun altro al mondo avrà quel capo.</p>
      <p>Il tuo design viene realizzato dai nostri artigiani su misura. Puoi scegliere il tipo di capo, i colori, la grafica — l'unica regola è che il <strong>nome o il logo VIVET deve essere parte del design</strong>. Non un'aggiunta: una firma condivisa, un pezzo di identità comune.</p>
      <p>Una volta prodotto, quel capo è <span class="solo-tuo">solo tuo</span>. Non viene replicato, non viene venduto, non viene rifatto. Mai.</p>
      <div class="custom-bullets">
        <div class="custom-bullet">3 CUSTOM CHANCES PER ANNO</div>
        <div class="custom-bullet">LOGO / NOME VIVET NEL DESIGN</div>
        <div class="custom-bullet">1 SOLO PEZZO — MAI REPLICATO</div>
        <div class="custom-bullet">PRODUZIONE ARTIGIANALE CERTIFICATA</div>
        <div class="custom-bullet">SI RINNOVANO OGNI 1° GENNAIO</div>
      </div>
    </div>
    <div class="custom-right reveal d2">
      <div class="custom-step">
        <div class="step-num-box">1</div>
        <div>
          <div class="step-title">PRIMA CHANCE</div>
          <div class="step-sub-tag">SKETCH / BRIEF → BOZZA DIGITALE</div>
          <div class="step-desc">Scegli il capo, invia il tuo sketch o brief creativo. Il nostro team ti guida nella realizzazione e propone una bozza digitale entro 5 giorni.</div>
        </div>
      </div>
      <div class="custom-step">
        <div class="step-num-box">2</div>
        <div>
          <div class="step-title">SECONDA CHANCE</div>
          <div class="step-sub-tag">REVISIONI → APPROVAZIONE FINALE</div>
          <div class="step-desc">Hai fino a 2 revisioni gratuite sulla bozza prima che il capo vada in produzione. Ogni dettaglio dev'essere perfetto.</div>
        </div>
      </div>
      <div class="custom-step">
        <div class="step-num-box">3</div>
        <div>
          <div class="step-title">TERZA CHANCE</div>
          <div class="step-sub-tag">PRODUZIONE → CERTIFICATO UNICITÀ</div>
          <div class="step-desc">Il tuo capo unico viene prodotto artigianalmente con un certificato di unicità firmato VIVET. Solo 1 pezzo. Solo tuo.</div>
        </div>
      </div>
    </div>
  </div>
  <!-- REGOLE -->
  <div class="custom-rules reveal">
    <div class="rules-head">
      <span class="rules-head-icon">📋</span>
      <span class="rules-head-title">LE REGOLE DEL CUSTOM PROGRAM</span>
    </div>
    <div class="rules-grid">
      <div class="rule-card"><div class="rule-icon">🖊️</div><div class="rule-title">LOGO VIVET NEL DESIGN</div><div class="rule-text">Il nome o il logo VIVET deve essere visivamente integrato nella grafica del capo — non solo stampato dietro. È la nostra firma comune.</div></div>
      <div class="rule-card"><div class="rule-icon">🔒</div><div class="rule-title">UNICITÀ GARANTITA</div><div class="rule-text">Una volta prodotto il tuo custom, il design viene archiviato come esclusivo. Non sarà mai riprodotto, né in modo identico né simile.</div></div>
      <div class="rule-card"><div class="rule-icon">🎟️</div><div class="rule-title">3 VOLTE ALL'ANNO</div><div class="rule-text">Ogni account riceve 3 custom chances ogni anno solare. Si rinnovano il 1° gennaio. Non sono trasferibili né si possono usare in qualsiasi momento dell'anno.</div></div>
      <div class="rule-card"><div class="rule-icon">🧵</div><div class="rule-title">QUALITÀ VIVET STANDARD</div><div class="rule-text">I capi custom usano gli stessi materiali della linea principale: cotone organico certificato, tinture sicure, rifinitura artigianale.</div></div>
      <div class="rule-card"><div class="rule-icon">⚠️</div><div class="rule-title">CONTENUTI ACCETTATI</div><div class="rule-text">Nessun contenuto offensivo, discriminatorio o che violi copyright. VIVET si riserva il diritto di rifiutare design non conformi.</div></div>
      <div class="rule-card"><div class="rule-icon">⏱️</div><div class="rule-title">TEMPI DI PRODUZIONE</div><div class="rule-text">Dalla bozza approvata alla consegna: 3–4 settimane. Il capo arriva con packaging speciale e certificato di unicità numerato.</div></div>
    </div>
  </div>
</section>

<!-- COMPETITION -->
<section id="competition">
  <div class="comp-top reveal">
    <div class="comp-top-left">
      <div class="s-label">// Ogni Mese</div>
      <h2 class="s-title">VIVET DESIGN <span class="acc">COMPETITION</span></h2>
      <p>Ogni mese VIVET lancia una competizione di design aperta a tutti. Invii il tuo disegno per un capo VIVET — può essere una hoodie, una tee, un cargo — e <strong>la community vota</strong>. <strong>Il design vincitore viene prodotto davvero</strong>, il vincitore riceve il capo fisico e tra <strong>1.000–1.500 punti VIVET Rewards</strong>.</p>
      <p>Non serve saper disegnare in modo professionale — serve un'idea forte, uno stile autentico e il logo o nome VIVET integrato nel design. Ogni mese un tema diverso. Ogni mese un vincitore reale.</p>
    </div>
    <div class="comp-timer reveal d2">
      <div class="timer-label">Prossima Gara</div>
      <div class="timer-num" id="timer-num">24</div>
      <div class="timer-sub">Giorni al voto</div>
    </div>
  </div>
  <!-- 4 prize cards -->
  <div class="comp-prizes reveal">
    <div class="prize-card">
      <span class="prize-icon">🏆</span>
      <div class="prize-name">IL TUO CAPO</div>
      <div class="prize-sub">Premio Principale</div>
      <div class="prize-desc">Il design vincitore viene prodotto fisicamente da VIVET e spedito al vincitore. Reale. Indossabile. Tuo.</div>
    </div>
    <div class="prize-card">
      <span class="prize-icon">⭐</span>
      <div class="prize-name">1.000–1.500</div>
      <div class="prize-sub">Punti VIVET Rewards</div>
      <div class="prize-desc">Equivale a €20 di sconto sui prossimi acquisti o sali di livello nel programma fedeltà.</div>
    </div>
    <div class="prize-card">
      <span class="prize-icon">📸</span>
      <div class="prize-name">FEATURE</div>
      <div class="prize-sub">Social VIVET</div>
      <div class="prize-desc">Il vincitore e il suo design vengono presentati su tutti i canali social VIVET con credit completo.</div>
    </div>
    <div class="prize-card">
      <span class="prize-icon">🎖️</span>
      <div class="prize-name">HALL</div>
      <div class="prize-sub">of Fame Permanente</div>
      <div class="prize-desc">Il tuo nome entra nella Hall of Fame VIVET sul sito, visibile per sempre accanto al design vincente.</div>
    </div>
  </div>
  <!-- 4 steps -->
  <div class="comp-bottom reveal">
    <div class="comp-steps-row">
      <div class="comp-step-card"><div class="comp-step-icon">✏️</div><div class="comp-step-title">DISEGNA</div><div class="comp-step-desc">Crea il tuo design — sketch, digitale, collage. Il capo deve avere il logo o nome VIVET integrato. Tema del mese obbligatorio.</div></div>
      <div class="comp-step-card"><div class="comp-step-icon">📤</div><div class="comp-step-title">INVIA</div><div class="comp-step-desc">Carica il design sull'app o sul sito nella sezione Competition entro la deadline (ultimo giorno del mese).</div></div>
      <div class="comp-step-card"><div class="comp-step-icon">🗳️</div><div class="comp-step-title">LA COMMUNITY VOTA</div><div class="comp-step-desc">Per i primi 5 giorni del mese successivo tutti i clienti VIVET votano il loro design preferito. 1 voto a testa, anonimo.</div></div>
      <div class="comp-step-card"><div class="comp-step-icon">🎉</div><div class="comp-step-title">IL VINCITORE</div><div class="comp-step-desc">Il design con più voti vince. VIVET produce il capo e lo spedisce. Il vincitore riceve anche 1.000–1.500 punti Rewards.</div></div>
    </div>
  </div>
  <!-- past winners -->
  <div class="past-winners-row reveal">
    <div class="pw-label"><span class="pw-label-icon">🥇</span><span class="pw-label-txt">Past Winners</span></div>
    <div class="pw-item"><span class="pw-medal">🏅</span><div><div class="pw-month">GEN 2025</div><div class="pw-name">@marco.design</div><div class="pw-design">Black Frost Hoodie</div></div></div>
    <div class="pw-item"><span class="pw-medal">🏅</span><div><div class="pw-month">FEB 2025</div><div class="pw-name">@sara_cre8</div><div class="pw-design">Terra Cargo Pants</div></div></div>
    <div class="pw-item"><span class="pw-medal">🏅</span><div><div class="pw-month">MAR 2025</div><div class="pw-name">@luca.vibes</div><div class="pw-design">Void Logo Tee</div></div></div>
    <div class="pw-item"><span class="pw-medal">🏅</span><div><div class="pw-month">APR 2025</div><div class="pw-name">@giuly_art</div><div class="pw-design">Origins Cap</div></div></div>
  </div>
  <!-- CTA buttons -->
  <div class="comp-cta-row reveal">
    <a href="#" class="comp-btn-lime">🏆 Partecipa alla Competizione</a>
    <a href="#" class="comp-btn-out">Vedi tutti i design →</a>
  </div>
</section>

<!-- PROCESSO -->
<section id="processo">
  <div class="reveal">
    <div class="s-label">Come nasce un capo VIVET</div>
    <h2 class="s-title">DAL FOGLIO <span class="acc-o">ALLO STORE</span></h2>
  </div>
  <div class="proc-steps">
    <div class="proc-step reveal"><div class="proc-n">01</div><span class="proc-icon">💡</span><div class="proc-title">CONCEPT</div><div class="proc-desc">Il team propone un tema. La community vota grafiche e palette via app.</div></div>
    <div class="proc-step reveal d1"><div class="proc-n">02</div><span class="proc-icon">✏️</span><div class="proc-title">DESIGN</div><div class="proc-desc">Designer under-30: sketch a mano, poi digitalizzati e mockup.</div></div>
    <div class="proc-step reveal d2"><div class="proc-n">03</div><span class="proc-icon">🧵</span><div class="proc-title">PROTOTIPO</div><div class="proc-desc">Campioni nei nostri atelier. Test vestibilità su persone reali.</div></div>
    <div class="proc-step reveal d3"><div class="proc-n">04</div><span class="proc-icon">🌿</span><div class="proc-title">PRODUZIONE</div><div class="proc-desc">Manifattura etica certificata. Cotone GOTS, tinture sicure.</div></div>
    <div class="proc-step reveal d4"><div class="proc-n">05</div><span class="proc-icon">🔥</span><div class="proc-title">DROP</div><div class="proc-desc">Ogni venerdì ore 12:00. Quantità limitate. Push notification 1h prima.</div></div>
  </div>
</section>

<!-- SOSTENIBILITÀ -->
<section id="sostenibilita">
  <div class="sost-layout">
    <div class="sost-metrics reveal">
      <div class="metric-card"><div class="metric-num">100%</div><div class="metric-label">Cotone organico<br>certificato GOTS<br>in tutti i capi base</div></div>
      <div class="metric-card"><div class="metric-num">0</div><div class="metric-label">Plastica negli imballaggi.<br>Carta riciclata,<br>inchiostro acqua</div></div>
      <div class="metric-card"><div class="metric-num">CO₂</div><div class="metric-label">Offset certificato<br>per ogni ordine,<br>1 albero ogni 50 ordini</div></div>
      <div class="metric-card"><div class="metric-num">Fair</div><div class="metric-label">Fornitori certificati SA8000.<br>Salari giusti,<br>condizioni sicure</div></div>
    </div>
    <div class="sost-text reveal d2">
      <div class="s-label">// Sostenibilità</div>
      <div class="sost-big">STILE SENZA<br><span class="acc">COMPROMESSI</span></div>
      <p>VIVET produce in modo etico, usa materiali sostenibili e ha una filiera trasparente. <strong>Scansiona il QR su ogni capo</strong> e vedi dove è stato prodotto.</p>
      <p>Crediamo che la moda giovanile non debba scegliere tra stile e responsabilità. Con VIVET non scegli: hai entrambi.</p>
    </div>
  </div>
</section>

<!-- PREZZI -->
<section id="prezzi" style="padding:5rem 0 0;">
  <div class="prezzi-head reveal">
    <div class="s-label">// Fasce Prezzo</div>
    <h2 class="s-title">PREZZI <span class="acc">ONESTI</span></h2>
  </div>
  <div class="price-grid">
    <div class="price-card reveal">
      <div class="price-tier">// Entry — Accessori & Tee</div>
      <div class="price-from"><sup>€</sup>19</div>
      <div class="price-sub">— prezzi a partire da</div>
      <p class="price-desc">T-shirt, calzini, cappellini. Il look VIVET senza grandi spese.</p>
      <ul class="price-list"><li>T-shirt 220gsm da €19</li><li>Calzini logo da €9</li><li>Beanie ricamato da €19</li><li>Tote bag da €14</li></ul>
      <a href="#" class="price-cta">VEDI PRODOTTI →</a>
    </div>
    <div class="price-card hot reveal d1">
      <div class="price-tier">// Core — Hoodie & Pants</div>
      <div class="price-from"><sup>€</sup>59</div>
      <div class="price-sub">— fascia principale</div>
      <p class="price-desc">Hoodie pesante, cargo pants, giacche. Qualità premium, prezzo giusto.</p>
      <ul class="price-list"><li>Hoodie 380gsm da €59</li><li>Cargo pants da €69</li><li>Crewneck da €49</li><li>3 rate senza interessi</li></ul>
      <a href="#" class="price-cta">SHOP NOW →</a>
    </div>
    <div class="price-card reveal d2">
      <div class="price-tier">// Custom Program</div>
      <div class="price-from"><sup>€</sup>89</div>
      <div class="price-sub">— capo custom unico</div>
      <p class="price-desc">Il tuo design. Solo tuo. Con logo VIVET integrato. Certificato di unicità incluso.</p>
      <ul class="price-list"><li>3 custom chances / anno</li><li>Si rinnovano il 1° gennaio</li><li>1 solo pezzo prodotto</li><li>Certificato unicità VIVET</li></ul>
      <a href="#custom" class="price-cta">SCOPRI IL PROGRAMMA →</a>
    </div>
  </div>
  <!-- inline payments -->
  <div class="pay-bar reveal">
    <span class="pay-bar-label">// Pagamenti Accettati</span>
    <div class="pay-chip"><div class="pay-chip-dot" style="background:#1a73e8;"></div>Carta</div>
    <div class="pay-chip"><div class="pay-chip-dot" style="background:#4ade80;"></div>Contanti</div>
    <div class="pay-chip"><div class="pay-chip-dot" style="background:#f0ece3;"></div>Apple/Google Pay</div>
    <div class="pay-chip"><div class="pay-chip-dot" style="background:#003087;"></div>PayPal</div>
    <div class="pay-chip"><div class="pay-chip-dot" style="background:#ffb3c7;"></div>Klarna 3×0%</div>
    <div class="pay-chip"><div class="pay-chip-dot" style="background:#e84c1e;"></div>Scalapay 4 Rate</div>
    <div class="pay-chip"><div class="pay-chip-dot" style="background:#f7931a;"></div>Crypto</div>
    <div class="pay-chip"><div class="pay-chip-dot" style="background:#c8ff00;"></div>Gift Card</div>
  </div>
</section>

<!-- REWARDS -->
<section id="rewards">
  <div class="reveal">
    <div class="s-label">Programma Fedeltà</div>
    <h2 class="s-title">VIVET <span class="acc">REWARDS</span></h2>
    <p style="font-family:var(--mono);font-size:.7rem;color:rgba(240,236,227,.4);max-width:540px;margin-top:1rem;line-height:1.75;letter-spacing:.06em;">Ogni euro speso = 10 punti. Vinci 1.000–1.500 punti extra con la Monthly Competition. Tre livelli, benefici crescenti.</p>
  </div>
  <div class="rewards-grid">
    <div class="reward-card reveal">
      <div class="reward-tier">Da 0 punti</div>
      <div class="reward-name">BRONZE</div>
      <div class="reward-threshold">// Da 0 punti · 10pt per €1</div>
      <ul class="reward-perks"><li>10 punti per ogni €1 speso</li><li>-10% il giorno del compleanno</li><li>Accesso vendite private</li><li>Newsletter preview drop</li><li>Reso gratuito 30 giorni</li><li>Partecipazione Monthly Comp.</li></ul>
    </div>
    <div class="reward-card reveal d1">
      <div class="reward-tier">Da 5.000 punti</div>
      <div class="reward-name">SILVER</div>
      <div class="reward-threshold">// Da 5.000 punti · 15pt per €1</div>
      <ul class="reward-perks"><li>Tutti i benefit Bronze</li><li>15 punti per ogni €1</li><li>-20% compleanno</li><li>Early access drop 24h prima</li><li>Spedizione gratuita sempre</li><li>Voto anticipato Competition</li></ul>
    </div>
    <div class="reward-card gold reveal d2">
      <div class="reward-tier">Da 15.000 punti</div>
      <div class="reward-name">GOLD ★</div>
      <div class="reward-threshold">// Da 15.000 punti · 20pt per €1</div>
      <ul class="reward-perks"><li>Tutti i benefit Silver</li><li>20 punti per ogni €1</li><li>-30% compleanno</li><li>Early access 48h prima</li><li>Nome nei credit collezione</li><li>Giudice ospite Competition</li><li>Gift mensile a sorpresa</li></ul>
    </div>
  </div>
</section>

<!-- ORARI -->
<section id="orari">
  <div class="reveal">
    <div class="s-label">Orari & Servizi</div>
    <h2 class="s-title">TROVACI <span class="acc">QUI</span></h2>
  </div>
  <div class="orari-layout">
    <div class="reveal">
      <div class="orari-table">
        <div class="orari-row special"><span class="orari-day">Lun — Ven</span><span class="orari-time">10:00 — 21:00</span></div>
        <div class="orari-row"><span class="orari-day">Sabato</span><span class="orari-time">09:30 — 22:00 <span class="drop-badge">Drop Day</span></span></div>
        <div class="orari-row"><span class="orari-day">Domenica</span><span class="orari-time">10:00 — 20:00</span></div>
        <div class="orari-row"><span class="orari-day">Festivi</span><span class="orari-time">11:00 — 19:00</span></div>
      </div>
      <div class="orari-online"><span class="online-dot"></span><span class="online-text">// ONLINE 24/7 — Ordini entro le 15:00 → same-day Milano · Entro le 18:00 → next day Italia</span></div>
    </div>
    <div class="servizi-list2 reveal d2">
      <div class="servizio2"><div class="s2-icon">🔄</div><div><div class="s2-title">Reso Gratuito</div><div class="s2-tag">30 giorni</div></div></div>
      <div class="servizio2"><div class="s2-icon">🚀</div><div><div class="s2-title">Same-Day Delivery</div><div class="s2-tag">Milano, entro le 15:00</div></div></div>
      <div class="servizio2"><div class="s2-icon">🎨</div><div><div class="s2-title">Custom Lab</div><div class="s2-tag">3 chances / account / anno</div></div></div>
      <div class="servizio2"><div class="s2-icon">🏆</div><div><div class="s2-title">Monthly Competition</div><div class="s2-tag">Vinci il tuo design</div></div></div>
      <div class="servizio2"><div class="s2-icon">📦</div><div><div class="s2-title">Click & Collect</div><div class="s2-tag">Ritiro gratuito in store</div></div></div>
      <div class="servizio2"><div class="s2-icon">🎂</div><div><div class="s2-title">Birthday Discount</div><div class="s2-tag">−20% il tuo giorno</div></div></div>
    </div>
  </div>
</section>

<!-- APP -->
<section id="app" style="padding:0;">
  <div class="app-inner" style="padding:4rem 2.5rem;">
    <div class="reveal">
      <div class="app-big">SCARICA L'APP<br>VIVET <span>GRATIS</span></div>
      <p class="app-desc">Drop alert, punti Rewards, wishlist, Custom Program, competition voting — tutto in un'unica app gratuita.</p>
    </div>
    <div class="app-btns reveal d2">
      <a href="#" class="app-btn"><div class="app-btn-icon">🍎</div><div><div class="app-btn-sub">Disponibile su</div><div class="app-btn-name">App Store</div></div></a>
      <a href="#" class="app-btn"><div class="app-btn-icon">🤖</div><div><div class="app-btn-sub">Disponibile su</div><div class="app-btn-name">Google Play</div></div></a>
    </div>
  </div>
</section>

<!-- DEMO -->
<section id="demo">
  <div class="demo-inner reveal">
    <div class="demo-tag">⚠️ Questo è un progetto demo</div>
    <div class="demo-title">TI PIACE L'IDEA?</div>
    <p class="demo-sub">VIVET è un <strong>concept di brand</strong> creato come progetto dimostrativo. Se credi nel potenziale di questa idea — il Custom Program, la Monthly Competition, le 6 collezioni originali — contattaci. Vogliamo trasformarlo in una <strong>vera azienda</strong>.</p>
    <div style="display:flex;gap:1px;justify-content:center;flex-wrap:wrap;">
      <a href="https://instagram.com/shubh._.y" target="_blank" class="demo-ig">📸 @shubh._.y</a>
      <a href="https://instagram.com/psng568" target="_blank" class="demo-ig" style="background:var(--card);color:var(--lime);border:1px solid rgba(200,255,0,.3);">📸 @psng568</a>
    </div>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <div class="footer-top">
    <div>
      <a href="#" class="f-logo">VIVET<sup>°</sup></a>
      <p class="f-desc">Non vendiamo vestiti. Vendiamo identità. Design originale, custom program, competizione mensile. Milano, 2024.</p>
    </div>
    <div>
      <div class="f-col-title">Collezioni</div>
      <ul class="f-links"><li><a href="#">Origins SS26</a></li><li><a href="#">Void Series</a></li><li><a href="#">Terra</a></li><li><a href="#">Raw Work</a></li><li><a href="#">Kanto Limited</a></li><li><a href="#">VIVET Classic</a></li></ul>
    </div>
    <div>
      <div class="f-col-title">Programmi</div>
      <ul class="f-links"><li><a href="#">Custom Program</a></li><li><a href="#">Monthly Competition</a></li><li><a href="#">VIVET Rewards</a></li><li><a href="#">Processo Creativo</a></li><li><a href="#">Sostenibilità</a></li></ul>
    </div>
    <div>
      <div class="f-col-title">Aiuto</div>
      <ul class="f-links"><li><a href="#">📍 Via Torino 12, Milano</a></li><li><a href="#">📍 Via del Corso 88, Roma</a></li><li><a href="#">📍 Via Roma 45, Torino</a></li><li><a href="#">Spedizioni & Resi</a></li><li><a href="#">FAQ Custom</a></li><li><a href="#">Contattaci</a></li></ul>
    </div>
  </div>
  <div class="demo-warning">
    <div class="demo-w-txt">⚠️ PROGETTO DEMO — Se ti piace l'idea e vuoi aiutarci a trasformarlo in una vera azienda, scrivici su Instagram: 📸 @shubh._.y · 📸 @psng568</div>
  </div>
  <div class="footer-bottom">
    <div class="f-copy">© 2024 VIVET — Progetto Demo — @vivet.official</div>
    <div class="f-socials"><a href="#">Instagram</a><a href="#">TikTok</a><a href="#">Pinterest</a></div>
  </div>
</footer>

<script>
const cur=document.getElementById('cur'),ring=document.getElementById('cur-ring');
let mx=0,my=0,rx=0,ry=0;
document.addEventListener('mousemove',e=>{mx=e.clientX;my=e.clientY;cur.style.transform=`translate(${mx-5}px,${my-5}px)`;});
(function loop(){rx+=(mx-rx-16)*.13;ry+=(my-ry-16)*.13;ring.style.transform=`translate(${rx}px,${ry}px)`;requestAnimationFrame(loop);})();
document.querySelectorAll('a,button').forEach(el=>{
  el.addEventListener('mouseenter',()=>{ring.style.width='48px';ring.style.height='48px';});
  el.addEventListener('mouseleave',()=>{ring.style.width='32px';ring.style.height='32px';});
});
const obs=new IntersectionObserver(e=>{e.forEach(x=>{if(x.isIntersecting)x.target.classList.add('visible');});},{threshold:.08});
document.querySelectorAll('.reveal').forEach(el=>obs.observe(el));
function updateTimer(){
  const now=new Date(),end=new Date(now.getFullYear(),now.getMonth()+1,0);
  const d=Math.ceil((end-now)/864e5);
  const el=document.getElementById('timer-num');if(el)el.textContent=d;
}
updateTimer();
</script>
</body>
</html>
