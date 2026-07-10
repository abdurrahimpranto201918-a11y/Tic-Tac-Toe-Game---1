# Tic-Tac-Toe-Game-1
<!DOCTYPE html><html lang="en"><head><meta charset="UTF-8"><meta name="viewport" content="width=device-width,initial-scale=1.0"><title>Tic Tac Toe Pro</title>
<link href="https://fonts.googleapis.com/css2?family=Nunito:wght@400;600;700;800;900&display=swap" rel="stylesheet">
<style>
:root{--bg:#0f0c29;--bg2:#302b63;--bg3:#24243e;--x:#00d4ff;--o:#ff6bcb;--cb:rgba(255,255,255,0.06);--cbr:rgba(255,255,255,0.12);--t:#fff;--t2:rgba(255,255,255,0.6);--bb:rgba(255,255,255,0.1);--bh:rgba(255,255,255,0.18);--ac:#f7c948;--sh:rgba(0,0,0,0.4);--wl:#f7c948;}
.theme-classic{--bg:#f0f4ff;--bg2:#dce8ff;--bg3:#c9d8f7;--x:#2563eb;--o:#dc2626;--cb:#fff;--cbr:#cbd5e1;--t:#1e293b;--t2:#64748b;--bb:#e2e8f0;--bh:#cbd5e1;--ac:#f59e0b;--sh:rgba(0,0,0,0.15);--wl:#f59e0b;}
.theme-candy{--bg:#fff0f7;--bg2:#ffe4f0;--bg3:#ffd6e8;--x:#a855f7;--o:#ec4899;--cb:#fff;--cbr:#f9a8d4;--t:#831843;--t2:#be185d;--bb:#fce7f3;--bh:#fbcfe8;--ac:#f97316;--sh:rgba(219,39,119,.2);--wl:#f97316;}
.theme-forest{--bg:#052e16;--bg2:#14532d;--bg3:#166534;--x:#4ade80;--o:#fde047;--cb:rgba(255,255,255,.07);--cbr:rgba(74,222,128,.2);--t:#f0fdf4;--t2:rgba(240,253,244,.6);--bb:rgba(74,222,128,.15);--bh:rgba(74,222,128,.25);--ac:#fb923c;--sh:rgba(0,0,0,.5);--wl:#fde047;}
.theme-ocean{--bg:#0a192f;--bg2:#112240;--bg3:#1d3461;--x:#64ffda;--o:#f76c6c;--cb:rgba(255,255,255,.06);--cbr:rgba(100,255,218,.15);--t:#ccd6f6;--t2:rgba(204,214,246,.6);--bb:rgba(100,255,218,.1);--bh:rgba(100,255,218,.2);--ac:#ffd166;--sh:rgba(0,0,0,.5);--wl:#ffd166;}
.theme-sunset{--bg:#1a0533;--bg2:#3d0b5e;--bg3:#6b1f8a;--x:#ff9a3c;--o:#ff6b9d;--cb:rgba(255,255,255,.07);--cbr:rgba(255,154,60,.2);--t:#fff0f6;--t2:rgba(255,240,246,.6);--bb:rgba(255,154,60,.15);--bh:rgba(255,154,60,.25);--ac:#ffe66d;--sh:rgba(0,0,0,.5);--wl:#ffe66d;}
*{margin:0;padding:0;box-sizing:border-box;-webkit-tap-highlight-color:transparent;touch-action:manipulation;}
html,body{height:100%;font-family:'Nunito',sans-serif;overflow:hidden;}
body{background:linear-gradient(135deg,var(--bg),var(--bg2),var(--bg3));color:var(--t);transition:background .4s;min-height:100vh;display:flex;flex-direction:column;align-items:center;justify-content:center;}
.screen{display:none;flex-direction:column;align-items:center;justify-content:center;width:100%;max-width:440px;padding:20px;animation:fsi .35s ease;}
.screen.active{display:flex;}
@keyframes fsi{from{opacity:0;transform:translateY(20px)}to{opacity:1;transform:translateY(0)}}
.bg-symbols{position:fixed;top:0;left:0;width:100%;height:100%;pointer-events:none;overflow:hidden;z-index:0;}
.bg-sym{position:absolute;opacity:.04;font-weight:900;animation:fs linear infinite;}
@keyframes fs{0%{transform:translateY(110vh) rotate(0deg)}100%{transform:translateY(-20vh) rotate(360deg)}}
#splash{z-index:999;position:fixed;top:0;left:0;width:100%;height:100%;background:linear-gradient(135deg,#0f0c29,#302b63,#24243e);display:flex;flex-direction:column;align-items:center;justify-content:center;animation:splashOut 0.5s ease 2.6s forwards;}
@keyframes splashOut{to{opacity:0;pointer-events:none;visibility:hidden;}}
.splash-x{font-size:80px;font-weight:900;color:#00d4ff;text-shadow:0 0 40px #00d4ff,0 0 80px #00d4ff;animation:splashX 0.6s cubic-bezier(.34,1.56,.64,1) forwards;}
.splash-o{font-size:80px;font-weight:900;color:#ff6bcb;text-shadow:0 0 40px #ff6bcb,0 0 80px #ff6bcb;animation:splashO 0.6s cubic-bezier(.34,1.56,.64,1) 0.3s both;}
@keyframes splashX{from{opacity:0;transform:scale(0) rotate(-180deg)}to{opacity:1;transform:scale(1) rotate(0)}}
@keyframes splashO{from{opacity:0;transform:scale(0) rotate(180deg)}to{opacity:1;transform:scale(1) rotate(0)}}
.splash-title{font-size:22px;font-weight:900;color:#fff;letter-spacing:6px;text-transform:uppercase;animation:fadeUp .5s ease .8s both;margin-top:16px;}
.splash-bar{width:160px;height:4px;background:rgba(255,255,255,.1);border-radius:4px;margin-top:28px;animation:fadeUp .5s ease 1s both;overflow:hidden;}
.splash-progress{height:100%;background:linear-gradient(90deg,#00d4ff,#ff6bcb);animation:loadBar 1.4s ease 1s both;}
@keyframes loadBar{from{width:0}to{width:100%}}
@keyframes fadeUp{from{opacity:0;transform:translateY(16px)}to{opacity:1;transform:translateY(0)}}
#home{position:relative;z-index:1;}
.logo-wrap{text-align:center;margin-bottom:26px;}
.logo-title{font-size:44px;font-weight:900;letter-spacing:-1px;line-height:1;}
.lx{color:var(--x);text-shadow:0 0 20px var(--x),0 0 40px var(--x);}
.lo{color:var(--o);text-shadow:0 0 20px var(--o),0 0 40px var(--o);}
.logo-sub{font-size:12px;color:var(--t2);letter-spacing:4px;text-transform:uppercase;margin-top:6px;font-weight:700;}
.gems{display:flex;justify-content:center;gap:12px;margin-top:14px;}
.gem{width:10px;height:10px;border-radius:50%;animation:gp 1.5s ease-in-out infinite;}
.gem:nth-child(1){background:var(--x)}.gem:nth-child(2){background:var(--ac);animation-delay:.2s}.gem:nth-child(3){background:var(--o);animation-delay:.4s}
@keyframes gp{0%,100%{transform:scale(1);opacity:.7}50%{transform:scale(1.6);opacity:1}}
.menu-btns{display:flex;flex-direction:column;gap:12px;width:100%;}
.btn-main{background:linear-gradient(135deg,var(--x),var(--o));color:#fff;border:none;border-radius:18px;padding:18px 28px;font-size:18px;font-weight:800;cursor:pointer;width:100%;display:flex;align-items:center;justify-content:center;gap:12px;box-shadow:0 8px 24px var(--sh);transition:transform .15s,box-shadow .15s;}
.btn-main:active{transform:scale(.96)}
.btn-sec{background:var(--bb);color:var(--t);border:1.5px solid var(--cbr);border-radius:18px;padding:15px 28px;font-size:16px;font-weight:700;cursor:pointer;width:100%;display:flex;align-items:center;justify-content:center;gap:10px;transition:background .2s,transform .15s;}
.btn-sec:active{transform:scale(.96);background:var(--bh)}
.section-label{font-size:12px;color:var(--t2);font-weight:700;letter-spacing:2px;text-transform:uppercase;text-align:center;margin:18px 0 10px;}
.theme-row{display:flex;gap:8px;justify-content:center;flex-wrap:wrap;}
.tdot{width:32px;height:32px;border-radius:50%;cursor:pointer;border:3px solid transparent;transition:transform .2s,border-color .2s;box-shadow:0 4px 10px var(--sh);}
.tdot.active{border-color:var(--ac);transform:scale(1.15)}
#td-neon{background:linear-gradient(135deg,#0f0c29,#302b63)}
#td-classic{background:linear-gradient(135deg,#f0f4ff,#2563eb)}
#td-candy{background:linear-gradient(135deg,#fff0f7,#ec4899)}
#td-forest{background:linear-gradient(135deg,#052e16,#4ade80)}
#td-ocean{background:linear-gradient(135deg,#0a192f,#64ffda)}
#td-sunset{background:linear-gradient(135deg,#1a0533,#ff9a3c)}
.screen-title{font-size:26px;font-weight:800;text-align:center;margin-bottom:6px;}
.screen-sub{font-size:14px;color:var(--t2);text-align:center;margin-bottom:22px;font-weight:600;}
.back-btn{background:none;border:none;color:var(--t2);font-size:15px;font-weight:700;cursor:pointer;display:flex;align-items:center;gap:6px;margin-bottom:16px;padding:6px 0;}
.opt-group{background:var(--bb);border:1.5px solid var(--cbr);border-radius:18px;padding:16px;width:100%;margin-bottom:12px;}
.opt-row{display:flex;align-items:center;justify-content:space-between;padding:8px 0;}
.opt-row+.opt-row{border-top:1px solid var(--cbr)}
.opt-label{font-size:14px;font-weight:700;color:var(--t)}
.seg{display:flex;gap:4px;}
.seg-btn{background:none;border:1.5px solid var(--cbr);border-radius:10px;padding:5px 11px;font-size:13px;font-weight:700;cursor:pointer;color:var(--t2);transition:all .2s;}
.seg-btn.active{background:linear-gradient(135deg,var(--x),var(--o));color:#fff;border-color:transparent;}
input.name-inp{background:var(--bb);border:1.5px solid var(--cbr);border-radius:10px;padding:7px 12px;font-size:14px;font-weight:700;color:var(--t);font-family:'Nunito',sans-serif;width:130px;outline:none;transition:border-color .2s;}
input.name-inp:focus{border-color:var(--ac)}
.diff-btns{display:flex;flex-direction:column;gap:10px;width:100%;}
.diff-btn{border:none;border-radius:16px;padding:18px 24px;font-size:16px;font-weight:800;cursor:pointer;display:flex;align-items:center;gap:14px;transition:transform .15s,box-shadow .15s;box-shadow:0 6px 18px var(--sh);}
.diff-btn:active{transform:scale(.96)}
.diff-easy{background:linear-gradient(135deg,#22c55e,#16a34a);color:#fff}
.diff-medium{background:linear-gradient(135deg,#f59e0b,#d97706);color:#fff}
.diff-hard{background:linear-gradient(135deg,#ef4444,#b91c1c);color:#fff}
.diff-info{display:flex;flex-direction:column;text-align:left}
.diff-name{font-size:18px;font-weight:800}
.diff-desc{font-size:12px;opacity:.85;font-weight:600;margin-top:2px}
.diff-icon{font-size:28px}
#game{position:relative;z-index:1;width:100%;max-width:440px;padding:12px 16px;}
.game-header{display:flex;align-items:center;justify-content:space-between;margin-bottom:14px;gap:6px;}
.hbtn{background:var(--bb);border:1.5px solid var(--cbr);border-radius:12px;color:var(--t);padding:7px 12px;font-size:13px;font-weight:700;cursor:pointer;transition:background .2s;white-space:nowrap;}
.hbtn:active{background:var(--bh)}
.exit-btn{background:linear-gradient(135deg,rgba(239,68,68,.2),rgba(185,28,28,.2)) !important;border-color:rgba(239,68,68,.4) !important;color:#ef4444 !important;}
.mode-lbl{font-size:12px;color:var(--t2);font-weight:700;letter-spacing:.5px;}
.score-panel{display:grid;grid-template-columns:1fr auto 1fr;gap:8px;margin-bottom:14px;}
.scard{background:var(--bb);border:1.5px solid var(--cbr);border-radius:16px;padding:11px 8px;text-align:center;transition:transform .2s,box-shadow .2s;}
.scard.at{transform:scale(1.04);border-color:var(--ac);box-shadow:0 0 16px rgba(247,201,72,.3)}
.scard.xc .ss{color:var(--x)}.scard.oc .ss{color:var(--o)}
.ss{font-size:20px;font-weight:900;display:block}.sl{font-size:10px;color:var(--t2);font-weight:700;text-transform:uppercase;letter-spacing:.5px;margin-top:2px}.sc{font-size:20px;font-weight:900;margin-top:2px}
.draw-card{display:flex;flex-direction:column;align-items:center;justify-content:center;}
.turn-ind{text-align:center;margin-bottom:12px;font-size:15px;font-weight:700;height:28px;}
.tx{color:var(--x)}.to{color:var(--o)}
.tp{animation:tp .5s ease}
@keyframes tp{0%{transform:scale(1)}50%{transform:scale(1.15)}100%{transform:scale(1)}}
.timer-bar{width:100%;height:5px;background:var(--cbr);border-radius:5px;margin-bottom:12px;overflow:hidden;display:none;}
.timer-fill{height:100%;background:linear-gradient(90deg,var(--x),var(--o));border-radius:5px;transition:width 1s linear;}
.board-wrap{position:relative;width:100%;aspect-ratio:1;margin-bottom:14px;}
.board{display:grid;grid-template-columns:repeat(3,1fr);gap:10px;width:100%;height:100%;}
.cell{background:var(--cb);border:1.5px solid var(--cbr);border-radius:20px;cursor:pointer;display:flex;align-items:center;justify-content:center;aspect-ratio:1;transition:background .2s,transform .1s;position:relative;overflow:hidden;}
.cell:hover:not(.taken){background:rgba(255,255,255,.12);border-color:rgba(255,255,255,.25)}
.cell:active:not(.taken){transform:scale(.93)}
.cell.taken{cursor:default}
.cell.winning{border-color:var(--wl);background:rgba(247,201,72,.1);box-shadow:0 0 20px rgba(247,201,72,.25)}
.cell svg{width:55%;height:55%;overflow:visible}
.xp{stroke:var(--x);stroke-width:8;stroke-linecap:round;fill:none;stroke-dasharray:100;stroke-dashoffset:100;animation:ds .35s ease forwards}
.xp:nth-child(2){animation-delay:.1s}
.op{stroke:var(--o);stroke-width:8;stroke-linecap:round;fill:none;stroke-dasharray:280;stroke-dashoffset:280;animation:ds .45s ease forwards}
@keyframes ds{to{stroke-dashoffset:0}}
.wls{position:absolute;top:0;left:0;width:100%;height:100%;pointer-events:none;z-index:5}
.wlp{stroke:var(--wl);stroke-width:6;stroke-linecap:round;fill:none;opacity:.8;stroke-dasharray:600;stroke-dashoffset:600;animation:dwl .5s ease .2s forwards}
@keyframes dwl{to{stroke-dashoffset:0}}
.game-controls{display:flex;gap:8px;}
.rbtn{flex:1;background:linear-gradient(135deg,var(--x),var(--o));color:#fff;border:none;border-radius:16px;padding:15px;font-size:15px;font-weight:800;cursor:pointer;transition:transform .15s;}
.rbtn:active{transform:scale(.96)}
.ubtn{background:var(--bb);border:1.5px solid var(--cbr);border-radius:16px;padding:15px 16px;font-size:18px;cursor:pointer;transition:background .2s;}
.ubtn:active{background:var(--bh)}
#win-overlay{display:none;position:fixed;top:0;left:0;width:100%;height:100%;background:rgba(0,0,0,.7);z-index:100;align-items:center;justify-content:center;backdrop-filter:blur(6px);}
#win-overlay.show{display:flex;animation:fi .3s ease}
@keyframes fi{from{opacity:0}to{opacity:1}}
.win-card{background:linear-gradient(135deg,var(--bg2),var(--bg3));border:1.5px solid var(--cbr);border-radius:28px;padding:32px 24px;text-align:center;max-width:320px;width:90%;box-shadow:0 20px 60px rgba(0,0,0,.5);animation:pi .4s cubic-bezier(.34,1.56,.64,1)}
@keyframes pi{from{opacity:0;transform:scale(.7)}to{opacity:1;transform:scale(1)}}
.we{font-size:60px;display:block;margin-bottom:10px;animation:wig .6s ease .3s}
@keyframes wig{0%,100%{transform:rotate(0)}25%{transform:rotate(-15deg)}75%{transform:rotate(15deg)}}
.wt{font-size:28px;font-weight:900;margin-bottom:6px}
.wt.xw{color:var(--x);text-shadow:0 0 20px var(--x)}.wt.ow{color:var(--o);text-shadow:0 0 20px var(--o)}.wt.dr{color:var(--ac);text-shadow:0 0 20px var(--ac)}
.ws{font-size:14px;color:var(--t2);margin-bottom:20px;font-weight:600}
.win-acts{display:flex;flex-direction:column;gap:8px}
.bpa{background:linear-gradient(135deg,var(--x),var(--o));color:#fff;border:none;border-radius:16px;padding:15px;font-size:16px;font-weight:800;cursor:pointer;transition:transform .15s}
.bpa:active{transform:scale(.96)}
.bho{background:var(--bb);color:var(--t);border:1.5px solid var(--cbr);border-radius:16px;padding:13px;font-size:15px;font-weight:700;cursor:pointer;transition:background .2s}
.bho:active{background:var(--bh)}
.score-reset{background:none;border:none;color:var(--t2);font-size:11px;font-weight:700;cursor:pointer;text-decoration:underline;padding:3px;margin-top:2px;}
.conf-container{position:fixed;top:0;left:0;width:100%;height:100%;pointer-events:none;z-index:200;overflow:hidden}
.conf{position:absolute;top:-10px;border-radius:3px;animation:cf linear forwards}
@keyframes cf{to{transform:translateY(110vh) rotate(720deg);opacity:0}}
.thinking{display:none;position:fixed;bottom:20px;left:50%;transform:translateX(-50%);background:rgba(0,0,0,.75);color:#fff;padding:10px 20px;border-radius:20px;font-size:13px;font-weight:700;z-index:50;backdrop-filter:blur(4px);}
.thinking.show{display:block;animation:fi .2s ease}
.td span{animation:bl 1s infinite}
.td span:nth-child(2){animation-delay:.2s}.td span:nth-child(3){animation-delay:.4s}
@keyframes bl{0%,100%{opacity:.2}50%{opacity:1}}
.exit-confirm{display:none;position:fixed;top:0;left:0;width:100%;height:100%;background:rgba(0,0,0,.75);z-index:150;align-items:center;justify-content:center;backdrop-filter:blur(4px);}
.exit-confirm.show{display:flex;animation:fi .2s ease}
.exit-card{background:linear-gradient(135deg,var(--bg2),var(--bg3));border:1.5px solid var(--cbr);border-radius:24px;padding:28px 24px;text-align:center;max-width:300px;width:90%;}
.exit-card h3{font-size:22px;font-weight:800;margin-bottom:8px}
.exit-card p{font-size:14px;color:var(--t2);font-weight:600;margin-bottom:20px}
.exit-btns{display:flex;gap:10px}
.exit-btns button{flex:1;border:none;border-radius:14px;padding:14px;font-size:15px;font-weight:800;cursor:pointer}
.exit-yes{background:linear-gradient(135deg,#ef4444,#b91c1c);color:#fff}
</style></head><body>
<div id="splash"><div class="splash-x">X</div><div class="splash-o">O</div><div class="splash-title">Tic Tac Toe</div><div class="splash-bar"><div class="splash-progress"></div></div></div>
<div class="bg-symbols" id="bgS"></div>
<div class="screen active" id="home">
  <div class="logo-wrap">
    <div class="logo-title"><span class="lx">X</span><span style="opacity:.4"> &middot; </span><span class="lo">O</span></div>
    <div style="font-size:26px;font-weight:900;margin-top:4px">TIC TAC TOE</div>
    <div class="logo-sub">Pro Edition</div>
    <div class="gems"><div class="gem"></div><div class="gem"></div><div class="gem"></div></div>
  </div>
  <div class="menu-btns">
    <button class="btn-main" onclick="goToDiff()"><span style="font-size:22px">&#x1F916;</span><span>Play vs Computer</span></button>
    <button class="btn-sec" onclick="goToOpts('2p')"><span style="font-size:22px">&#x1F465;</span><span>2 Players &mdash; Local</span></button>
    <button class="btn-sec" onclick="showScreen('howto')"><span style="font-size:22px">&#x2753;</span><span>How to Play</span></button>
  </div>
  <div class="section-label">Choose Theme</div>
  <div class="theme-row">
    <div class="tdot active" id="td-neon" onclick="setTheme('neon',this)" title="Neon"></div>
    <div class="tdot" id="td-classic" onclick="setTheme('classic',this)" title="Classic"></div>
    <div class="tdot" id="td-candy" onclick="setTheme('candy',this)" title="Candy"></div>
    <div class="tdot" id="td-forest" onclick="setTheme('forest',this)" title="Forest"></div>
    <div class="tdot" id="td-ocean" onclick="setTheme('ocean',this)" title="Ocean"></div>
    <div class="tdot" id="td-sunset" onclick="setTheme('sunset',this)" title="Sunset"></div>
  </div>
</div>
<div class="screen" id="opts">
  <button class="back-btn" onclick="showScreen('home')">&#8592; Back</button>
  <div class="screen-title">Game Options</div>
  <div class="screen-sub">Customize your game</div>
  <div class="opt-group" id="nameGroup">
    <div class="opt-row"><span class="opt-label">&#x270F; Player 1 (X)</span><input class="name-inp" id="p1name" value="Player 1" maxlength="10"></div>
    <div class="opt-row"><span class="opt-label">&#x270F; Player 2 (O)</span><input class="name-inp" id="p2name" value="Player 2" maxlength="10"></div>
  </div>
  <div class="opt-group">
    <div class="opt-row"><span class="opt-label">&#x1F3AF; First Move</span><div class="seg"><button class="seg-btn active" id="fp-x" onclick="setFirst('X')">X</button><button class="seg-btn" id="fp-o" onclick="setFirst('O')">O</button><button class="seg-btn" id="fp-r" onclick="setFirst('R')">Random</button></div></div>
    <div class="opt-row"><span class="opt-label">&#x23F1; Timer</span><div class="seg"><button class="seg-btn active" id="tm-off" onclick="setTimer(0)">Off</button><button class="seg-btn" id="tm-15" onclick="setTimer(15)">15s</button><button class="seg-btn" id="tm-30" onclick="setTimer(30)">30s</button></div></div>
  </div>
  <button class="btn-main" style="margin-top:12px" onclick="startGame()">&#x25B6; Start Game</button>
</div>
<div class="screen" id="difficulty">
  <button class="back-btn" onclick="showScreen('home')">&#8592; Back</button>
  <div class="screen-title">Choose Difficulty</div>
  <div class="screen-sub">How smart should the AI be?</div>
  <div class="diff-btns">
    <button class="diff-btn diff-easy" onclick="goToOpts('ai','easy')"><span class="diff-icon">&#x1F60A;</span><div class="diff-info"><span class="diff-name">Easy</span><span class="diff-desc">Perfect for beginners &amp; kids</span></div></button>
    <button class="diff-btn diff-medium" onclick="goToOpts('ai','medium')"><span class="diff-icon">&#x1F914;</span><div class="diff-info"><span class="diff-name">Medium</span><span class="diff-desc">Blocks your moves, tries to win</span></div></button>
    <button class="diff-btn diff-hard" onclick="goToOpts('ai','hard')"><span class="diff-icon">&#x1F525;</span><div class="diff-info"><span class="diff-name">Hard &mdash; Unbeatable</span><span class="diff-desc">Minimax AI &mdash; challenge yourself!</span></div></button>
  </div>
</div>
<div class="screen" id="howto">
  <button class="back-btn" onclick="showScreen('home')">&#8592; Back</button>
  <div class="screen-title">How to Play</div>
  <div class="opt-group" style="width:100%">
    <div style="font-size:14px;font-weight:600;color:var(--t2);line-height:2;">
      &#x1F3AF; <b>Goal:</b> Get 3 in a row &mdash; horizontal, vertical, or diagonal.<br>
      &#x1F504; <b>Turns:</b> X always goes first (unless changed in Options).<br>
      &#x1F3C6; <b>Win:</b> First to get 3 in a row wins!<br>
      &#x1F91D; <b>Draw:</b> All 9 cells filled with no winner.<br>
      &#x21A9; <b>Undo:</b> In 2P mode, undo your last move.<br>
      &#x23F1; <b>Timer:</b> Each player has limited time per move.
    </div>
  </div>
  <button class="btn-main" style="margin-top:12px" onclick="showScreen('home')">&#x1F44D; Got It!</button>
</div>
<div class="screen" id="game">
  <div class="game-header">
    <button class="hbtn" onclick="showExitConfirm()">&#8592; Menu</button>
    <span class="mode-lbl" id="modeLbl">VS COMPUTER</span>
    <div style="display:flex;gap:6px">
      <button class="hbtn" id="soundBtn" onclick="toggleSound()">&#x1F50A;</button>
      <button class="hbtn exit-btn" onclick="showExitConfirm()">&#x2715; Exit</button>
    </div>
  </div>
  <div class="score-panel">
    <div class="scard xc at" id="xCard"><span class="ss" id="xLbl">X</span><span class="sl" id="xNm">Player</span><span class="sc" id="xSc">0</span></div>
    <div class="scard draw-card" style="background:var(--bb);border:1.5px solid var(--cbr);border-radius:16px;padding:11px 8px;"><span style="font-size:10px;color:var(--t2);font-weight:700;text-transform:uppercase;letter-spacing:.5px">Draw</span><span class="sc" id="drSc">0</span><button class="score-reset" onclick="resetScores()">reset</button></div>
    <div class="scard oc" id="oCard"><span class="ss" id="oLbl">O</span><span class="sl" id="oNm">Computer</span><span class="sc" id="oSc">0</span></div>
  </div>
  <div class="timer-bar" id="timerBar"><div class="timer-fill" id="timerFill"></div></div>
  <div class="turn-ind" id="turnInd"><span class="tx">X's Turn</span></div>
  <div class="board-wrap"><div class="board" id="board"></div><svg class="wls" id="wlSvg" viewBox="0 0 300 300" style="display:none"></svg></div>
  <div class="game-controls">
    <button class="ubtn" id="undoBtn" onclick="undoMove()" title="Undo">&#x21A9;</button>
    <button class="rbtn" onclick="restartGame()">&#x1F504; New Round</button>
  </div>
</div>
<div id="win-overlay">
  <div class="win-card">
    <span class="we" id="winEmoji">&#x1F389;</span>
    <div class="wt" id="winTitle">X Wins!</div>
    <div class="ws" id="winSub">Amazing!</div>
    <div class="win-acts">
      <button class="bpa" onclick="restartGame();closeOverlay()">&#x1F504; Play Again</button>
      <button class="bho" onclick="goHome()">&#x1F3E0; Main Menu</button>
    </div>
  </div>
</div>
<div class="exit-confirm" id="exitConfirm">
  <div class="exit-card">
    <h3>&#x2715; Exit Game?</h3>
    <p>Your current game progress will be lost.</p>
    <div class="exit-btns">
      <button class="exit-yes" onclick="goHome()">Yes, Exit</button>
      <button class="bho" style="flex:1" onclick="hideExitConfirm()">Keep Playing</button>
    </div>
  </div>
</div>
<div class="conf-container" id="confC"></div>
<div class="thinking" id="thinkEl">&#x1F916; AI thinking<span class="td"><span>.</span><span>.</span><span>.</span></span></div>
<script>
var E={
  robot:'\uD83E\uDD16',party:'\uD83C\uDF89',devil:'\uD83D\uDE08',handshake:'\uD83E\uDD1D',
  sound:'\uD83D\uDD0A',mute:'\uD83D\uDD07',fire:'\uD83D\uDD25',trophy:'\uD83C\uDFC6',
  target:'\uD83C\uDFAF',muscle:'\uD83D\uDCAA',bolt:'\u26A1',brain:'\uD83E\uDDE0',
  pc:'\uD83D\uDCBB',champ:'\uD83C\uDFC6'
};
let board=Array(9).fill(''),cur='X',mode='ai',diff='hard',over=false;
let scores={X:0,O:0,draw:0},soundOn=true,aiTimer=null;
let firstPlayer='X',timerSec=0,timerLeft=0,timerInterval=null;
let history=[],optMode='ai';
const WC=[[0,1,2],[3,4,5],[6,7,8],[0,3,6],[1,4,7],[2,5,8],[0,4,8],[2,4,6]];
let actx=null;
function ga(){if(!actx)actx=new(window.AudioContext||window.webkitAudioContext)();return actx;}
function tone(f,d,t,v,delay){
  t=t||'sine';v=v||0.3;delay=delay||0;
  if(!soundOn)return;
  try{const c=ga(),o=c.createOscillator(),g=c.createGain();
  o.connect(g);g.connect(c.destination);
  o.type=t;o.frequency.setValueAtTime(f,c.currentTime+delay);
  g.gain.setValueAtTime(0,c.currentTime+delay);
  g.gain.linearRampToValueAtTime(v,c.currentTime+delay+0.01);
  g.gain.exponentialRampToValueAtTime(0.001,c.currentTime+delay+d);
  o.start(c.currentTime+delay);o.stop(c.currentTime+delay+d);}catch(e){}}
function playPlace(p){if(p==='X'){tone(523,0.12,'triangle',0.2);tone(659,0.08,'sine',0.1,0.08);}else{tone(392,0.12,'triangle',0.2);tone(523,0.08,'sine',0.1,0.08);}}
function playWin(){[[523,0],[659,.1],[784,.2],[1047,.3],[1319,.45]].forEach(function(a){tone(a[0],0.25,'sine',0.25,a[1]);});}
function playDraw(){tone(400,.15,'sawtooth',.15);tone(350,.15,'sawtooth',.15,.18);tone(300,.3,'sawtooth',.15,.36);}
function playClick(){tone(700,.06,'sine',.12);}
function playUndo(){tone(300,.1,'triangle',.15);tone(250,.1,'triangle',.12,.1);}
function playTimeWarn(){tone(440,.08,'square',.1);tone(330,.08,'square',.08,.12);}
function setTheme(n,el){
  document.querySelectorAll('.tdot').forEach(function(d){d.classList.remove('active');});
  if(el)el.classList.add('active');
  var b=document.body;
  b.className=b.className.replace(/theme-\w+/g,'').trim();
  if(n!=='neon')b.classList.add('theme-'+n);
  playClick();}
function makeBg(){
  var c=document.getElementById('bgS');c.innerHTML='';
  var s=['X','O','\u00D7','\u25CB'];
  for(var i=0;i<14;i++){
    var d=document.createElement('div');d.className='bg-sym';
    d.textContent=s[i%4];d.style.left=Math.random()*90+'%';
    d.style.animationDuration=(15+Math.random()*20)+'s';
    d.style.animationDelay=(-Math.random()*20)+'s';
    d.style.fontSize=(30+Math.random()*50)+'px';c.appendChild(d);}}
function showScreen(id){document.querySelectorAll('.screen').forEach(function(s){s.classList.remove('active');});document.getElementById(id).classList.add('active');}
function goToDiff(){playClick();showScreen('difficulty');}
var _optFirstP='X',_optTimer=0;
function goToOpts(m,d){
  playClick();optMode=m;if(d)diff=d;
  var ng=document.getElementById('nameGroup');
  ng.style.display=m==='2p'?'':'none';
  showScreen('opts');}
function setFirst(v){_optFirstP=v;['x','o','r'].forEach(function(k){document.getElementById('fp-'+k).classList.remove('active');});document.getElementById('fp-'+v.toLowerCase()).classList.add('active');playClick();}
function setTimer(v){_optTimer=v;document.getElementById('tm-off').classList.remove('active');document.getElementById('tm-15').classList.remove('active');document.getElementById('tm-30').classList.remove('active');document.getElementById(v===0?'tm-off':v===15?'tm-15':'tm-30').classList.add('active');playClick();}
function startGame(){
  playClick();mode=optMode;timerSec=_optTimer;
  var p1=document.getElementById('p1name').value.trim()||'Player 1';
  var p2=document.getElementById('p2name').value.trim()||'Player 2';
  scores={X:0,O:0,draw:0};updateScoreUI();
  if(mode==='2p'){document.getElementById('xNm').textContent=p1;document.getElementById('oNm').textContent=p2;document.getElementById('modeLbl').textContent='2 PLAYERS';}
  else{document.getElementById('xNm').textContent='You';document.getElementById('oNm').textContent='AI \u00B7 '+diff[0].toUpperCase()+diff.slice(1);document.getElementById('modeLbl').textContent='VS AI \u2014 '+diff.toUpperCase();}
  document.getElementById('undoBtn').style.display=mode==='2p'?'':'none';
  showScreen('game');resetBoard();}
function resetBoard(){
  board=Array(9).fill('');history=[];over=false;
  cur=_optFirstP==='R'?(Math.random()<.5?'X':'O'):_optFirstP;
  clearTimeout(aiTimer);clearInterval(timerInterval);
  document.getElementById('thinkEl').classList.remove('show');
  document.getElementById('wlSvg').style.display='none';document.getElementById('wlSvg').innerHTML='';
  document.getElementById('timerBar').style.display=timerSec>0?'block':'none';
  renderBoard();updateTurnUI();
  if(timerSec>0)startTimer();
  if(mode==='ai'&&cur==='O'&&!over)aiThink();}
function restartGame(){closeOverlay();resetBoard();playClick();}
function goHome(){playClick();closeOverlay();hideExitConfirm();showScreen('home');}
function showExitConfirm(){playClick();document.getElementById('exitConfirm').classList.add('show');}
function hideExitConfirm(){document.getElementById('exitConfirm').classList.remove('show');}
function resetScores(){scores={X:0,O:0,draw:0};updateScoreUI();playClick();}
function startTimer(){
  timerLeft=timerSec;updateTimerBar();clearInterval(timerInterval);
  timerInterval=setInterval(function(){
    if(over){clearInterval(timerInterval);return;}
    timerLeft--;updateTimerBar();
    if(timerLeft<=3&&timerLeft>0)playTimeWarn();
    if(timerLeft<=0){clearInterval(timerInterval);handleTimeOut();}},1000);}
function updateTimerBar(){
  var pct=timerLeft/timerSec*100;
  var f=document.getElementById('timerFill');
  f.style.width=pct+'%';
  f.style.background=pct>50?'linear-gradient(90deg,var(--x),var(--o))':pct>20?'linear-gradient(90deg,#f59e0b,#f97316)':'linear-gradient(90deg,#ef4444,#b91c1c)';}
function handleTimeOut(){if(over)return;var winner=cur==='X'?'O':'X';scores[winner]++;playWin();updateScoreUI();showOverlay('win',winner,true);}
function renderBoard(){
  var b=document.getElementById('board');b.innerHTML='';
  board.forEach(function(v,i){
    var c=document.createElement('div');c.className='cell'+(v?' taken':'');
    if(v)c.innerHTML=v==='X'?mkX():mkO();
    else{(function(idx){c.addEventListener('click',function(){handleClick(idx);});})(i);}
    b.appendChild(c);});}
function mkX(){return'<svg viewBox="0 0 100 100"><line class="xp" x1="20" y1="20" x2="80" y2="80"/><line class="xp" x1="80" y1="20" x2="20" y2="80"/></svg>';}
function mkO(){return'<svg viewBox="0 0 100 100"><circle class="op" cx="50" cy="50" r="32"/></svg>';}
function handleClick(i){if(over||board[i])return;if(mode==='ai'&&cur==='O')return;makeMove(i);}
function makeMove(i){
  history.push({board:board.slice(),cur:cur,timerLeft:timerLeft});
  board[i]=cur;
  var cells=document.querySelectorAll('.cell');
  cells[i].classList.add('taken');cells[i].innerHTML=cur==='X'?mkX():mkO();
  playPlace(cur);clearInterval(timerInterval);
  var res=checkResult();
  if(res){handleResult(res);return;}
  cur=cur==='X'?'O':'X';updateTurnUI();
  if(timerSec>0)startTimer();
  if(mode==='ai'&&cur==='O'&&!over)aiThink();}
function undoMove(){
  if(!history.length||over)return;
  if(mode==='ai'&&history.length>=2){history.splice(history.length-2,2);}
  else if(mode==='ai')return;
  else history.pop();
  var snap=history[history.length-1];
  if(snap){board=snap.board.slice();cur=snap.cur;timerLeft=snap.timerLeft;}
  else{board=Array(9).fill('');cur=_optFirstP==='R'?cur:_optFirstP;}
  over=false;clearInterval(timerInterval);clearTimeout(aiTimer);
  document.getElementById('wlSvg').style.display='none';document.getElementById('wlSvg').innerHTML='';
  renderBoard();updateTurnUI();playUndo();
  if(timerSec>0)startTimer();}
function checkResult(){
  for(var i=0;i<WC.length;i++){var w=WC[i];if(board[w[0]]&&board[w[0]]===board[w[1]]&&board[w[0]]===board[w[2]])return{winner:board[w[0]],combo:w};}
  if(board.every(function(v){return v;}))return{winner:'draw'};return null;}
function handleResult(res){
  over=true;clearInterval(timerInterval);
  document.getElementById('thinkEl').classList.remove('show');
  if(res.winner==='draw'){scores.draw++;playDraw();showOverlay('draw',null);}
  else{scores[res.winner]++;playWin();highlightWin(res.combo);drawLine(res.combo);setTimeout(function(){showOverlay('win',res.winner);},600);}
  updateScoreUI();}
function highlightWin(c){var cs=document.querySelectorAll('.cell');c.forEach(function(i){cs[i].classList.add('winning');});}
function drawLine(combo){
  var svg=document.getElementById('wlSvg');svg.style.display='block';
  function cc(i){return{x:(i%3)*100+50,y:Math.floor(i/3)*100+50};}
  var s=cc(combo[0]),e=cc(combo[2]);
  var dx=e.x-s.x,dy=e.y-s.y,len=Math.sqrt(dx*dx+dy*dy),ext=35;
  svg.innerHTML='<line class="wlp" x1="'+(s.x-(dx/len)*ext)+'" y1="'+(s.y-(dy/len)*ext)+'" x2="'+(e.x+(dx/len)*ext)+'" y2="'+(e.y+(dy/len)*ext)+'"/>';}
function aiThink(){
  var t=diff==='easy'?400:diff==='medium'?600:750;
  document.getElementById('thinkEl').classList.add('show');
  aiTimer=setTimeout(function(){
    document.getElementById('thinkEl').classList.remove('show');
    if(!over){var m=getMove();if(m!==-1)makeMove(m);}},t);}
function getMove(){return diff==='easy'?easyMove():diff==='medium'?medMove():hardMove();}
function easyMove(){var e=board.map(function(v,i){return v?-1:i;}).filter(function(v){return v!==-1;});return Math.random()<.35?medMove():e[Math.floor(Math.random()*e.length)];}
function medMove(){
  var w=findWin('O');if(w!==-1)return w;
  var bl=findWin('X');if(bl!==-1)return bl;
  if(!board[4])return 4;
  var c=[0,2,6,8].filter(function(i){return!board[i];});if(c.length)return c[Math.floor(Math.random()*c.length)];
  var e=board.map(function(v,i){return v?-1:i;}).filter(function(v){return v!==-1;});return e.length?e[Math.floor(Math.random()*e.length)]:-1;}
function findWin(p){
  var op=p==='X'?'O':'X';
  for(var i=0;i<WC.length;i++){var w=WC[i];var l=[board[w[0]],board[w[1]],board[w[2]]];if(l.filter(function(v){return v===p;}).length===2&&l.indexOf(op)===-1){for(var j=0;j<3;j++){if(!board[w[j]])return w[j];}}}return -1;}
function hardMove(){var best=-Infinity,bm=-1;for(var i=0;i<9;i++){if(!board[i]){board[i]='O';var s=mm(board,0,false,-Infinity,Infinity);board[i]='';if(s>best){best=s;bm=i;}}}return bm;}
function mm(b,d,isMax,a,be){
  var r=cr(b);if(r==='O')return 10-d;if(r==='X')return d-10;if(r==='draw')return 0;
  if(isMax){var best=-Infinity;for(var i=0;i<9;i++){if(!b[i]){b[i]='O';best=Math.max(best,mm(b,d+1,false,a,be));b[i]='';a=Math.max(a,best);if(be<=a)break;}}return best;}
  else{var best2=Infinity;for(var i=0;i<9;i++){if(!b[i]){b[i]='X';best2=Math.min(best2,mm(b,d+1,true,a,be));b[i]='';be=Math.min(be,best2);if(be<=a)break;}}return best2;}}
function cr(b){for(var i=0;i<WC.length;i++){var w=WC[i];if(b[w[0]]&&b[w[0]]===b[w[1]]&&b[w[0]]===b[w[2]])return b[w[0]];}if(b.every(function(v){return v;}))return 'draw';return null;}
function updateTurnUI(){
  var ti=document.getElementById('turnInd');if(over){ti.innerHTML='';return;}
  var nm=mode==='2p'?(cur==='X'?document.getElementById('xNm').textContent:document.getElementById('oNm').textContent):(cur==='X'?'Your Turn':'AI is thinking...');
  ti.innerHTML='<span class="'+(cur==='X'?'tx':'to')+' tp">'+cur+' \u00B7 '+nm+'</span>';
  document.getElementById('xCard').classList.toggle('at',cur==='X');
  document.getElementById('oCard').classList.toggle('at',cur==='O');}
function updateScoreUI(){document.getElementById('xSc').textContent=scores.X;document.getElementById('oSc').textContent=scores.O;document.getElementById('drSc').textContent=scores.draw;}
var wm={xw:[E.target+' Brilliant!',E.muscle+' You crushed it!',E.bolt+' Masterful!',E.trophy+' Outstanding!'],ow:[E.robot+' AI wins!',E.pc+' Machine triumphs!',E.fire+' Tough luck!',E.brain+' AI too smart!'],ow2:[E.party+' Player 2 wins!',E.trophy+' O victorious!',E.bolt+' Amazing P2!'],dr:[E.handshake+" It's a Draw!",'Nobody wins!','Perfect balance!','So evenly matched!']};
function rnd(a){return a[Math.floor(Math.random()*a.length)];}
function showOverlay(type,winner,timeout){
  var te=document.getElementById('winTitle'),se=document.getElementById('winSub'),ee=document.getElementById('winEmoji');
  if(type==='draw'){te.textContent="It's a Draw!";te.className='wt dr';ee.textContent=E.handshake;se.textContent=rnd(wm.dr);}
  else{var ix=winner==='X';te.className='wt '+(ix?'xw':'ow');ee.textContent=ix?E.party:E.devil;
    if(ix){te.textContent=mode==='2p'?'Player 1 Wins!':timeout?'You Win! (Time)':'You Win!';se.textContent=rnd(wm.xw);}
    else{te.textContent=mode==='2p'?'Player 2 Wins!':timeout?'AI Wins! (Time)':'AI Wins!';se.textContent=rnd(mode==='2p'?wm.ow2:wm.ow);}}
  document.getElementById('win-overlay').classList.add('show');
  if(type!=='draw')spawnConf();}
function closeOverlay(){document.getElementById('win-overlay').classList.remove('show');}
function spawnConf(){
  var c=document.getElementById('confC');
  var cols=['#00d4ff','#ff6bcb','#f7c948','#4ade80','#fb923c','#a855f7','#ffffff','#ffd166'];
  for(var i=0;i<60;i++){
    var el=document.createElement('div');el.className='conf';
    var col=cols[Math.floor(Math.random()*cols.length)],sz=5+Math.random()*9;
    el.style.cssText='left:'+Math.random()*100+'%;width:'+sz+'px;height:'+sz+'px;background:'+col+';animation-duration:'+(1.2+Math.random()*1.5)+'s;animation-delay:'+Math.random()*.6+'s;transform:rotate('+Math.random()*360+'deg);'+(Math.random()>.5?'border-radius:50%':'');
    c.appendChild(el);setTimeout(function(){el.remove();},3200);}}
function toggleSound(){soundOn=!soundOn;document.getElementById('soundBtn').textContent=soundOn?E.sound:E.mute;if(soundOn)playClick();}
makeBg();
document.getElementById('p1name').addEventListener('focus',function(){this.select();});
document.getElementById('p2name').addEventListener('focus',function(){this.select();});
</script></body></html>
