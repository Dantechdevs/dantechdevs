<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width,initial-scale=1.0"/>
<title>Daniel Ngwasi · Developer Portfolio</title>
<link href="https://fonts.googleapis.com/css2?family=Bebas+Neue&family=DM+Sans:ital,opsz,wght@0,9..40,300;0,9..40,400;0,9..40,500;0,9..40,700;1,9..40,300&family=DM+Mono:wght@400;500&display=swap" rel="stylesheet"/>
<style>
*,*::before,*::after{box-sizing:border-box;margin:0;padding:0}
:root{
  --ink:    #050608;
  --ink2:   #0b0d12;
  --card:   #0f1117;
  --card2:  #13161f;
  --line:   #1c2030;
  --line2:  #252a3a;
  --lime:   #c8f135;
  --lime2:  #a8d420;
  --white:  #f0f2f7;
  --grey:   #6b7591;
  --dim:    #353d54;
  --red:    #ff4d6d;
  --blue:   #4d9fff;
  --amber:  #ffb830;
}
html{scroll-behavior:smooth}
body{
  background:var(--ink);
  color:var(--white);
  font-family:'DM Sans',sans-serif;
  overflow-x:hidden;
  cursor:none;
}
::-webkit-scrollbar{width:3px}
::-webkit-scrollbar-track{background:var(--ink)}
::-webkit-scrollbar-thumb{background:var(--lime);border-radius:2px}

/* CURSOR */
#c1,#c2{position:fixed;border-radius:50%;pointer-events:none;z-index:9999;will-change:transform}
#c1{width:6px;height:6px;background:var(--lime);margin:-3px 0 0 -3px;box-shadow:0 0 12px var(--lime),0 0 24px var(--lime)}
#c2{width:28px;height:28px;border:1.5px solid rgba(200,241,53,.35);margin:-14px 0 0 -14px;transition:width .18s,height .18s,border-color .18s,margin .18s}

/* NOISE TEXTURE */
body::before{
  content:'';position:fixed;inset:0;
  background-image:url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='0.035'/%3E%3C/svg%3E");
  pointer-events:none;z-index:0;opacity:.6;
}

/* LAYOUT */
.wrap{position:relative;z-index:1;max-width:920px;margin:0 auto;padding:0 28px 120px}

/* ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
   HERO
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ */
.hero{
  min-height:100svh;
  display:grid;
  grid-template-rows:1fr auto;
  padding-top:80px;
  position:relative;
}

.hero-top{
  display:flex;
  flex-direction:column;
  justify-content:center;
  gap:0;
}

/* BIG NUMBER bg */
.hero-num{
  font-family:'Bebas Neue',sans-serif;
  font-size:clamp(200px,28vw,380px);
  line-height:.82;
  color:transparent;
  -webkit-text-stroke:1px rgba(200,241,53,.06);
  user-select:none;
  position:absolute;
  top:50%;left:-20px;
  transform:translateY(-54%);
  pointer-events:none;
  letter-spacing:-4px;
}

.hero-eyebrow{
  font-family:'DM Mono',monospace;
  font-size:11px;letter-spacing:4px;
  text-transform:uppercase;
  color:var(--lime);
  margin-bottom:20px;
  display:flex;align-items:center;gap:10px;
  opacity:0;animation:up .7s ease .1s both;
}
.hero-eyebrow i{display:block;width:24px;height:1px;background:var(--lime);box-shadow:0 0 6px var(--lime)}

.hero-name{
  font-family:'Bebas Neue',sans-serif;
  font-size:clamp(72px,12vw,160px);
  line-height:.9;
  letter-spacing:-1px;
  color:var(--white);
  margin-bottom:28px;
  opacity:0;animation:up .8s ease .2s both;
}
.hero-name em{
  color:var(--lime);
  font-style:normal;
  display:block;
  -webkit-text-stroke:0;
}

.hero-bio{
  max-width:500px;
  font-size:16px;
  line-height:1.75;
  color:var(--grey);
  margin-bottom:40px;
  font-weight:300;
  opacity:0;animation:up .8s ease .35s both;
}
.hero-bio strong{color:var(--white);font-weight:500}

.hero-pills{
  display:flex;flex-wrap:wrap;gap:8px;
  margin-bottom:44px;
  opacity:0;animation:up .8s ease .45s both;
}
.pill{
  font-family:'DM Mono',monospace;
  font-size:11px;letter-spacing:1px;
  padding:7px 16px;border-radius:100px;
  border:1px solid var(--line2);
  color:var(--grey);background:var(--card);
  transition:all .2s;cursor:default;
}
.pill:hover{border-color:var(--lime);color:var(--lime);background:rgba(200,241,53,.06)}
.pill.active{border-color:var(--lime);color:var(--lime);background:rgba(200,241,53,.08)}

.hero-cta{
  display:flex;gap:12px;flex-wrap:wrap;
  opacity:0;animation:up .8s ease .55s both;
}
.btn-a{
  display:inline-flex;align-items:center;gap:9px;
  padding:14px 30px;border-radius:10px;
  background:var(--lime);color:var(--ink);
  font-size:14px;font-weight:700;
  text-decoration:none;
  transition:all .2s;
  box-shadow:0 0 40px rgba(200,241,53,.25);
}
.btn-a:hover{background:var(--lime2);transform:translateY(-2px);box-shadow:0 0 60px rgba(200,241,53,.4)}
.btn-b{
  display:inline-flex;align-items:center;gap:9px;
  padding:13px 28px;border-radius:10px;
  border:1px solid var(--line2);
  color:var(--white);font-size:14px;font-weight:500;
  text-decoration:none;
  transition:all .2s;background:transparent;
}
.btn-b:hover{border-color:var(--line2);background:var(--card);transform:translateY(-2px)}

/* floating gif */
.hero-img{
  position:absolute;right:0;top:50%;transform:translateY(-50%);
  width:200px;
  opacity:0;animation:fadeRight .9s ease .6s both;
}
.hero-img img{
  width:100%;border-radius:24px;
  border:1px solid var(--line2);
  box-shadow:0 30px 80px rgba(0,0,0,.6),0 0 0 1px rgba(200,241,53,.05);
  filter:saturate(1.1);
}
@media(max-width:700px){.hero-img,.hero-num{display:none}}

/* bottom bar */
.hero-bar{
  display:flex;align-items:center;justify-content:space-between;
  padding:20px 0;
  border-top:1px solid var(--line);
  opacity:0;animation:up .6s ease .8s both;
  flex-wrap:wrap;gap:12px;
}
.hero-bar-item{
  font-family:'DM Mono',monospace;
  font-size:10px;letter-spacing:3px;
  text-transform:uppercase;color:var(--dim);
}
.hero-bar-item span{color:var(--grey)}
.hero-bar-item.live{color:var(--lime)}
.hero-bar-item.live::before{
  content:'';display:inline-block;
  width:6px;height:6px;border-radius:50%;
  background:var(--lime);margin-right:6px;
  animation:blink 2s ease-in-out infinite;
  box-shadow:0 0 6px var(--lime);
}

/* ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
   SECTION CHROME
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ */
.sec{
  margin:100px 0;
  opacity:0;transform:translateY(32px);
  transition:opacity .65s ease,transform .65s ease;
}
.sec.on{opacity:1;transform:none}

.sec-head{
  display:flex;align-items:flex-end;justify-content:space-between;
  margin-bottom:36px;
  padding-bottom:20px;
  border-bottom:1px solid var(--line);
  gap:16px;flex-wrap:wrap;
}
.sec-left{display:flex;flex-direction:column;gap:6px}
.sec-num{
  font-family:'DM Mono',monospace;
  font-size:10px;letter-spacing:4px;
  color:var(--dim);text-transform:uppercase;
}
.sec-title{
  font-family:'Bebas Neue',sans-serif;
  font-size:clamp(36px,5vw,56px);
  letter-spacing:1px;
  color:var(--white);
  line-height:1;
}
.sec-title span{color:var(--lime)}

/* ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
   ABOUT
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ */
.about-layout{
  display:grid;
  grid-template-columns:1fr 1fr;
  gap:16px;
}
@media(max-width:640px){.about-layout{grid-template-columns:1fr}}

.about-main{
  grid-column:1/-1;
  background:var(--card);
  border:1px solid var(--line);
  border-radius:20px;
  padding:36px;
  position:relative;overflow:hidden;
}
.about-main::after{
  content:'';position:absolute;
  top:0;left:0;right:0;height:2px;
  background:linear-gradient(90deg,var(--lime),var(--lime2),transparent);
}
.about-main p{
  font-size:15.5px;line-height:1.85;color:var(--grey);
  font-weight:300;margin-bottom:14px;
}
.about-main p:last-child{margin-bottom:0}
.about-main p strong{color:var(--white);font-weight:500}

.about-list{
  list-style:none;
  margin-top:28px;padding-top:24px;
  border-top:1px solid var(--line);
  display:grid;grid-template-columns:1fr 1fr;gap:4px;
}
@media(max-width:520px){.about-list{grid-template-columns:1fr}}
.about-list li{
  display:flex;align-items:center;gap:10px;
  padding:10px 12px;border-radius:10px;
  font-size:13.5px;color:var(--grey);
  transition:background .2s,color .2s;
}
.about-list li:hover{background:var(--card2);color:var(--white)}
.about-list li .ic{font-size:16px;flex-shrink:0}
.about-list a{color:var(--lime);text-decoration:none}
.about-list a:hover{text-decoration:underline}

/* stat cards */
.stat-card{
  background:var(--card);border:1px solid var(--line);
  border-radius:20px;padding:28px;
  display:flex;flex-direction:column;justify-content:space-between;
  min-height:130px;
  transition:border-color .25s,transform .25s;
  position:relative;overflow:hidden;
}
.stat-card:hover{border-color:var(--line2);transform:translateY(-3px)}
.stat-card-label{
  font-family:'DM Mono',monospace;
  font-size:9px;letter-spacing:3px;text-transform:uppercase;
  color:var(--dim);margin-bottom:14px;
}
.stat-card-val{
  font-family:'Bebas Neue',sans-serif;
  font-size:38px;letter-spacing:1px;color:var(--lime);
  line-height:1;
}
.stat-card-sub{font-size:12px;color:var(--grey);margin-top:4px;font-weight:300}
.stat-card.green .stat-card-val{color:var(--lime)}
.stat-card-dot{
  position:absolute;top:20px;right:20px;
  width:8px;height:8px;border-radius:50%;
  background:var(--lime);
  animation:blink 2s ease-in-out infinite;
  box-shadow:0 0 8px var(--lime);
}

/* ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
   SOCIALS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ */
.social-grid{
  display:grid;
  grid-template-columns:repeat(3,1fr);
  gap:12px;
}
@media(max-width:600px){.social-grid{grid-template-columns:1fr 1fr}}
@media(max-width:380px){.social-grid{grid-template-columns:1fr}}

.soc{
  display:flex;align-items:center;gap:14px;
  padding:18px 20px;
  background:var(--card);border:1px solid var(--line);border-radius:16px;
  text-decoration:none;color:var(--white);
  transition:all .22s;
  position:relative;overflow:hidden;
}
.soc::before{
  content:'';position:absolute;inset:0;
  background:var(--hov,transparent);
  opacity:0;transition:opacity .22s;border-radius:16px;
}
.soc:hover{transform:translateY(-3px)}
.soc:hover::before{opacity:1}
.soc:hover .soc-name{color:var(--hov-c,var(--white))}
.soc.fb{--hov:rgba(24,119,242,.07);--hov-c:#1877F2}
.soc.li{--hov:rgba(0,119,181,.07);--hov-c:#0077B5}
.soc.tw{--hov:rgba(29,161,242,.07);--hov-c:#1DA1F2}
.soc.gm{--hov:rgba(234,67,53,.07);--hov-c:#EA4335}
.soc.wa{--hov:rgba(37,211,102,.07);--hov-c:#25D366}
.soc.sp{--hov:rgba(200,241,53,.07);--hov-c:var(--lime)}
.soc:hover{border-color:var(--hov-c,var(--line2))}

.soc-ico{
  width:40px;height:40px;border-radius:12px;
  background:var(--card2);border:1px solid var(--line);
  display:flex;align-items:center;justify-content:center;
  flex-shrink:0;font-size:19px;
  transition:border-color .2s;
  position:relative;z-index:1;
}
.soc-txt{position:relative;z-index:1}
.soc-name{font-size:14px;font-weight:600;transition:color .2s}
.soc-handle{font-family:'DM Mono',monospace;font-size:10px;color:var(--dim);margin-top:2px}

/* ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
   TECH STACK
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ */
.stack-groups{display:flex;flex-direction:column;gap:20px}

.sg{
  background:var(--card);border:1px solid var(--line);
  border-radius:16px;padding:22px 24px;
  transition:border-color .2s;
}
.sg:hover{border-color:var(--line2)}

.sg-label{
  font-family:'DM Mono',monospace;
  font-size:9px;letter-spacing:4px;text-transform:uppercase;
  color:var(--dim);margin-bottom:14px;
  display:flex;align-items:center;gap:10px;
}
.sg-label::after{content:'';flex:1;height:1px;background:var(--line)}

.chips{display:flex;flex-wrap:wrap;gap:7px}
.chip{
  display:inline-flex;align-items:center;gap:7px;
  padding:7px 14px;border-radius:8px;
  font-family:'DM Mono',monospace;
  font-size:12px;letter-spacing:.3px;
  background:var(--card2);border:1px solid var(--line);
  color:var(--grey);
  transition:all .18s;cursor:default;
}
.chip:hover{border-color:var(--lime);color:var(--white);background:rgba(200,241,53,.05);transform:translateY(-2px)}
.cd{width:7px;height:7px;border-radius:50%;flex-shrink:0}

/* ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
   GITHUB STATS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ */
.stats-wrap{display:flex;flex-direction:column;gap:14px}
.stats-row{display:grid;grid-template-columns:1fr 1fr;gap:14px}
@media(max-width:560px){.stats-row{grid-template-columns:1fr}}

.gh-card{
  background:var(--card);border:1px solid var(--line);
  border-radius:16px;overflow:hidden;
  transition:border-color .22s,transform .22s;
}
.gh-card:hover{border-color:var(--line2);transform:translateY(-2px)}
.gh-card img{width:100%;display:block}
.gh-card.full{grid-column:1/-1}

/* ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
   QUOTE
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ */
.quote-card{
  background:var(--card);border:1px solid var(--line);
  border-radius:20px;overflow:hidden;
  position:relative;
  transition:border-color .2s;
}
.quote-card:hover{border-color:var(--line2)}
.quote-card::before{
  content:'\201C';
  position:absolute;top:-16px;left:24px;
  font-family:'Bebas Neue',sans-serif;
  font-size:140px;color:var(--line);
  line-height:1;pointer-events:none;
}
.quote-card img{width:100%;display:block;position:relative;z-index:1}

/* ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
   TROPHY
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ */
.trophy-card{
  background:var(--card);border:1px solid var(--line);
  border-radius:16px;overflow:hidden;padding:8px;
  transition:border-color .2s;
}
.trophy-card:hover{border-color:var(--line2)}
.trophy-card img{width:100%;display:block;border-radius:10px}

/* ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
   README BOX
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ */
.readme-wrap{
  background:var(--card);border:1px solid var(--line);
  border-radius:20px;overflow:hidden;
}
.readme-bar{
  display:flex;align-items:center;justify-content:space-between;
  padding:14px 20px;
  background:var(--card2);
  border-bottom:1px solid var(--line);
}
.readme-dots{display:flex;gap:6px}
.rdt{width:12px;height:12px;border-radius:50%}
.readme-file{
  font-family:'DM Mono',monospace;
  font-size:11px;color:var(--dim);letter-spacing:.5px;
  margin-left:10px;
}
.copy-btn{
  font-family:'DM Mono',monospace;
  font-size:11px;font-weight:500;letter-spacing:1px;
  padding:8px 18px;border-radius:8px;
  border:1px solid var(--line2);
  background:transparent;color:var(--lime);
  cursor:pointer;transition:all .2s;
}
.copy-btn:hover{background:var(--lime);color:var(--ink);border-color:var(--lime)}

.readme-pre{
  padding:28px;
  font-family:'DM Mono',monospace;
  font-size:11.5px;line-height:1.9;
  color:var(--grey);
  max-height:480px;
  overflow-y:auto;
  overflow-x:auto;
  white-space:pre-wrap;
  word-break:break-word;
}
.readme-pre::-webkit-scrollbar{width:3px;height:3px}
.readme-pre::-webkit-scrollbar-thumb{background:var(--line2);border-radius:2px}

.toast{
  position:fixed;bottom:36px;left:50%;
  transform:translateX(-50%) translateY(16px);
  background:var(--lime);color:var(--ink);
  font-family:'DM Mono',monospace;font-size:12px;font-weight:700;letter-spacing:1px;
  padding:12px 28px;border-radius:100px;
  opacity:0;transition:all .3s;pointer-events:none;z-index:9997;
  box-shadow:0 8px 40px rgba(200,241,53,.4);
}
.toast.show{opacity:1;transform:translateX(-50%) translateY(0)}

/* ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
   FOOTER
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ */
.foot{
  border-top:1px solid var(--line);
  padding:36px 0 0;
  display:flex;align-items:center;justify-content:space-between;
  flex-wrap:wrap;gap:16px;
}
.foot-left{font-size:13px;color:var(--dim);font-weight:300}
.foot-left a{color:var(--lime);text-decoration:none}
.foot-views img{border-radius:8px}

/* ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
   ANIMATIONS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ */
@keyframes up{from{opacity:0;transform:translateY(22px)}to{opacity:1;transform:none}}
@keyframes fadeRight{from{opacity:0;transform:translate(24px,-50%)}to{opacity:1;transform:translate(0,-50%)}}
@keyframes blink{0%,100%{opacity:1}50%{opacity:.3}}
</style>
</head>
<body>

<div id="c1"></div>
<div id="c2"></div>

<div class="wrap">

  <!-- ══ HERO ══ -->
  <section class="hero">
    <div class="hero-num">DN</div>

    <div class="hero-top">
      <div class="hero-eyebrow"><i></i>Kenya · Nairobi · Open to Work</div>

      <h1 class="hero-name">
        Daniel<em>Ngwasi</em>
      </h1>

      <p class="hero-bio">
        Passionate self-taught <strong>full-stack developer</strong> &amp; <strong>freelance web designer</strong> from 🇰🇪 Kenya. I dream up ideas and bring them to life with elegant interfaces — obsessing over every detail of experience, architecture, and code quality.
      </p>

      <div class="hero-pills">
        <span class="pill active">Full-Stack Dev</span>
        <span class="pill">Freelance Designer</span>
        <span class="pill">Open Source</span>
        <span class="pill">React · Django · Laravel</span>
        <span class="pill">AI/ML Enthusiast</span>
      </div>

      <div class="hero-cta">
        <a class="btn-a" href="mailto:dantechdevs@gmail.com">📧 Get in Touch</a>
        <a class="btn-b" href="https://github.com/Dantechdevs" target="_blank">GitHub ↗</a>
        <a class="btn-b" href="https://github.com/sponsors/Dantechdevs" target="_blank">❤️ Sponsor</a>
      </div>
    </div>

    <div class="hero-img">
      <img src="https://media.giphy.com/media/xT9IgG50Fb7Mi0prBC/giphy.gif" alt="coding"/>
    </div>

    <div class="hero-bar">
      <span class="hero-bar-item live">Available for hire</span>
      <span class="hero-bar-item">📫 <span>dantechdevs@gmail.com</span></span>
      <span class="hero-bar-item">📱 <span>+254712328150</span></span>
      <span class="hero-bar-item">⏰ <span>EAT · UTC+3</span></span>
    </div>
  </section>


  <!-- ══ ABOUT ══ -->
  <section class="sec">
    <div class="sec-head">
      <div class="sec-left">
        <span class="sec-num">01 — About</span>
        <h2 class="sec-title">💫 About <span>Me</span></h2>
      </div>
    </div>

    <div class="about-layout">
      <div class="about-main">
        <p>Hi, I'm <strong>Daniel Ngwasi</strong> — a passionate self-taught <strong>full-stack web developer</strong> and <strong>freelance web designer</strong> from 🇰🇪 Kenya.</p>
        <p>My passion for software lies in dreaming up ideas and bringing them to life with <strong>elegant interfaces</strong>. I take great care in the experience, architecture, and code quality of the things I build.</p>
        <p>I'm also an <strong>open-source enthusiast and maintainer</strong>. I've learned a lot from the open-source community, and I really enjoy the <strong>collaboration and knowledge sharing</strong> that happens through open-source.</p>
        <ul class="about-list">
          <li><span class="ic">💬</span> Ask me about code, food, space crafts, and life</li>
          <li><span class="ic">📫</span> <a href="mailto:dantechdevs@gmail.com">dantechdevs@gmail.com</a></li>
          <li><span class="ic">📱</span> <a href="https://wa.me/254712328150">WhatsApp: +254712328150</a></li>
          <li><span class="ic">❤️</span> <a href="https://github.com/sponsors/Dantechdevs">Sponsor my open source work</a></li>
        </ul>
      </div>

      <div class="stat-card green">
        <div class="stat-card-dot"></div>
        <div class="stat-card-label">Status</div>
        <div class="stat-card-val">Open</div>
        <div class="stat-card-sub">Available for freelance &amp; collaboration</div>
      </div>

      <div class="stat-card">
        <div class="stat-card-label">Location</div>
        <div class="stat-card-val" style="font-size:28px">🇰🇪</div>
        <div class="stat-card-sub">Nairobi, Kenya · EAT UTC+3</div>
      </div>

      <div class="stat-card">
        <div class="stat-card-label">Current Focus</div>
        <div class="stat-card-val" style="font-size:26px;color:var(--white)">AI Apps</div>
        <div class="stat-card-sub">Full-stack + AI integration</div>
      </div>
    </div>
  </section>


  <!-- ══ SOCIALS ══ -->
  <section class="sec">
    <div class="sec-head">
      <div class="sec-left">
        <span class="sec-num">02 — Connect</span>
        <h2 class="sec-title">🌐 <span>Socials</span></h2>
      </div>
    </div>
    <div class="social-grid">
      <a class="soc fb" href="https://web.facebook.com/daniel.ngwasi.9/" target="_blank">
        <div class="soc-ico"><svg width="20" height="20" viewBox="0 0 24 24" fill="#1877F2"><path d="M24 12.073c0-6.627-5.373-12-12-12s-12 5.373-12 12c0 5.99 4.388 10.954 10.125 11.854v-8.385H7.078v-3.47h3.047V9.43c0-3.007 1.792-4.669 4.533-4.669 1.312 0 2.686.235 2.686.235v2.953H15.83c-1.491 0-1.956.925-1.956 1.874v2.25h3.328l-.532 3.47h-2.796v8.385C19.612 23.027 24 18.062 24 12.073z"/></svg></div>
        <div class="soc-txt"><div class="soc-name">Facebook</div><div class="soc-handle">daniel.ngwasi.9</div></div>
      </a>
      <a class="soc li" href="https://www.linkedin.com/in/daniel-n-29924a69/" target="_blank">
        <div class="soc-ico"><svg width="20" height="20" viewBox="0 0 24 24" fill="#0077B5"><path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433c-1.144 0-2.063-.926-2.063-2.065 0-1.138.92-2.063 2.063-2.063 1.14 0 2.064.925 2.064 2.063 0 1.139-.925 2.065-2.064 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/></svg></div>
        <div class="soc-txt"><div class="soc-name">LinkedIn</div><div class="soc-handle">daniel-n-29924a69</div></div>
      </a>
      <a class="soc tw" href="https://twitter.com/Ngwasidaniel" target="_blank">
        <div class="soc-ico"><svg width="20" height="20" viewBox="0 0 24 24" fill="#1DA1F2"><path d="M23.953 4.57a10 10 0 01-2.825.775 4.958 4.958 0 002.163-2.723c-.951.555-2.005.959-3.127 1.184a4.92 4.92 0 00-8.384 4.482C7.69 8.095 4.067 6.13 1.64 3.162a4.822 4.822 0 00-.666 2.475c0 1.71.87 3.213 2.188 4.096a4.904 4.904 0 01-2.228-.616v.06a4.923 4.923 0 003.946 4.827 4.996 4.996 0 01-2.212.085 4.936 4.936 0 004.604 3.417 9.867 9.867 0 01-6.102 2.105c-.39 0-.779-.023-1.17-.067a13.995 13.995 0 007.557 2.209c9.053 0 13.998-7.496 13.998-13.985 0-.21 0-.42-.015-.63A9.935 9.935 0 0024 4.59z"/></svg></div>
        <div class="soc-txt"><div class="soc-name">Twitter / X</div><div class="soc-handle">@Ngwasidaniel</div></div>
      </a>
      <a class="soc gm" href="mailto:dantechdevs@gmail.com">
        <div class="soc-ico"><svg width="20" height="20" viewBox="0 0 24 24" fill="#EA4335"><path d="M24 5.457v13.909c0 .904-.732 1.636-1.636 1.636h-3.819V11.73L12 16.64l-6.545-4.91v9.273H1.636A1.636 1.636 0 010 19.366V5.457c0-2.023 2.309-3.178 3.927-1.964L5.455 4.64 12 9.548l6.545-4.91 1.528-1.145C21.69 2.28 24 3.434 24 5.457z"/></svg></div>
        <div class="soc-txt"><div class="soc-name">Gmail</div><div class="soc-handle">dantechdevs@gmail.com</div></div>
      </a>
      <a class="soc wa" href="https://wa.me/254712328150" target="_blank">
        <div class="soc-ico"><svg width="20" height="20" viewBox="0 0 24 24" fill="#25D366"><path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347m-5.421 7.403h-.004a9.87 9.87 0 01-5.031-1.378l-.361-.214-3.741.982.998-3.648-.235-.374a9.86 9.86 0 01-1.51-5.26c.001-5.45 4.436-9.884 9.888-9.884 2.64 0 5.122 1.03 6.988 2.898a9.825 9.825 0 012.893 6.994c-.003 5.45-4.437 9.884-9.885 9.884m8.413-18.297A11.815 11.815 0 0012.05 0C5.495 0 .16 5.335.157 11.892c0 2.096.547 4.142 1.588 5.945L.057 24l6.305-1.654a11.882 11.882 0 005.683 1.448h.005c6.554 0 11.89-5.335 11.893-11.893a11.821 11.821 0 00-3.48-8.413z"/></svg></div>
        <div class="soc-txt"><div class="soc-name">WhatsApp</div><div class="soc-handle">+254712328150</div></div>
      </a>
      <a class="soc sp" href="https://github.com/sponsors/Dantechdevs" target="_blank">
        <div class="soc-ico">❤️</div>
        <div class="soc-txt"><div class="soc-name" style="color:var(--lime)">Sponsor</div><div class="soc-handle">Dantechdevs</div></div>
      </a>
    </div>
  </section>


  <!-- ══ TECH STACK ══ -->
  <section class="sec">
    <div class="sec-head">
      <div class="sec-left">
        <span class="sec-num">03 — Arsenal</span>
        <h2 class="sec-title">💻 Tech <span>Stack</span></h2>
      </div>
    </div>
    <div class="stack-groups">
      <div class="sg">
        <div class="sg-label">Languages</div>
        <div class="chips">
          <span class="chip"><span class="cd" style="background:#F7DF1E"></span>JavaScript</span>
          <span class="chip"><span class="cd" style="background:#3178C6"></span>TypeScript</span>
          <span class="chip"><span class="cd" style="background:#3776AB"></span>Python</span>
          <span class="chip"><span class="cd" style="background:#777BB4"></span>PHP</span>
          <span class="chip"><span class="cd" style="background:#239120"></span>C#</span>
          <span class="chip"><span class="cd" style="background:#00599C"></span>C++</span>
          <span class="chip"><span class="cd" style="background:#6e6e6e"></span>C</span>
          <span class="chip"><span class="cd" style="background:#E34F26"></span>HTML5</span>
          <span class="chip"><span class="cd" style="background:#1572B6"></span>CSS3</span>
        </div>
      </div>
      <div class="sg">
        <div class="sg-label">Frontend</div>
        <div class="chips">
          <span class="chip"><span class="cd" style="background:#61DAFB"></span>React</span>
          <span class="chip"><span class="cd" style="background:#61DAFB"></span>React Native</span>
          <span class="chip"><span class="cd" style="background:#eeeeee"></span>Next.js</span>
          <span class="chip"><span class="cd" style="background:#38BDF8"></span>TailwindCSS</span>
        </div>
      </div>
      <div class="sg">
        <div class="sg-label">Backend & Frameworks</div>
        <div class="chips">
          <span class="chip"><span class="cd" style="background:#092E20"></span>Django</span>
          <span class="chip"><span class="cd" style="background:#FF2D20"></span>Laravel</span>
          <span class="chip"><span class="cd" style="background:#6DA55F"></span>Node.js</span>
          <span class="chip"><span class="cd" style="background:#D42029"></span>Apache</span>
        </div>
      </div>
      <div class="sg">
        <div class="sg-label">Databases & Cloud</div>
        <div class="chips">
          <span class="chip"><span class="cd" style="background:#4479A1"></span>MySQL</span>
          <span class="chip"><span class="cd" style="background:#CC2927"></span>SQL Server</span>
          <span class="chip"><span class="cd" style="background:#47A248"></span>MongoDB</span>
          <span class="chip"><span class="cd" style="background:#4285F4"></span>Google Cloud</span>
          <span class="chip"><span class="cd" style="background:#0db7ed"></span>Docker</span>
        </div>
      </div>
      <div class="sg">
        <div class="sg-label">Data Science & AI / ML</div>
        <div class="chips">
          <span class="chip"><span class="cd" style="background:#EE4C2C"></span>PyTorch</span>
          <span class="chip"><span class="cd" style="background:#150458"></span>Pandas</span>
          <span class="chip"><span class="cd" style="background:#013243"></span>NumPy</span>
          <span class="chip"><span class="cd" style="background:#3F4F75"></span>Plotly</span>
        </div>
      </div>
    </div>
  </section>


  <!-- ══ GITHUB STATS ══ -->
  <section class="sec">
    <div class="sec-head">
      <div class="sec-left">
        <span class="sec-num">04 — Activity</span>
        <h2 class="sec-title">📊 GitHub <span>Stats</span></h2>
      </div>
    </div>
    <div class="stats-wrap">
      <div class="stats-row">
        <div class="gh-card">
          <img src="https://github-readme-stats.vercel.app/api?username=Dantechdevs&show_icons=true&theme=github_dark&include_all_commits=true&count_private=true&hide_border=true&bg_color=0f1117&title_color=c8f135&icon_color=c8f135&text_color=6b7591&ring_color=c8f135" alt="GitHub Stats"/>
        </div>
        <div class="gh-card">
          <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=Dantechdevs&layout=compact&langs_count=8&theme=github_dark&hide_border=true&bg_color=0f1117&title_color=c8f135&text_color=6b7591" alt="Top Languages"/>
        </div>
      </div>
      <div class="gh-card full">
        <img src="https://streak-stats.demolab.com/?user=Dantechdevs&theme=dark&hide_border=true&background=0f1117&ring=c8f135&fire=ff4d6d&currStreakLabel=c8f135&sideLabels=6b7591&dates=6b7591&stroke=1c2030" alt="GitHub Streak"/>
      </div>
      <div class="gh-card full">
        <img src="https://github-readme-activity-graph.vercel.app/graph?username=Dantechdevs&bg_color=0f1117&color=c8f135&line=c8f135&point=ffffff&area=true&hide_border=true&custom_title=Contribution%20Timeline" alt="Activity Graph"/>
      </div>
    </div>
  </section>


  <!-- ══ TROPHIES ══ -->
  <section class="sec">
    <div class="sec-head">
      <div class="sec-left">
        <span class="sec-num">05 — Achievements</span>
        <h2 class="sec-title">🏆 <span>Trophies</span></h2>
      </div>
    </div>
    <div class="trophy-card">
      <img src="https://github-profile-trophy.vercel.app/?username=Dantechdevs&theme=darkhub&no-frame=true&no-bg=true&margin-w=6" alt="GitHub Trophies"/>
    </div>
  </section>


  <!-- ══ QUOTE ══ -->
  <section class="sec">
    <div class="sec-head">
      <div class="sec-left">
        <span class="sec-num">06 — Inspiration</span>
        <h2 class="sec-title">✍️ Dev <span>Quote</span></h2>
      </div>
    </div>
    <div class="quote-card">
      <img src="https://quotes-github-readme.vercel.app/api?type=horizontal&theme=dark" alt="Dev Quote"/>
    </div>
  </section>


  <!-- ══ README SOURCE ══ -->
  <section class="sec">
    <div class="sec-head">
      <div class="sec-left">
        <span class="sec-num">07 — GitHub Ready</span>
        <h2 class="sec-title">📄 README <span>Source</span></h2>
      </div>
    </div>
    <div class="readme-wrap">
      <div class="readme-bar">
        <div style="display:flex;align-items:center">
          <div class="readme-dots">
            <span class="rdt" style="background:#ff5f57"></span>
            <span class="rdt" style="background:#ffbd2e"></span>
            <span class="rdt" style="background:#28c840"></span>
          </div>
          <span class="readme-file">README.md — Dantechdevs/Dantechdevs</span>
        </div>
        <button class="copy-btn" onclick="copyMe()">📋 Copy All</button>
      </div>
      <pre class="readme-pre" id="rme">&lt;img src="https://capsule-render.vercel.app/api?type=waving&amp;color=gradient&amp;customColorList=12,14,20,24,30&amp;height=220&amp;section=header&amp;text=Hi%20there%2C%20I'm%20Daniel%20Ngwasi%20%F0%9F%91%8B&amp;fontSize=36&amp;fontColor=ffffff&amp;animation=twinkling&amp;fontAlignY=38&amp;desc=Full-Stack%20Developer%20%7C%20Freelance%20Designer%20%7C%20Open%20Source%20Enthusiast%20%F0%9F%87%B0%F0%9F%87%AA&amp;descSize=15&amp;descAlignY=58&amp;descColor=a8d8ea" width="100%"/&gt;

&lt;div align="center"&gt;

[![Typing SVG](https://readme-typing-svg.demolab.com?font=Fira+Code&amp;weight=600&amp;size=20&amp;pause=1200&amp;color=58A6FF&amp;center=true&amp;vCenter=true&amp;width=680&amp;lines=Dreaming+up+ideas+and+bringing+them+to+life+%E2%9C%A8;Self-taught+%7C+Passionate+%7C+Nairobi-based+%F0%9F%87%B0%F0%9F%87%AA;Open+source+enthusiast+%26+maintainer+%F0%9F%8C%8D;Clean+code+%7C+Elegant+interfaces+%7C+Great+UX)](https://git.io/typing-svg)

&lt;/div&gt;

---

## 💫 About Me

&lt;img align="right" width="280" src="https://media.giphy.com/media/xT9IgG50Fb7Mi0prBC/giphy.gif"/&gt;

Hi, I'm **Daniel Ngwasi** — a passionate self-taught **full-stack web developer** and **freelance web designer** from 🇰🇪 Kenya.

My passion for software lies in **dreaming up ideas** and bringing them to life with **elegant interfaces**. I take great care in the experience, architecture, and code quality of the things I build.

I'm also an **open-source enthusiast and maintainer**. I've learned a lot from the open-source community, and I really enjoy the **collaboration and knowledge sharing** that happens through open-source.

- 💬 Ask me about **code, food, space crafts, and life**
- 📫 Reach me at **dantechdevs@gmail.com**
- 📱 WhatsApp: **+254712328150**
- ❤️ [Sponsor my work](https://github.com/sponsors/Dantechdevs)

&lt;br clear="right"/&gt;

---

## 🌐 Socials

&lt;div align="center"&gt;

[![Facebook](https://img.shields.io/badge/Facebook-%231877F2.svg?style=for-the-badge&amp;logo=Facebook&amp;logoColor=white)](https://web.facebook.com/daniel.ngwasi.9/)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-%230077B5.svg?style=for-the-badge&amp;logo=linkedin&amp;logoColor=white)](https://www.linkedin.com/in/daniel-n-29924a69/)
[![Twitter](https://img.shields.io/badge/Twitter-%231DA1F2.svg?style=for-the-badge&amp;logo=Twitter&amp;logoColor=white)](https://twitter.com/Ngwasidaniel)
[![Gmail](https://img.shields.io/badge/Gmail-D14836?style=for-the-badge&amp;logo=gmail&amp;logoColor=white)](mailto:dantechdevs@gmail.com)
[![WhatsApp](https://img.shields.io/badge/WhatsApp-25D366?style=for-the-badge&amp;logo=whatsapp&amp;logoColor=white)](https://wa.me/254712328150)

&lt;/div&gt;

---

## 💻 Tech Stack

### Languages
![JavaScript](https://img.shields.io/badge/javascript-%23323330.svg?style=for-the-badge&amp;logo=javascript&amp;logoColor=%23F7DF1E)
![TypeScript](https://img.shields.io/badge/typescript-%23007ACC.svg?style=for-the-badge&amp;logo=typescript&amp;logoColor=white)
![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&amp;logo=python&amp;logoColor=ffdd54)
![PHP](https://img.shields.io/badge/php-%23777BB4.svg?style=for-the-badge&amp;logo=php&amp;logoColor=white)
![C#](https://img.shields.io/badge/c%23-%23239120.svg?style=for-the-badge&amp;logo=c-sharp&amp;logoColor=white)
![C](https://img.shields.io/badge/c-%2300599C.svg?style=for-the-badge&amp;logo=c&amp;logoColor=white)
![C++](https://img.shields.io/badge/c++-%2300599C.svg?style=for-the-badge&amp;logo=c%2B%2B&amp;logoColor=white)
![HTML5](https://img.shields.io/badge/html5-%23E34F26.svg?style=for-the-badge&amp;logo=html5&amp;logoColor=white)
![CSS3](https://img.shields.io/badge/css3-%231572B6.svg?style=for-the-badge&amp;logo=css3&amp;logoColor=white)

### Frontend
![React](https://img.shields.io/badge/react-%2320232a.svg?style=for-the-badge&amp;logo=react&amp;logoColor=%2361DAFB)
![React Native](https://img.shields.io/badge/react_native-%2320232a.svg?style=for-the-badge&amp;logo=react&amp;logoColor=%2361DAFB)
![Next JS](https://img.shields.io/badge/Next-black?style=for-the-badge&amp;logo=next.js&amp;logoColor=white)
![TailwindCSS](https://img.shields.io/badge/tailwindcss-%2338B2AC.svg?style=for-the-badge&amp;logo=tailwind-css&amp;logoColor=white)

### Backend &amp; Frameworks
![Django](https://img.shields.io/badge/django-%23092E20.svg?style=for-the-badge&amp;logo=django&amp;logoColor=white)
![Laravel](https://img.shields.io/badge/laravel-%23FF2D20.svg?style=for-the-badge&amp;logo=laravel&amp;logoColor=white)
![NodeJS](https://img.shields.io/badge/node.js-6DA55F?style=for-the-badge&amp;logo=node.js&amp;logoColor=white)
![Apache](https://img.shields.io/badge/apache-%23D42029.svg?style=for-the-badge&amp;logo=apache&amp;logoColor=white)

### Databases &amp; Cloud
![MySQL](https://img.shields.io/badge/mysql-%2300f.svg?style=for-the-badge&amp;logo=mysql&amp;logoColor=white)
![MicrosoftSQLServer](https://img.shields.io/badge/Microsoft%20SQL%20Server-CC2927?style=for-the-badge&amp;logo=microsoft%20sql%20server&amp;logoColor=white)
![MongoDB](https://img.shields.io/badge/MongoDB-%234ea94b.svg?style=for-the-badge&amp;logo=mongodb&amp;logoColor=white)
![Google Cloud](https://img.shields.io/badge/GoogleCloud-%234285F4.svg?style=for-the-badge&amp;logo=google-cloud&amp;logoColor=white)
![Docker](https://img.shields.io/badge/docker-%230db7ed.svg?style=for-the-badge&amp;logo=docker&amp;logoColor=white)

### Data Science &amp; AI/ML
![Pandas](https://img.shields.io/badge/pandas-%23150458.svg?style=for-the-badge&amp;logo=pandas&amp;logoColor=white)
![NumPy](https://img.shields.io/badge/numpy-%23013243.svg?style=for-the-badge&amp;logo=numpy&amp;logoColor=white)
![Plotly](https://img.shields.io/badge/Plotly-%233F4F75.svg?style=for-the-badge&amp;logo=plotly&amp;logoColor=white)
![PyTorch](https://img.shields.io/badge/PyTorch-%23EE4C2C.svg?style=for-the-badge&amp;logo=PyTorch&amp;logoColor=white)

---

## 📊 GitHub Stats

&lt;div align="center"&gt;

&lt;img height="180em" src="https://github-readme-stats.vercel.app/api?username=Dantechdevs&amp;show_icons=true&amp;theme=github_dark&amp;include_all_commits=true&amp;count_private=true&amp;hide_border=true&amp;bg_color=0d1117&amp;title_color=58a6ff&amp;icon_color=58a6ff&amp;text_color=8b949e"/&gt;
&lt;img height="180em" src="https://github-readme-stats.vercel.app/api/top-langs/?username=Dantechdevs&amp;layout=compact&amp;langs_count=8&amp;theme=github_dark&amp;hide_border=true&amp;bg_color=0d1117&amp;title_color=58a6ff&amp;text_color=8b949e"/&gt;

&lt;/div&gt;

&lt;div align="center"&gt;

[![GitHub Streak](https://streak-stats.demolab.com/?user=Dantechdevs&amp;theme=github-dark-blue&amp;hide_border=true&amp;background=0d1117&amp;ring=58a6ff&amp;fire=ff6e6e&amp;currStreakLabel=58a6ff&amp;sideLabels=8b949e&amp;dates=8b949e)](https://git.io/streak-stats)

&lt;/div&gt;

&lt;div align="center"&gt;

[![Activity Graph](https://github-readme-activity-graph.vercel.app/graph?username=Dantechdevs&amp;bg_color=0d1117&amp;color=58a6ff&amp;line=58a6ff&amp;point=ffffff&amp;area=true&amp;hide_border=true&amp;custom_title=Daniel's%20Contribution%20Graph)](https://github.com/ashutosh00710/github-readme-activity-graph)

&lt;/div&gt;

---

## 🏆 GitHub Trophies

&lt;div align="center"&gt;

[![trophy](https://github-profile-trophy.vercel.app/?username=Dantechdevs&amp;theme=github_dark&amp;no-frame=true&amp;no-bg=true&amp;margin-w=6)](https://github.com/ryo-ma/github-profile-trophy)

&lt;/div&gt;

---

## ✍️ Random Dev Quote

&lt;div align="center"&gt;

![Dev Quote](https://quotes-github-readme.vercel.app/api?type=horizontal&amp;theme=dark)

&lt;/div&gt;

---

## 🐍 Contribution Snake

&lt;div align="center"&gt;

&lt;picture&gt;
  &lt;source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/Dantechdevs/Dantechdevs/output/github-contribution-grid-snake-dark.svg"/&gt;
  &lt;source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/Dantechdevs/Dantechdevs/output/github-contribution-grid-snake.svg"/&gt;
  &lt;img alt="Snake animation" src="https://raw.githubusercontent.com/Dantechdevs/Dantechdevs/output/github-contribution-grid-snake-dark.svg" width="100%"/&gt;
&lt;/picture&gt;

&lt;/div&gt;

---

&lt;div align="center"&gt;

[![](https://visitcount.itsvg.in/api?id=Dantechdevs&amp;label=Profile%20Views&amp;color=1&amp;icon=5&amp;pretty=true)](https://visitcount.itsvg.in)

*Thanks to [ABSphreak](https://github.com/manuarora700) for letting me know about this cool feature.*

&lt;/div&gt;

&lt;img src="https://capsule-render.vercel.app/api?type=waving&amp;color=gradient&amp;customColorList=12,14,20,24,30&amp;height=140&amp;section=footer&amp;animation=twinkling" width="100%"/&gt;</pre>
    </div>
  </section>


  <!-- ══ FOOTER ══ -->
  <div class="foot">
    <div class="foot-left">
      Thanks to <a href="https://github.com/manuarora700">ABSphreak</a> for the cool feature tip.
    </div>
    <div class="foot-views">
      <img src="https://visitcount.itsvg.in/api?id=Dantechdevs&label=Profile%20Views&color=1&icon=5&pretty=true" alt="Profile Views"/>
    </div>
  </div>

</div>

<div id="toast" class="toast">✅ Copied! Paste into GitHub README</div>

<script>
// Cursor
const c1=document.getElementById('c1'),c2=document.getElementById('c2');
let mx=0,my=0,lx=0,ly=0;
document.addEventListener('mousemove',e=>{
  mx=e.clientX;my=e.clientY;
  c1.style.transform=`translate(${mx}px,${my}px)`;
});
(function loop(){
  lx+=(mx-lx)*.14;ly+=(my-ly)*.14;
  c2.style.transform=`translate(${lx}px,${ly}px)`;
  requestAnimationFrame(loop);
})();
document.querySelectorAll('a,button,.chip,.soc,.stat-card,.pill').forEach(el=>{
  el.addEventListener('mouseenter',()=>{c2.style.width='44px';c2.style.height='44px';c2.style.margin='-22px 0 0 -22px';c2.style.borderColor='rgba(200,241,53,.6)'});
  el.addEventListener('mouseleave',()=>{c2.style.width='28px';c2.style.height='28px';c2.style.margin='-14px 0 0 -14px';c2.style.borderColor='rgba(200,241,53,.35)'});
});

// Scroll reveal
const obs=new IntersectionObserver(entries=>{
  entries.forEach(e=>{if(e.isIntersecting)e.target.classList.add('on')});
},{threshold:.07});
document.querySelectorAll('.sec').forEach(s=>obs.observe(s));

// Copy README
function copyMe(){
  const raw=document.getElementById('rme').innerText
    .replace(/&lt;/g,'<').replace(/&gt;/g,'>').replace(/&amp;/g,'&');
  navigator.clipboard.writeText(raw).then(()=>{
    const t=document.getElementById('toast');
    t.classList.add('show');
    setTimeout(()=>t.classList.remove('show'),2800);
  });
}
</script>
</body>
</html>
