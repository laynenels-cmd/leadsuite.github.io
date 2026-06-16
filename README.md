<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>LeadSuite — Data-Fueled Cold Email Engine for B2B Agencies</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@400;500;600;700&family=IBM+Plex+Sans:wght@400;500;600;700&family=IBM+Plex+Mono:wght@400;500;600&display=swap" rel="stylesheet">
<style>
  :root{
    --ink:#0D1117;          /* deep ground */
    --ink-2:#121A24;        /* raised dark surface */
    --ink-3:#19222F;        /* card on dark */
    --ink-4:#222D3C;        /* hairline-raised */
    --mist:#F4F6F8;         /* cool light section */
    --paper:#FFFFFF;
    --line-d:rgba(255,255,255,0.09);
    --line-l:#E3E8ED;
    --t-hi:#F6F8FB;         /* high text on dark */
    --t-mid:#98A6B5;        /* muted on dark */
    --t-ink:#0F141C;        /* text on light */
    --t-inkmute:#56616F;    /* muted on light */
    --ignite:#FF7A1A;       /* engine / heat / primary accent */
    --ignite-2:#FF9A4D;
    --ignite-soft:rgba(255,122,26,0.13);
    --fresh:#3DDC97;        /* fresh / verified / live signal */
    --fresh-soft:rgba(61,220,151,0.13);
    --warn:#FFC24B;
    --maxw:1180px;
    --display:'Space Grotesk',sans-serif;
    --body:'IBM Plex Sans',sans-serif;
    --mono:'IBM Plex Mono',monospace;
  }

  *{box-sizing:border-box;margin:0;padding:0}
  html{scroll-behavior:smooth}
  body{
    font-family:var(--body);
    background:var(--ink);
    color:var(--t-hi);
    line-height:1.6;
    -webkit-font-smoothing:antialiased;
    overflow-x:hidden;
  }
  h1,h2,h3,h4{font-family:var(--display);line-height:1.05;letter-spacing:-0.02em;font-weight:700}
  a{color:inherit;text-decoration:none}
  .mono{font-family:var(--mono)}

  /* ---------- layout primitives ---------- */
  .wrap{max-width:var(--maxw);margin:0 auto;padding:0 24px}
  .section{padding:104px 0;position:relative}
  .section--tight{padding:72px 0}
  .light{background:var(--mist);color:var(--t-ink)}
  .light h1,.light h2,.light h3,.light h4{color:var(--t-ink)}
  .ink2{background:var(--ink-2)}

  .eyebrow{
    font-family:var(--mono);font-size:12px;letter-spacing:0.22em;text-transform:uppercase;
    color:var(--ignite);font-weight:600;display:inline-flex;align-items:center;gap:9px;
  }
  .eyebrow::before{content:"";width:22px;height:1px;background:var(--ignite);display:inline-block}
  .light .eyebrow{color:#C2540A}
  .light .eyebrow::before{background:#C2540A}

  .sectionhead{max-width:760px;margin-bottom:54px}
  .sectionhead h2{font-size:clamp(30px,4.4vw,50px);margin:18px 0 16px}
  .sectionhead p{font-size:18px;color:var(--t-mid);max-width:640px}
  .light .sectionhead p{color:var(--t-inkmute)}

  /* ---------- buttons ---------- */
  .btn{
    display:inline-flex;align-items:center;justify-content:center;gap:9px;
    font-family:var(--display);font-weight:600;font-size:15.5px;letter-spacing:-0.01em;
    padding:15px 26px;border-radius:10px;cursor:pointer;border:1px solid transparent;
    transition:transform .15s ease, box-shadow .2s ease, background .2s ease;
  }
  .btn--primary{background:var(--ignite);color:#1A0E03;box-shadow:0 6px 24px rgba(255,122,26,.32)}
  .btn--primary:hover{transform:translateY(-2px);box-shadow:0 12px 34px rgba(255,122,26,.42)}
  .btn--ghost{background:transparent;border-color:var(--line-d);color:var(--t-hi)}
  .btn--ghost:hover{border-color:var(--ignite);color:var(--ignite-2)}
  .light .btn--ghost{border-color:var(--line-l);color:var(--t-ink)}
  .light .btn--ghost:hover{border-color:var(--ignite);color:#C2540A}
  .btn--lg{padding:18px 34px;font-size:16.5px}
  .btn .arr{transition:transform .15s ease}
  .btn:hover .arr{transform:translateX(3px)}

  /* ---------- nav ---------- */
  header.nav{position:sticky;top:0;z-index:50;background:rgba(13,17,23,.78);backdrop-filter:blur(14px);border-bottom:1px solid var(--line-d)}
  .nav .wrap{display:flex;align-items:center;justify-content:space-between;height:68px}
  .logo{display:flex;align-items:center;gap:10px;font-family:var(--display);font-weight:700;font-size:20px;letter-spacing:-0.03em}
  .logo .mark{
    width:26px;height:26px;border-radius:7px;
    background:linear-gradient(135deg,var(--ignite),var(--ignite-2));
    display:grid;place-items:center;color:#1A0E03;font-size:15px;font-weight:700;box-shadow:0 3px 12px rgba(255,122,26,.4)
  }
  .navlinks{display:flex;align-items:center;gap:30px;font-size:14.5px;color:var(--t-mid);font-weight:500}
  .navlinks a:hover{color:var(--t-hi)}
  .nav .btn{padding:11px 20px;font-size:14px}
  @media(max-width:860px){.navlinks{display:none}}

  /* ---------- hero ---------- */
  .hero{position:relative;padding:78px 0 96px;overflow:hidden}
  .hero::before{
    content:"";position:absolute;inset:0;z-index:0;
    background:
      radial-gradient(620px 360px at 78% 8%, rgba(255,122,26,.16), transparent 70%),
      radial-gradient(540px 420px at 6% 96%, rgba(61,220,151,.09), transparent 70%);
  }
  .hero .wrap{position:relative;z-index:1;display:grid;grid-template-columns:1.05fr .95fr;gap:54px;align-items:center}
  @media(max-width:980px){.hero .wrap{grid-template-columns:1fr;gap:42px}}
  .hero h1{font-size:clamp(38px,5.8vw,68px);margin:22px 0}
  .hero h1 .hot{color:var(--ignite)}
  .hero .sub{font-size:19px;color:var(--t-mid);max-width:560px;margin-bottom:32px}
  .hero .sub b{color:var(--t-hi);font-weight:600}
  .hero-cta{display:flex;gap:14px;flex-wrap:wrap;margin-bottom:26px}
  .hero-trust{display:flex;gap:26px;flex-wrap:wrap;font-size:13px;color:var(--t-mid)}
  .hero-trust span{display:inline-flex;align-items:center;gap:7px}
  .dot{width:7px;height:7px;border-radius:50%;background:var(--fresh);box-shadow:0 0 0 3px var(--fresh-soft)}

  /* ---------- console (hero signature) ---------- */
  .console{
    background:linear-gradient(180deg,var(--ink-3),var(--ink-2));
    border:1px solid var(--line-d);border-radius:16px;padding:6px;
    box-shadow:0 30px 70px rgba(0,0,0,.5);
  }
  .console-top{display:flex;align-items:center;gap:8px;padding:12px 14px;border-bottom:1px solid var(--line-d)}
  .console-top .led{width:9px;height:9px;border-radius:50%}
  .led.r{background:#FF5B5B}.led.y{background:var(--warn)}.led.g{background:var(--fresh)}
  .console-title{margin-left:8px;font-family:var(--mono);font-size:11.5px;letter-spacing:.12em;text-transform:uppercase;color:var(--t-mid)}
  .console-live{margin-left:auto;font-family:var(--mono);font-size:11px;color:var(--fresh);display:flex;align-items:center;gap:6px}
  .console-live .dot{animation:pulse 1.8s infinite}
  @keyframes pulse{0%,100%{opacity:1}50%{opacity:.35}}
  .console-body{padding:18px 16px 20px}
  .crow{border:1px solid var(--line-d);border-radius:11px;padding:14px 15px;margin-bottom:12px;background:rgba(255,255,255,.015)}
  .crow:last-child{margin-bottom:0}
  .crow-label{font-family:var(--mono);font-size:10.5px;letter-spacing:.16em;text-transform:uppercase;color:var(--t-mid);margin-bottom:9px;display:flex;justify-content:space-between}
  .crow-label .stage{color:var(--ignite)}
  .crow-main{display:flex;align-items:baseline;gap:10px}
  .crow-num{font-family:var(--mono);font-size:26px;font-weight:600;color:var(--t-hi)}
  .crow-unit{font-size:13px;color:var(--t-mid)}
  .pills{display:flex;gap:6px;flex-wrap:wrap;margin-top:11px}
  .pill{font-family:var(--mono);font-size:10.5px;padding:4px 9px;border-radius:20px;border:1px solid var(--line-d);color:var(--t-mid)}
  .pill.live{color:var(--fresh);border-color:rgba(61,220,151,.32);background:var(--fresh-soft)}
  .pill.hot{color:var(--ignite-2);border-color:rgba(255,122,26,.32);background:var(--ignite-soft)}
  .flowarrow{text-align:center;color:var(--t-mid);font-size:14px;margin:-4px 0 8px}

  /* ---------- stat bar ---------- */
  .statbar{border-top:1px solid var(--line-d);border-bottom:1px solid var(--line-d);background:var(--ink-2)}
  .statbar .grid{display:grid;grid-template-columns:repeat(4,1fr)}
  .stat{padding:34px 26px;border-right:1px solid var(--line-d)}
  .stat:last-child{border-right:none}
  .stat .n{font-family:var(--mono);font-size:30px;font-weight:600;color:var(--ignite);letter-spacing:-0.02em}
  .stat .l{font-size:13.5px;color:var(--t-mid);margin-top:5px}
  @media(max-width:760px){.statbar .grid{grid-template-columns:repeat(2,1fr)}.stat:nth-child(2n){border-right:none}.stat:nth-child(-n+2){border-bottom:1px solid var(--line-d)}}

  /* ---------- prose thesis ---------- */
  .thesis{max-width:780px}
  .thesis p{font-size:19px;color:var(--t-mid);margin-bottom:22px}
  .thesis p b{color:var(--t-hi);font-weight:600}
  .thesis .hammer{font-family:var(--display);font-size:clamp(22px,3vw,30px);line-height:1.25;color:var(--t-hi);font-weight:600;letter-spacing:-0.02em;margin:34px 0;padding-left:22px;border-left:3px solid var(--ignite)}
  .light .thesis p{color:var(--t-inkmute)}
  .light .thesis p b{color:var(--t-ink)}
  .light .thesis .hammer{color:var(--t-ink)}

  /* ---------- triple cards ---------- */
  .cards3{display:grid;grid-template-columns:repeat(3,1fr);gap:18px;margin-top:48px}
  @media(max-width:860px){.cards3{grid-template-columns:1fr}}
  .card{background:var(--ink-3);border:1px solid var(--line-d);border-radius:14px;padding:26px}
  .light .card{background:var(--paper);border-color:var(--line-l);box-shadow:0 2px 16px rgba(15,20,28,.04)}
  .card .ic{width:40px;height:40px;border-radius:10px;background:var(--ignite-soft);color:var(--ignite);display:grid;place-items:center;font-size:19px;margin-bottom:16px;font-family:var(--mono)}
  .card h4{font-size:18.5px;margin-bottom:9px}
  .card p{font-size:15px;color:var(--t-mid)}
  .light .card p{color:var(--t-inkmute)}

  /* ---------- broken alternatives ---------- */
  .broken{display:grid;grid-template-columns:repeat(2,1fr);gap:14px;margin-top:46px}
  @media(max-width:760px){.broken{grid-template-columns:1fr}}
  .brk{display:flex;gap:15px;padding:20px 22px;border:1px solid var(--line-l);border-radius:12px;background:var(--paper)}
  .brk .x{flex:0 0 auto;width:26px;height:26px;border-radius:7px;background:#FBE7E4;color:#D23B1F;display:grid;place-items:center;font-weight:700;font-size:14px;font-family:var(--mono)}
  .brk h4{font-size:16.5px;margin-bottom:4px}
  .brk p{font-size:14.5px;color:var(--t-inkmute)}

  /* ---------- mechanism flow ---------- */
  .mech{display:grid;grid-template-columns:repeat(5,1fr);gap:0;margin-top:50px;counter-reset:m}
  @media(max-width:960px){.mech{grid-template-columns:1fr}}
  .step{position:relative;padding:26px 22px;border:1px solid var(--line-d);border-radius:14px;background:var(--ink-3);margin-right:-1px}
  .step .sn{font-family:var(--mono);font-size:12px;color:var(--ignite);letter-spacing:.1em}
  .step h4{font-size:17px;margin:12px 0 9px}
  .step p{font-size:13.8px;color:var(--t-mid)}
  .step .tag{display:inline-block;margin-top:14px;font-family:var(--mono);font-size:10.5px;letter-spacing:.1em;text-transform:uppercase;padding:4px 9px;border-radius:6px}
  .tag.in{background:var(--fresh-soft);color:var(--fresh)}
  .tag.eng{background:var(--ignite-soft);color:var(--ignite-2)}
  .tag.out{background:rgba(255,255,255,.06);color:var(--t-hi)}

  /* ---------- infra under the hood ---------- */
  .hood{display:grid;grid-template-columns:1fr 1fr;gap:42px;align-items:center;margin-top:40px}
  @media(max-width:860px){.hood{grid-template-columns:1fr;gap:30px}}
  .hood ul{list-style:none;display:flex;flex-direction:column;gap:14px}
  .hood li{display:flex;gap:13px;font-size:16px;color:var(--t-mid)}
  .hood li b{color:var(--t-hi);font-weight:600}
  .hood li .ck{flex:0 0 auto;width:22px;height:22px;border-radius:6px;background:var(--fresh-soft);color:var(--fresh);display:grid;place-items:center;font-size:12px;margin-top:2px}
  .rig{background:linear-gradient(180deg,var(--ink-3),var(--ink-2));border:1px solid var(--line-d);border-radius:16px;padding:22px;box-shadow:0 24px 60px rgba(0,0,0,.4)}
  .rig .rhead{font-family:var(--mono);font-size:11px;letter-spacing:.16em;text-transform:uppercase;color:var(--t-mid);margin-bottom:16px;display:flex;justify-content:space-between}
  .domgrid{display:grid;grid-template-columns:repeat(6,1fr);gap:6px;margin-bottom:8px}
  .node{aspect-ratio:1;border-radius:7px;border:1px solid var(--line-d);display:grid;place-items:center;font-family:var(--mono);font-size:9px;color:var(--t-mid);background:rgba(255,255,255,.02)}
  .node.on{border-color:rgba(61,220,151,.4);color:var(--fresh);background:var(--fresh-soft)}
  .riglbl{font-family:var(--mono);font-size:10px;color:var(--t-mid);margin:14px 0 7px;letter-spacing:.08em}
  .meter{height:8px;border-radius:6px;background:var(--ink-4);overflow:hidden;margin-bottom:4px}
  .meter span{display:block;height:100%;background:linear-gradient(90deg,var(--fresh),#2fb47e)}
  .metaline{display:flex;justify-content:space-between;font-family:var(--mono);font-size:10.5px;color:var(--t-mid)}

  /* ---------- cost comparison ---------- */
  .compare{display:grid;grid-template-columns:1fr 1fr;gap:20px;margin-top:46px}
  @media(max-width:860px){.compare{grid-template-columns:1fr}}
  .col{border-radius:16px;padding:30px 28px;border:1px solid var(--line-l);background:var(--paper)}
  .col.win{border:1.5px solid var(--ignite);box-shadow:0 18px 50px rgba(255,122,26,.14);position:relative}
  .col .tophead{font-family:var(--mono);font-size:11px;letter-spacing:.18em;text-transform:uppercase;color:var(--t-inkmute);margin-bottom:6px}
  .col h3{font-size:23px;margin-bottom:22px;color:var(--t-ink)}
  .col.win h3{color:#C2540A}
  .col ul{list-style:none;display:flex;flex-direction:column;gap:13px;margin-bottom:24px}
  .col li{display:flex;gap:11px;font-size:15px;color:var(--t-inkmute);align-items:flex-start}
  .col li .m{flex:0 0 auto;font-size:14px;margin-top:1px}
  .col.diy li .m{color:#D23B1F}
  .col.win li .m{color:var(--fresh);font-weight:700}
  .col .total{border-top:1px solid var(--line-l);padding-top:18px}
  .col .total .lbl{font-size:13px;color:var(--t-inkmute);margin-bottom:4px}
  .col .total .big{font-family:var(--mono);font-size:30px;font-weight:600;color:var(--t-ink)}
  .col.win .total .big{color:#C2540A}
  .ribbon{position:absolute;top:-13px;right:24px;background:var(--ignite);color:#1A0E03;font-family:var(--mono);font-size:11px;letter-spacing:.1em;text-transform:uppercase;padding:5px 13px;border-radius:7px;font-weight:600}

  /* ---------- roadmap ---------- */
  .road{display:flex;flex-direction:column;gap:18px;margin-top:46px}
  .phase{display:grid;grid-template-columns:120px 1fr;gap:26px;border:1px solid var(--line-d);border-radius:16px;padding:28px;background:var(--ink-3)}
  @media(max-width:760px){.phase{grid-template-columns:1fr;gap:16px}}
  .phase .pn{font-family:var(--mono)}
  .phase .pn .big{font-size:42px;color:var(--ignite);font-weight:600;display:block;line-height:1}
  .phase .pn .wk{font-size:12px;color:var(--t-mid);letter-spacing:.08em;text-transform:uppercase;margin-top:8px;display:block}
  .phase h4{font-size:20px;margin-bottom:14px}
  .phase ul{list-style:none;display:grid;grid-template-columns:1fr 1fr;gap:10px}
  @media(max-width:620px){.phase ul{grid-template-columns:1fr}}
  .phase li{display:flex;gap:10px;font-size:14.5px;color:var(--t-mid)}
  .phase li .ck{color:var(--fresh);font-family:var(--mono);flex:0 0 auto}

  /* ---------- division of labor ---------- */
  .labor{display:grid;grid-template-columns:1fr 1fr;gap:20px;margin-top:46px}
  @media(max-width:760px){.labor{grid-template-columns:1fr}}
  .lcol{border:1px solid var(--line-d);border-radius:16px;padding:30px 28px;background:var(--ink-3)}
  .lcol.us{border-color:rgba(255,122,26,.35)}
  .lcol .lh{display:flex;align-items:center;gap:11px;margin-bottom:22px;font-family:var(--display);font-size:20px;font-weight:600}
  .lcol .lh .badge{font-family:var(--mono);font-size:11px;padding:4px 10px;border-radius:6px}
  .us .lh .badge{background:var(--ignite-soft);color:var(--ignite)}
  .you .lh .badge{background:var(--fresh-soft);color:var(--fresh)}
  .lcol ul{list-style:none;display:flex;flex-direction:column;gap:12px}
  .lcol li{display:flex;gap:12px;font-size:15px;color:var(--t-mid)}
  .lcol li .ck{flex:0 0 auto;color:var(--ignite);font-family:var(--mono)}
  .you li .ck{color:var(--fresh)}

  /* ---------- deliverables ---------- */
  .deliv{display:grid;grid-template-columns:repeat(3,1fr);gap:10px;margin-top:46px}
  @media(max-width:860px){.deliv{grid-template-columns:repeat(2,1fr)}}
  @media(max-width:560px){.deliv{grid-template-columns:1fr}}
  .ditem{display:flex;gap:11px;padding:15px 17px;border:1px solid var(--line-l);border-radius:10px;background:var(--paper);font-size:14.5px;color:var(--t-ink)}
  .ditem .ck{flex:0 0 auto;color:var(--ignite);font-family:var(--mono);font-weight:700}

  /* ---------- proof / believability ---------- */
  .proofgrid{display:grid;grid-template-columns:repeat(3,1fr);gap:18px;margin-top:46px}
  @media(max-width:860px){.proofgrid{grid-template-columns:1fr}}
  .pcard{background:var(--ink-3);border:1px solid var(--line-d);border-radius:14px;padding:26px}
  .pcard .k{font-family:var(--mono);font-size:11px;letter-spacing:.14em;text-transform:uppercase;color:var(--ignite);margin-bottom:12px}
  .pcard h4{font-size:18px;margin-bottom:9px}
  .pcard p{font-size:14.5px;color:var(--t-mid)}

  /* ---------- guarantee ---------- */
  .guarantee{border:1.5px solid rgba(255,122,26,.4);border-radius:18px;padding:42px;background:linear-gradient(180deg,var(--ink-3),var(--ink-2));margin-top:10px;display:grid;grid-template-columns:auto 1fr;gap:30px;align-items:center}
  @media(max-width:760px){.guarantee{grid-template-columns:1fr;gap:20px;padding:30px}}
  .gseal{width:96px;height:96px;border-radius:50%;border:2px solid var(--ignite);display:grid;place-items:center;text-align:center;font-family:var(--mono);font-size:11px;color:var(--ignite);letter-spacing:.08em;line-height:1.3}
  .guarantee h3{font-size:24px;margin-bottom:12px}
  .guarantee p{font-size:16px;color:var(--t-mid)}
  .guarantee p+p{margin-top:12px}

  /* ---------- pricing ---------- */
  .price-note{font-family:var(--mono);font-size:12.5px;color:var(--t-inkmute);text-align:center;margin-bottom:40px;letter-spacing:.04em}
  .plans{display:grid;grid-template-columns:1fr 1fr;gap:22px;max-width:880px;margin:0 auto}
  @media(max-width:760px){.plans{grid-template-columns:1fr}}
  .plan{border:1px solid var(--line-l);border-radius:18px;padding:34px 32px;background:var(--paper);display:flex;flex-direction:column}
  .plan.pop{border:1.5px solid var(--ignite);box-shadow:0 20px 56px rgba(255,122,26,.16);position:relative}
  .plan .pname{font-family:var(--mono);font-size:12px;letter-spacing:.16em;text-transform:uppercase;color:var(--t-inkmute);margin-bottom:14px}
  .plan .price{display:flex;align-items:baseline;gap:6px;margin-bottom:4px}
  .plan .price .amt{font-family:var(--mono);font-size:46px;font-weight:600;color:var(--t-ink);letter-spacing:-0.02em}
  .plan .price .per{font-size:15px;color:var(--t-inkmute)}
  .plan .qtr{font-family:var(--mono);font-size:13px;color:#C2540A;margin-bottom:24px}
  .plan ul{list-style:none;display:flex;flex-direction:column;gap:12px;margin-bottom:28px;flex:1}
  .plan li{display:flex;gap:11px;font-size:14.8px;color:var(--t-ink)}
  .plan li .ck{flex:0 0 auto;color:var(--ignite);font-family:var(--mono);font-weight:700}
  .plan .btn{width:100%}
  .plan.pop .pname{color:#C2540A}

  /* ---------- scarcity ---------- */
  .scar{display:flex;align-items:center;gap:18px;max-width:780px;margin:46px auto 0;padding:24px 28px;border:1px solid rgba(255,122,26,.3);border-radius:14px;background:var(--ignite-soft)}
  .scar .ic{font-size:24px}
  .scar p{font-size:15.5px;color:var(--t-hi)}
  .scar p b{color:var(--ignite-2)}

  /* ---------- faq ---------- */
  .faq{max-width:820px;margin:46px auto 0}
  .qa{border-bottom:1px solid var(--line-d)}
  .qa button{width:100%;text-align:left;background:none;border:none;color:var(--t-hi);font-family:var(--display);font-size:18px;font-weight:600;padding:24px 40px 24px 0;cursor:pointer;position:relative;letter-spacing:-0.01em}
  .qa button::after{content:"+";position:absolute;right:6px;top:50%;transform:translateY(-50%);color:var(--ignite);font-size:24px;font-family:var(--mono);transition:transform .2s}
  .qa.open button::after{content:"−"}
  .qa .ans{max-height:0;overflow:hidden;transition:max-height .3s ease;color:var(--t-mid);font-size:15.5px}
  .qa .ans p{padding-bottom:24px}

  /* ---------- final cta ---------- */
  .final{position:relative;text-align:center;overflow:hidden}
  .final::before{content:"";position:absolute;inset:0;background:radial-gradient(700px 400px at 50% 0%,rgba(255,122,26,.18),transparent 70%)}
  .final .wrap{position:relative;z-index:1;max-width:760px}
  .final h2{font-size:clamp(32px,5vw,56px);margin-bottom:18px}
  .final h2 .hot{color:var(--ignite)}
  .final p{font-size:19px;color:var(--t-mid);margin-bottom:34px}
  .final .hero-cta{justify-content:center}

  footer{border-top:1px solid var(--line-d);padding:42px 0;background:var(--ink)}
  footer .wrap{display:flex;justify-content:space-between;align-items:center;flex-wrap:wrap;gap:18px;font-size:13.5px;color:var(--t-mid)}
  footer .legal{max-width:640px;line-height:1.6}

  /* ---------- reveal ---------- */
  .reveal{opacity:0;transform:translateY(24px);transition:opacity .7s ease, transform .7s ease}
  .reveal.in{opacity:1;transform:none}
  @media(prefers-reduced-motion:reduce){
    .reveal{opacity:1;transform:none;transition:none}
    .console-live .dot{animation:none}
    html{scroll-behavior:auto}
  }
</style>
</head>
<body>

<!-- NAV -->
<header class="nav">
  <div class="wrap">
    <a class="logo" href="#top"><span class="mark">L</span>LeadSuite</a>
    <nav class="navlinks">
      <a href="#mechanism">How it works</a>
      <a href="#cost">vs. DIY</a>
      <a href="#roadmap">Timeline</a>
      <a href="#pricing">Pricing</a>
      <a href="#faq">FAQ</a>
    </nav>
    <a href="#pricing" class="btn btn--primary">Book a Strategy Call</a>
  </div>
</header>

<!-- HERO -->
<section class="hero" id="top">
  <div class="wrap">
    <div class="reveal">
      <span class="eyebrow">Done-for-you · Onboarding 3–5 partners this quarter</span>
      <h1>Cold email isn't dead.<br><span class="hot">Your lead source is.</span></h1>
      <p class="sub">We build and manage a data-fueled cold email engine that pulls <b>30,000–45,000 fresh, Instagram-sourced B2B prospects</b> into your pipeline every month — and turns the replies into qualified sales conversations. <b>You approve the strategy, take the calls, and close. We run everything else.</b></p>
      <div class="hero-cta">
        <a href="#pricing" class="btn btn--primary btn--lg">See pricing &amp; plans <span class="arr">→</span></a>
        <a href="#mechanism" class="btn btn--ghost btn--lg">How the engine works</a>
      </div>
      <div class="hero-trust">
        <span><span class="dot"></span> Private cold email infrastructure</span>
        <span><span class="dot"></span> 24/7 AI deliverability monitoring</span>
        <span><span class="dot"></span> Fresh leads every month</span>
      </div>
    </div>

    <!-- signature: engine console -->
    <div class="reveal">
      <div class="console" role="img" aria-label="Outbound engine console showing fresh leads sourced, infrastructure running, and positive replies routed">
        <div class="console-top">
          <span class="led r"></span><span class="led y"></span><span class="led g"></span>
          <span class="console-title">leadsuite_engine.live</span>
          <span class="console-live"><span class="dot"></span> RUNNING</span>
        </div>
        <div class="console-body">
          <div class="crow">
            <div class="crow-label"><span>Input — fresh sourcing</span><span class="stage">LeadSweeper</span></div>
            <div class="crow-main"><span class="crow-num">38,420</span><span class="crow-unit">IG-sourced prospects scraped this cycle</span></div>
            <div class="pills"><span class="pill live">enriched</span><span class="pill live">verified</span><span class="pill">deduped</span></div>
          </div>
          <div class="flowarrow">↓</div>
          <div class="crow">
            <div class="crow-label"><span>Engine — sending</span><span class="stage">SmartLead · 90 inboxes</span></div>
            <div class="crow-main"><span class="crow-num">98.1%</span><span class="crow-unit">inbox deliverability · spam 0.2%</span></div>
            <div class="pills"><span class="pill hot">warmup ok</span><span class="pill hot">domains healthy</span><span class="pill">3-step seq</span></div>
          </div>
          <div class="flowarrow">↓</div>
          <div class="crow">
            <div class="crow-label"><span>Output — to you</span><span class="stage">routed + phone-enriched</span></div>
            <div class="crow-main"><span class="crow-num">+147</span><span class="crow-unit">positive replies pushed to your inbox</span></div>
            <div class="pills"><span class="pill live">interested</span><span class="pill live">meeting req</span><span class="pill">📞 enriched</span></div>
          </div>
        </div>
      </div>
      <p style="font-family:var(--mono);font-size:11px;color:var(--t-mid);text-align:center;margin-top:12px;letter-spacing:.06em">Illustrative console. Volumes reflect plan capacity, not a results guarantee.</p>
    </div>
  </div>
</section>

<!-- STAT BAR -->
<section class="statbar">
  <div class="wrap" style="padding:0">
    <div class="grid">
      <div class="stat reveal"><div class="n">30K–45K</div><div class="l">Fresh prospects contacted / month</div></div>
      <div class="stat reveal"><div class="n">60–90</div><div class="l">Private inboxes built &amp; monitored</div></div>
      <div class="stat reveal"><div class="n">5–8 wks</div><div class="l">From kickoff to live campaigns</div></div>
      <div class="stat reveal"><div class="n">24/7</div><div class="l">AI deliverability monitoring</div></div>
    </div>
  </div>
</section>

<!-- THESIS -->
<section class="section" id="why">
  <div class="wrap">
    <div class="reveal">
      <span class="eyebrow">Why this works</span>
      <div class="sectionhead"><h2>Fresh inputs beat better automation</h2></div>
    </div>
    <div class="thesis reveal">
      <p>Here's the uncomfortable truth almost nobody in this space will tell you: <b>most cold email doesn't fail because the copy is bad.</b> It fails before a single email is ever written.</p>
      <p>99% of outbound runs on the exact same fuel. The same Apollo export. The same ZoomInfo list. The same contacts your three closest competitors already hammered last quarter. You can hire the best copywriter alive and it won't matter — <b>you're rewording a better message to a worse audience.</b></p>
      <div class="hammer">Outbound isn't broken. The inputs are.</div>
      <p>So we fix the inputs first. Instead of starting where everyone else starts — a recycled database — we start with <b>live public business signals from Instagram:</b> the niches, accounts, hashtags, locations, and audience clusters where your buyers are visibly active right now. Then we enrich, validate, clean, and suppress before a single send.</p>
      <p>That fresh, less-commoditized data goes into <b>private cold email infrastructure</b> — separate from your main domain — and gets activated through <b>SmartLead campaigns we write, launch, monitor, and optimize every month.</b> The result is a managed outbound engine: a consistent path to qualified sales conversations without you buying stale lists, babysitting deliverability, or manually prospecting.</p>
      <p>This is the same play that built outbound pipelines that don't dry up the moment referrals slow down. <b>Steal it. We'll run it for you.</b></p>
    </div>

    <div class="cards3">
      <div class="card reveal">
        <div class="ic">01</div>
        <h4>Fresh data, not recycled lists</h4>
        <p>Prospects sourced from live Instagram business signals — then enriched and verified — instead of the same database every competitor is already buying.</p>
      </div>
      <div class="card reveal">
        <div class="ic">02</div>
        <h4>Infrastructure that protects you</h4>
        <p>60–90 private inboxes across 30–45 fresh domains. You never send from your main business domain. Deliverability is monitored around the clock.</p>
      </div>
      <div class="card reveal">
        <div class="ic">03</div>
        <h4>Managed every single month</h4>
        <p>New lists, new campaigns, new tests — every month. We don't hand you a setup and disappear. We run the engine and report on it.</p>
      </div>
    </div>
  </div>
</section>

<!-- BROKEN ALTERNATIVES -->
<section class="section light" id="broken">
  <div class="wrap">
    <div class="reveal">
      <span class="eyebrow">You've tried to fix this before</span>
      <div class="sectionhead">
        <h2>Why the usual fixes didn't stick</h2>
        <p>You're not new to outbound. You're overexposed to it. Here's exactly where each path breaks down — and why none of them solved the input problem.</p>
      </div>
    </div>
    <div class="broken">
      <div class="brk reveal"><div class="x">✕</div><div><h4>Apollo / ZoomInfo lists</h4><p>Broad, overused, and decaying. Outdated titles, bouncing emails, and the same names your competitors are already emailing.</p></div></div>
      <div class="brk reveal"><div class="x">✕</div><div><h4>Cheap list vendors</h4><p>Looks fine on a spreadsheet. Then half of it bounces and the replies are dead. You paid for volume, not fit.</p></div></div>
      <div class="brk reveal"><div class="x">✕</div><div><h4>DIY cold email</h4><p>You become a part-time deliverability operator — domains, DNS, warmup, inbox rotation, reply triage — instead of closing deals.</p></div></div>
      <div class="brk reveal"><div class="x">✕</div><div><h4>Hiring an SDR</h4><p>$11K–$16K/mo all-in with manager and tooling, 60–90 days to ramp, 35%+ turnover — before you've proven the motion works.</p></div></div>
      <div class="brk reveal"><div class="x">✕</div><div><h4>Generic outbound agencies</h4><p>Same lists, same scripts, same vanity metrics. "We book meetings" means nothing when the meetings aren't qualified.</p></div></div>
      <div class="brk reveal"><div class="x">✕</div><div><h4>VAs &amp; one-off scraping tools</h4><p>Manual, inconsistent, and impossible to scale to the volume that makes outbound actually work. A tool isn't a system.</p></div></div>
    </div>
  </div>
</section>

<!-- MECHANISM -->
<section class="section" id="mechanism">
  <div class="wrap">
    <div class="reveal">
      <span class="eyebrow">The mechanism</span>
      <div class="sectionhead">
        <h2>The Data-Fueled Cold Email Engine</h2>
        <p>Five components running as one managed system. The order matters: we fix the input layer first, then build the campaign engine around it.</p>
      </div>
    </div>
    <div class="mech">
      <div class="step reveal">
        <div class="sn">STEP 01</div>
        <h4>LeadSweeper sourcing</h4>
        <p>Fresh e-commerce and Instagram-active business data scraped from live public signals — bios, sites, contact clues, audience clusters.</p>
        <span class="tag in">Fresh input</span>
      </div>
      <div class="step reveal">
        <div class="sn">STEP 02</div>
        <h4>Enrichment</h4>
        <p>Routed through ListKit, ZoomInfo, Apollo and more to append decision-maker contacts, verify emails, and fill the gaps.</p>
        <span class="tag in">Verified</span>
      </div>
      <div class="step reveal">
        <div class="sn">STEP 03</div>
        <h4>Private infrastructure</h4>
        <p>60–90 inboxes on private infrastructure across fresh domains — never your main domain — warmed and monitored for sender health.</p>
        <span class="tag eng">Engine</span>
      </div>
      <div class="step reveal">
        <div class="sn">STEP 04</div>
        <h4>SmartLead execution</h4>
        <p>A 3-step sequence we write, launch, and manage. Sending volume, inbox config, and performance handled end to end.</p>
        <span class="tag eng">Engine</span>
      </div>
      <div class="step reveal">
        <div class="sn">STEP 05</div>
        <h4>Optimize &amp; refresh</h4>
        <p>New lists monthly, copy tested continuously, deliverability watched 24/7. Positive replies phone-enriched and pushed to you.</p>
        <span class="tag out">Output</span>
      </div>
    </div>
  </div>
</section>

<!-- UNDER THE HOOD -->
<section class="section ink2" id="infra">
  <div class="wrap">
    <div class="reveal">
      <span class="eyebrow">Under the hood</span>
      <div class="sectionhead">
        <h2>The infrastructure you never have to touch</h2>
        <p>You'll never log into any of this. But here's what's running for you — so you understand the depth of what we build and manage.</p>
      </div>
    </div>
    <div class="hood">
      <ul class="reveal">
        <li><span class="ck">✓</span><span><b>30–45 fresh sending domains</b> purchased through PorkBun and configured for you — isolated from your primary business domain.</span></li>
        <li><span class="ck">✓</span><span><b>60–90 private inboxes</b> on LeadSuite infrastructure, warmed and rotated to protect deliverability.</span></li>
        <li><span class="ck">✓</span><span><b>24/7 AI deliverability monitoring</b> that flags inbox health issues and reconnects or replaces underperformers before they cost you.</span></li>
        <li><span class="ck">✓</span><span><b>SmartLead campaign execution</b> — sequence logic, sending controls, reply tracking, and performance monitoring.</span></li>
        <li><span class="ck">✓</span><span><b>Phone enrichment on positive replies</b> so your interested prospects come with a number, ready for fast follow-up.</span></li>
      </ul>
      <div class="rig reveal">
        <div class="rhead"><span>infrastructure_panel</span><span style="color:var(--fresh)">● healthy</span></div>
        <div class="domgrid">
          <div class="node on">D01</div><div class="node on">D02</div><div class="node on">D03</div><div class="node on">D04</div><div class="node on">D05</div><div class="node">+40</div>
        </div>
        <div class="riglbl">DOMAINS ONLINE · 45 / 45</div>
        <div class="riglbl">INBOX DELIVERABILITY</div>
        <div class="meter"><span style="width:98%"></span></div>
        <div class="metaline"><span>98.1% primary inbox</span><span>spam 0.2%</span></div>
        <div class="riglbl" style="margin-top:16px">WARMUP STATUS · 90 INBOXES</div>
        <div class="meter"><span style="width:100%"></span></div>
        <div class="metaline"><span>100% warmed</span><span>0 flagged</span></div>
      </div>
    </div>
  </div>
</section>

<!-- COST COMPARISON -->
<section class="section light" id="cost">
  <div class="wrap">
    <div class="reveal">
      <span class="eyebrow">The real cost comparison</span>
      <div class="sectionhead">
        <h2>Why building this yourself rarely pencils out</h2>
        <p>Most teams underestimate what it costs to assemble — and keep alive — the stack required to run outbound at the volume that actually moves the needle.</p>
      </div>
    </div>
    <div class="compare">
      <div class="col diy reveal">
        <div class="tophead">The DIY route</div>
        <h3>Building it in-house</h3>
        <ul>
          <li><span class="m">✕</span> $11,000–$16,000/mo for one SDR once you add salary, manager, and benefits</li>
          <li><span class="m">✕</span> 60–90 days to hire, onboard, and ramp — with 35%+ annual turnover</li>
          <li><span class="m">✕</span> Tool stack: scraping, enrichment, inboxes, domains, sending tool (~$1,000+/mo)</li>
          <li><span class="m">✕</span> You still source the data, write the copy, and watch deliverability yourself</li>
          <li><span class="m">✕</span> Domains burning and emails in spam while you learn DNS the hard way</li>
          <li><span class="m">✕</span> The same recycled lists everyone else is already using</li>
        </ul>
        <div class="total"><div class="lbl">Realistic monthly cost (1 SDR + stack + overhead)</div><div class="big">$12,000–$17,000/mo</div></div>
      </div>
      <div class="col win reveal">
        <span class="ribbon">The LeadSuite way</span>
        <div class="tophead">Done-for-you</div>
        <h3>The managed engine</h3>
        <ul>
          <li><span class="m">✓</span> Full cold email engine built &amp; managed for you — live in weeks, not months</li>
          <li><span class="m">✓</span> Fresh Instagram-sourced lead lists rebuilt every single month</li>
          <li><span class="m">✓</span> Private infrastructure — 30–45 domains, 60–90 inboxes, max deliverability protection</li>
          <li><span class="m">✓</span> Copy, sequences, sending, and optimization handled end to end</li>
          <li><span class="m">✓</span> 24/7 AI deliverability monitoring so your sends keep landing</li>
          <li><span class="m">✓</span> No hiring, no managing, no tool sprawl — you approve and close</li>
        </ul>
        <div class="total"><div class="lbl">Starting at (Minimum plan, billed quarterly)</div><div class="big">$3,000/mo</div></div>
      </div>
    </div>
  </div>
</section>

<!-- ROADMAP -->
<section class="section" id="roadmap">
  <div class="wrap">
    <div class="reveal">
      <span class="eyebrow">Launch timeline</span>
      <div class="sectionhead">
        <h2>From kickoff to live campaigns in weeks</h2>
        <p>A bounded, three-phase build. You know exactly what happens, and when.</p>
      </div>
    </div>
    <div class="road">
      <div class="phase reveal">
        <div class="pn"><span class="big">01</span><span class="wk">Weeks 1–2</span></div>
        <div>
          <h4>Discovery &amp; strategy</h4>
          <ul>
            <li><span class="ck">›</span> Review your offer, ICP, and sales motion</li>
            <li><span class="ck">›</span> Define exact lead criteria &amp; Instagram sourcing angles</li>
            <li><span class="ck">›</span> First LeadSweeper sourcing strategy built</li>
            <li><span class="ck">›</span> PorkBun domains purchased &amp; configured</li>
            <li><span class="ck">›</span> SmartLead campaign structure set up</li>
            <li><span class="ck">›</span> First cold email script drafted for your approval</li>
          </ul>
        </div>
      </div>
      <div class="phase reveal">
        <div class="pn"><span class="big">02</span><span class="wk">Weeks 3–4</span></div>
        <div>
          <h4>Build &amp; configuration</h4>
          <ul>
            <li><span class="ck">›</span> First targeted lead list scraped &amp; prepared</li>
            <li><span class="ck">›</span> Missing data enriched via ListKit &amp; sources</li>
            <li><span class="ck">›</span> 3-step sequence finalized</li>
            <li><span class="ck">›</span> Inboxes warmed, deliverability checks run</li>
            <li><span class="ck">›</span> AI deliverability monitoring configured</li>
            <li><span class="ck">›</span> Reporting format &amp; reply tracking prepared</li>
          </ul>
        </div>
      </div>
      <div class="phase reveal">
        <div class="pn"><span class="big">03</span><span class="wk">Weeks 5–8</span></div>
        <div>
          <h4>Launch, optimize &amp; scale</h4>
          <ul>
            <li><span class="ck">›</span> First campaign goes live</li>
            <li><span class="ck">›</span> Deliverability, bounce, and reply behavior monitored</li>
            <li><span class="ck">›</span> Positive replies routed &amp; phone-enriched for you</li>
            <li><span class="ck">›</span> New email angles tested on live feedback</li>
            <li><span class="ck">›</span> Additional monthly lead lists built</li>
            <li><span class="ck">›</span> Volume scaled once the system is stable</li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- DIVISION OF LABOR -->
<section class="section ink2" id="labor">
  <div class="wrap">
    <div class="reveal">
      <span class="eyebrow">Division of labor</span>
      <div class="sectionhead">
        <h2>What we handle vs. what you handle</h2>
        <p>A clean split. We run the machine. Your team stays focused on the only two things that actually require you: real conversations and closing.</p>
      </div>
    </div>
    <div class="labor">
      <div class="lcol us reveal">
        <div class="lh"><span class="badge">LEADSUITE</span> We handle</div>
        <ul>
          <li><span class="ck">▸</span> Custom inbox &amp; domain setup</li>
          <li><span class="ck">▸</span> LeadSweeper scraping &amp; monthly list building</li>
          <li><span class="ck">▸</span> Contact data enrichment</li>
          <li><span class="ck">▸</span> Cold email copy &amp; 3-step sequences</li>
          <li><span class="ck">▸</span> SmartLead setup, launch &amp; management</li>
          <li><span class="ck">▸</span> Deliverability &amp; inbox health monitoring</li>
          <li><span class="ck">▸</span> Campaign optimization &amp; monthly reporting</li>
          <li><span class="ck">▸</span> Phone enrichment on positive replies</li>
          <li><span class="ck">▸</span> Infrastructure troubleshooting</li>
        </ul>
      </div>
      <div class="lcol you reveal">
        <div class="lh"><span class="badge">YOUR TEAM</span> You handle</div>
        <ul>
          <li><span class="ck">✓</span> Approve messaging &amp; strategy</li>
          <li><span class="ck">✓</span> Give feedback on target market &amp; positioning</li>
          <li><span class="ck">✓</span> Respond to interested leads in your inbox</li>
          <li><span class="ck">✓</span> Take the sales calls</li>
          <li><span class="ck">✓</span> Follow up with qualified opportunities</li>
          <li><span class="ck">✓</span> Sign clients</li>
        </ul>
        <p style="margin-top:18px;font-size:14px;color:var(--t-mid)">You never manage the backend infrastructure, scraping, list building, deliverability, SmartLead, inboxes, or campaign operations. That's the whole point.</p>
      </div>
    </div>
  </div>
</section>

<!-- DELIVERABLES -->
<section class="section light" id="deliverables">
  <div class="wrap">
    <div class="reveal">
      <span class="eyebrow">The offer stack</span>
      <div class="sectionhead">
        <h2>Everything that's built, launched &amp; run for you</h2>
        <p>This isn't software access or a list drop. It's a managed system, delivered in full.</p>
      </div>
    </div>
    <div class="deliv">
      <div class="ditem reveal"><span class="ck">✓</span> Custom cold email outreach engine</div>
      <div class="ditem reveal"><span class="ck">✓</span> LeadSweeper-powered lead sourcing</div>
      <div class="ditem reveal"><span class="ck">✓</span> Fresh monthly lead list creation</div>
      <div class="ditem reveal"><span class="ck">✓</span> Instagram-sourced business lead data</div>
      <div class="ditem reveal"><span class="ck">✓</span> Enrichment via ListKit, ZoomInfo, Apollo</div>
      <div class="ditem reveal"><span class="ck">✓</span> PorkBun domain setup guidance</div>
      <div class="ditem reveal"><span class="ck">✓</span> 60–90 cold email inboxes</div>
      <div class="ditem reveal"><span class="ck">✓</span> Private cold email infrastructure</div>
      <div class="ditem reveal"><span class="ck">✓</span> SmartLead campaign setup &amp; access</div>
      <div class="ditem reveal"><span class="ck">✓</span> 24/7 AI deliverability monitoring</div>
      <div class="ditem reveal"><span class="ck">✓</span> Inbox warmup &amp; health checks</div>
      <div class="ditem reveal"><span class="ck">✓</span> 3-step cold email sequence</div>
      <div class="ditem reveal"><span class="ck">✓</span> Monthly campaign writing</div>
      <div class="ditem reveal"><span class="ck">✓</span> Campaign launch &amp; management</div>
      <div class="ditem reveal"><span class="ck">✓</span> Monthly optimization &amp; new tests</div>
      <div class="ditem reveal"><span class="ck">✓</span> Positive reply tracking</div>
      <div class="ditem reveal"><span class="ck">✓</span> Phone enrichment for positive replies</div>
      <div class="ditem reveal"><span class="ck">✓</span> Monthly performance reporting</div>
    </div>
  </div>
</section>

<!-- PROOF / BELIEVABILITY -->
<section class="section" id="proof">
  <div class="wrap">
    <div class="reveal">
      <span class="eyebrow">Why you can believe it works</span>
      <div class="sectionhead">
        <h2>We show you the messy middle</h2>
        <p>Most outbound offers hide the part that matters. We do the opposite. Before you commit a dollar, you see exactly how the engine is built, sourced, and measured.</p>
      </div>
    </div>
    <div class="proofgrid">
      <div class="pcard reveal">
        <div class="k">Mechanism proof</div>
        <h4>A specific, bounded system</h4>
        <p>Not "we book meetings." A defined input layer, defined infrastructure, defined sequence, defined reporting. On your strategy call we walk the exact sourcing path for your market.</p>
      </div>
      <div class="pcard reveal">
        <div class="k">Process proof</div>
        <h4>Sample leads &amp; infra checklist</h4>
        <p>You see how Instagram signals map to your ICP, what enrichment and validation look like, and the deliverability checklist your sending runs through — before launch.</p>
      </div>
      <div class="pcard reveal">
        <div class="k">Operational proof</div>
        <h4>Reporting you can read</h4>
        <p>Monthly reporting on sends, replies, positive responses, and deliverability health — so you always know what the engine is doing and what's converting.</p>
      </div>
    </div>
  </div>
</section>

<!-- GUARANTEE -->
<section class="section ink2" id="guarantee">
  <div class="wrap">
    <div class="reveal">
      <span class="eyebrow">Risk reversal</span>
      <div class="sectionhead"><h2>We guarantee the build &amp; the execution</h2></div>
    </div>
    <div class="guarantee reveal">
      <div class="gseal">BUILD<br>&amp;<br>LAUNCH<br>GUARANTEE</div>
      <div>
        <h3>If it isn't live, we keep working — free.</h3>
        <p>We guarantee your cold email outreach engine will be built, configured, launched, monitored, and optimized to the agreed execution timeline. If we don't complete the infrastructure setup, lead list buildout, campaign sequence, and first campaign launch within the agreed onboarding window, <b style="color:var(--t-hi)">we keep working at no additional management fee until the system is live.</b></p>
        <p>And if deliverability issues come up, we diagnose, troubleshoot, and optimize the infrastructure at no additional management fee as part of the ongoing service. We guarantee the buildout and the execution — the parts we control — not closed revenue, which depends on your offer, pricing, and close rate.</p>
      </div>
    </div>
  </div>
</section>

<!-- PRICING -->
<section class="section light" id="pricing">
  <div class="wrap">
    <div class="reveal" style="text-align:center">
      <span class="eyebrow" style="justify-content:center">Investment</span>
      <div class="sectionhead" style="margin:18px auto 0;text-align:center">
        <h2 style="margin:0 auto">Choose your outbound engine</h2>
      </div>
    </div>
    <p class="price-note">Billed quarterly · 90-day minimum commitment · No setup fees</p>
    <div class="plans">
      <div class="plan reveal">
        <div class="pname">Minimum</div>
        <div class="price"><span class="amt">$3,000</span><span class="per">/mo</span></div>
        <div class="qtr">$9,000 / quarter</div>
        <ul>
          <li><span class="ck">✓</span> Up to 30,000 emails &amp; leads contacted / month</li>
          <li><span class="ck">✓</span> 30 domains (purchased via PorkBun)</li>
          <li><span class="ck">✓</span> 60 private email inboxes</li>
          <li><span class="ck">✓</span> Cold email sending tool</li>
          <li><span class="ck">✓</span> LeadSweeper-powered sourcing</li>
          <li><span class="ck">✓</span> 24/7 AI deliverability monitoring</li>
          <li><span class="ck">✓</span> Monthly campaign setup &amp; optimization</li>
          <li><span class="ck">✓</span> Phone enrichment on positive replies</li>
        </ul>
        <a href="#final" class="btn btn--ghost">Start with Minimum</a>
      </div>
      <div class="plan pop reveal">
        <span class="ribbon" style="background:var(--ignite);color:#1A0E03">Most popular</span>
        <div class="pname">Pro</div>
        <div class="price"><span class="amt">$5,000</span><span class="per">/mo</span></div>
        <div class="qtr">$15,000 / quarter</div>
        <ul>
          <li><span class="ck">✓</span> Up to 45,000 emails &amp; leads contacted / month</li>
          <li><span class="ck">✓</span> 45 domains (purchased via PorkBun)</li>
          <li><span class="ck">✓</span> 90 private email inboxes</li>
          <li><span class="ck">✓</span> Cold email sending tool</li>
          <li><span class="ck">✓</span> Expanded LeadSweeper sourcing</li>
          <li><span class="ck">✓</span> 24/7 AI deliverability monitoring</li>
          <li><span class="ck">✓</span> More campaign testing capacity</li>
          <li><span class="ck">✓</span> Priority campaign management</li>
        </ul>
        <a href="#final" class="btn btn--primary">Start with Pro</a>
      </div>
    </div>
    <div class="scar reveal" style="background:#FFF;border-color:rgba(255,122,26,.32)">
      <span class="ic">⚡</span>
      <p style="color:var(--t-ink)"><b style="color:#C2540A">Only 3–5 new partners onboarded per month.</b> Every account requires dedicated domain setup, inbox configuration, LeadSweeper sourcing, and private infrastructure allocation. Once this month's capacity is allocated, new partners move to the next onboarding window.</p>
    </div>
  </div>
</section>

<!-- FAQ -->
<section class="section" id="faq">
  <div class="wrap">
    <div class="reveal">
      <span class="eyebrow">Questions, answered</span>
      <div class="sectionhead"><h2>The things skeptical buyers ask</h2></div>
    </div>
    <div class="faq">
      <div class="qa reveal"><button>Are Instagram-sourced leads actually qualified for B2B?</button><div class="ans"><p>We don't email random Instagram users. Instagram is a discovery layer — a way to find visibly active businesses by niche, account, hashtag, location, and audience cluster that traditional databases flatten or miss. Those signals are then enriched, validated against your ICP, cleaned, and suppressed before any outreach. It's discovery first, validation second, sending third.</p></div></div>
      <div class="qa reveal"><button>Will these emails land in the inbox, or will we burn domains?</button><div class="ans"><p>You send from 30–45 fresh domains and 60–90 private inboxes — never your main business domain. Inboxes are warmed, rotated, and watched by 24/7 AI deliverability monitoring that flags and replaces underperformers. If deliverability issues come up, we diagnose and fix the infrastructure at no additional management fee. We don't promise a specific inbox-placement percentage — no honest provider can under current Gmail and Outlook rules — but protecting deliverability is the core of the system.</p></div></div>
      <div class="qa reveal"><button>Why use this instead of Apollo, ZoomInfo, or a VA?</button><div class="ans"><p>Apollo and ZoomInfo are broad databases — useful, but the same lists your competitors already use. This is a fresher, less-commoditized input layer plus a fully managed engine on top. A VA can run a tool; they can't build private infrastructure, source fresh data, manage deliverability, and optimize campaigns at 30K–45K sends a month. A tool isn't a system.</p></div></div>
      <div class="qa reveal"><button>Why not just hire an SDR internally?</button><div class="ans"><p>Hiring before the motion is proven means salary, manager cost, tooling, 60–90 days of ramp, and 35%+ turnover risk — realistically $11K–$16K/mo all-in — and you still have to build the system yourself. This gives you a managed outbound motion live in weeks, for a fraction of that, before you ever staff a department.</p></div></div>
      <div class="qa reveal"><button>How much work will my team still have to do?</button><div class="ans"><p>After onboarding: approve messaging and strategy, respond to interested replies, take the calls we route to you, and close. You don't manage scraping, domains, inboxes, deliverability, SmartLead, list building, or campaign operations. Those stay with us.</p></div></div>
      <div class="qa reveal"><button>How long does it take to launch — and why the 90-day commitment?</button><div class="ans"><p>Campaigns go live within the 5–8 week onboarding window. The 90-day minimum exists because cold email isn't a 30-day experiment: domain setup, inbox warmup, deliverability testing, launch, reply analysis, and optimization all need time to stabilize and produce data worth acting on. Ninety days gives the engine room to compound toward qualified conversations.</p></div></div>
      <div class="qa reveal"><button>How is this different from a typical outbound agency?</button><div class="ans"><p>Most agencies start where everyone starts — a recycled database — then compete on "better copy." We fix the input layer first with fresh Instagram-sourced data, then run private infrastructure and managed SmartLead execution around it. You get a managed engine with a defined mechanism and transparent reporting, not vanity metrics and the same lists as everyone else.</p></div></div>
    </div>
  </div>
</section>

<!-- FINAL CTA -->
<section class="section final" id="final">
  <div class="wrap">
    <div class="reveal">
      <span class="eyebrow" style="justify-content:center">Your move</span>
      <h2>Stop fighting over the<br><span class="hot">same stale leads.</span></h2>
      <p>We build and manage the data-fueled cold email engine that turns fresh Instagram-sourced business leads into qualified B2B sales conversations — without stale databases, fragile infrastructure, or manual prospecting. You approve the strategy, take the calls, and close.</p>
      <div class="hero-cta">
        <a href="#pricing" class="btn btn--primary btn--lg">Book a strategy call <span class="arr">→</span></a>
        <a href="#mechanism" class="btn btn--ghost btn--lg">See how the engine works</a>
      </div>
      <p style="font-size:14px;color:var(--t-mid);margin-top:22px">On the call we'll review your offer, map your market, and show you the exact sourcing path — then tell you honestly whether you're a fit.</p>
    </div>
  </div>
</section>

<footer>
  <div class="wrap">
    <a class="logo" href="#top"><span class="mark">L</span>LeadSuite</a>
    <p class="legal">LeadSuite builds and manages a data-fueled cold email engine for B2B agencies, SaaS, and service businesses. We guarantee buildout and execution to the agreed timeline — not closed revenue, which depends on your offer, pricing, and close rate. Sourcing uses public business signals, enriched and validated before outreach.</p>
  </div>
</footer>

<script>
  // scroll reveal
  const io = new IntersectionObserver((entries)=>{
    entries.forEach(e=>{ if(e.isIntersecting){ e.target.classList.add('in'); io.unobserve(e.target);} });
  },{threshold:0.12, rootMargin:'0px 0px -40px 0px'});
  document.querySelectorAll('.reveal').forEach(el=>io.observe(el));

  // faq accordion
  document.querySelectorAll('.qa button').forEach(btn=>{
    btn.addEventListener('click',()=>{
      const qa = btn.parentElement;
      const ans = qa.querySelector('.ans');
      const open = qa.classList.contains('open');
      document.querySelectorAll('.qa.open').forEach(o=>{ o.classList.remove('open'); o.querySelector('.ans').style.maxHeight=null; });
      if(!open){ qa.classList.add('open'); ans.style.maxHeight = ans.scrollHeight + 'px'; }
    });
  });
</script>
</body>
</html>
