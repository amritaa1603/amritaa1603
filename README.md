<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>amritaa1603</title>
<style>
  @import url('https://fonts.googleapis.com/css2?family=Space+Mono:wght@400;700&family=VT323&display=swap');

  :root{
    --bg:#050805;
    --panel:#0a120a;
    --line:#1d3a1d;
    --green:#3ef23e;
    --green-dim:#1f8c1f;
    --green-bright:#8dffb0;
  }
  *{box-sizing:border-box;}
  body{
    margin:0;
    background:#000;
    font-family:'Space Mono', monospace;
    display:flex;
    justify-content:center;
    align-items:center;
    min-height:100vh;
    padding:24px;
  }

  .browser{
    width:520px;
    max-width:100%;
    border:1px solid var(--line);
    border-radius:6px;
    overflow:hidden;
    box-shadow:0 0 40px rgba(62,242,62,0.08);
    background:var(--bg);
  }

  .titlebar{
    display:flex;
    align-items:center;
    gap:10px;
    padding:8px 10px;
    background:#0c140c;
    border-bottom:1px solid var(--line);
  }
  .dots{display:flex;gap:6px;}
  .dot{width:10px;height:10px;border-radius:50%;background:#274d27;}
  .addr{
    flex:1;
    background:#050805;
    border:1px solid var(--line);
    border-radius:4px;
    padding:4px 8px;
    color:var(--green-dim);
    font-size:11px;
    letter-spacing:.5px;
  }
  .search{
    background:#050805;
    border:1px solid var(--line);
    border-radius:4px;
    padding:4px 8px;
    color:var(--green-dim);
    font-size:11px;
  }

  .stage{position:relative;}
  canvas#rain{
    position:absolute;
    inset:0;
    opacity:.55;
  }

  .content{position:relative;z-index:2;padding:14px;}

  .top{display:grid;grid-template-columns:100px 1fr;gap:14px;}
  .avatar{
    width:100px;height:100px;
    border:1px solid var(--line);
    background:repeating-linear-gradient(45deg,#0a120a,#0a120a 6px,#0f1d0f 6px,#0f1d0f 12px);
    display:flex;align-items:center;justify-content:center;
    color:var(--green-dim);font-family:'VT323',monospace;font-size:15px;text-align:center;
  }
  .handle{color:var(--green-bright);font-size:12px;margin-bottom:6px;}
  .profile-label{
    font-family:'VT323',monospace;
    color:var(--green);
    font-size:16px;
    text-decoration:underline;
    text-underline-offset:3px;
  }
  .name{color:#eafff0;font-size:14px;margin:4px 0;}
  .name b{color:var(--green-bright);}
  .tags{font-size:10px;color:var(--green-dim);line-height:1.6;}

  .btnrow{display:flex;gap:8px;margin-top:8px;}
  .btn{
    background:var(--green-dim);
    color:#03140a;
    border:none;
    font-family:'Space Mono',monospace;
    font-size:10px;
    font-weight:700;
    padding:5px 12px;
    border-radius:2px;
    letter-spacing:.5px;
    cursor:pointer;
  }

  .bio-box{
    margin-top:10px;
    border:1px solid var(--line);
    padding:8px;
    font-size:10.5px;
    color:#bfe9c8;
    line-height:1.5;
  }

  .status-btn{
    margin-top:10px;
    display:inline-block;
    border:1px solid var(--green-dim);
    color:var(--green-bright);
    font-size:10px;
    padding:5px 10px;
    letter-spacing:.5px;
  }

  .grid2{
    display:grid;
    grid-template-columns:1fr 1fr;
    gap:10px;
    margin-top:14px;
  }
  .card{
    border:1px solid var(--line);
    padding:9px;
  }
  .card h4{
    margin:0 0 6px;
    font-size:10px;
    color:var(--green-dim);
    letter-spacing:.5px;
    font-weight:700;
  }
  .card p{margin:0;font-size:10.5px;color:#bfe9c8;line-height:1.5;}

  .interests-title{
    text-align:center;
    margin-top:16px;
  }
  .interests-title .glyphs{color:var(--green);font-size:22px;}
  .interests-title .lbl{font-family:'VT323',monospace;color:#eafff0;font-size:18px;letter-spacing:1px;}

  .interests-box{
    margin-top:10px;
    border:1px solid var(--line);
  }
  .interests-head{
    display:flex;justify-content:space-between;
    padding:6px 10px;
    border-bottom:1px solid var(--line);
    font-size:10px;color:var(--green-dim);
  }
  ul.ilist{list-style:none;margin:0;padding:8px 10px;font-size:11px;color:#d7ffe0;}
  ul.ilist li{padding:3px 0;}
  ul.ilist li:before{content:"☆ ";color:var(--green);}

  .findme{border:1px solid var(--line);padding:10px;text-align:center;}
  .findme .lbl{background:var(--green-dim);color:#03140a;font-size:10px;font-weight:700;padding:4px 10px;display:inline-block;margin-bottom:10px;}
  .icons{display:flex;justify-content:center;gap:12px;margin-bottom:10px;}
  .icons svg{width:16px;height:16px;fill:var(--green-bright);}
  .findme img{width:64px;height:64px;object-fit:cover;border:1px solid var(--line);}

  .bottom2{display:grid;grid-template-columns:1fr 1fr;gap:10px;margin-top:10px;}
  .terminal{
    border:1px solid var(--line);
    padding:8px;
    font-family:'VT323',monospace;
    color:var(--green);
  }
  .terminal .brand{font-size:11px;color:#9fd9a8;margin-bottom:4px;}
  .terminal pre{
    margin:0;font-size:9px;line-height:1;color:var(--green);
    white-space:pre-wrap;
  }
  .terminal .caption{font-size:10px;margin-top:4px;color:#eafff0;}

  .speech{
    border:1px solid var(--line);
    display:flex;
    align-items:center;
    gap:8px;
    padding:8px;
  }
  .speech .face{width:26px;height:26px;background:#111;border:1px solid var(--line);flex-shrink:0;}
  .speech .txt{font-family:'VT323',monospace;color:var(--green-bright);font-size:12px;line-height:1.2;}
  .speech .sub{font-size:9px;color:var(--green-dim);margin-top:2px;font-family:'Space Mono',monospace;}

  .footer{
    text-align:center;
    font-size:9px;
    color:var(--green-dim);
    padding:8px;
    border-top:1px solid var(--line);
  }
</style>
</head>
<body>

<div class="browser">
  <div class="titlebar">
    <div class="dots"><div class="dot"></div><div class="dot"></div><div class="dot"></div></div>
    <div class="addr">amritaa1603.dev</div>
    <div class="search">⌕ search</div>
  </div>

  <div class="stage">
    <canvas id="rain"></canvas>
    <div class="content">

      <div class="top">
        <div class="avatar">[ photo ]</div>
        <div>
          <div class="handle">@amritaa1603</div>
          <div class="profile-label">My Profile</div>
          <div class="name"><b>Amrita</b> · CSE @ VIT Bhopal</div>
          <div class="tags">Cybersecurity · AppSec · SOC (enthusiast) · She/Her</div>
          <div class="btnrow">
            <button class="btn">connect</button>
            <button class="btn">resume</button>
          </div>
        </div>
      </div>

      <div class="bio-box">
        Building JWT auth, RBAC and IDS/IPS pipelines by day, chasing CTF flags and
        PortSwigger labs by night. Currently hunting for AppSec / Security Engineering roles.
      </div>

      <div class="status-btn">◉ status: hardening a codebase...</div>

      <div class="grid2">
        <div class="card">
          <h4>WHAT I'M ABOUT</h4>
          <p>OWASP fundamentals, clean write-ups, sharing what I break and fix, asking good questions.</p>
        </div>
        <div class="card">
          <h4>NOT INTO</h4>
          <p>Skipping the basics, shipping without threat-modelling, security theatre.</p>
        </div>
      </div>

      <div class="interests-title">
        <div class="glyphs">✦</div>
        <div class="lbl">MY INTERESTS</div>
      </div>

      <div class="interests-box">
        <div class="interests-head"><span>MY INTERESTS</span><span>&lt;3</span></div>
        <ul class="ilist">
          <li>OWASP Top 10 &amp; web app pentesting</li>
          <li>TryHackMe &amp; PortSwigger labs</li>
          <li>ML for intrusion detection</li>
          <li>SOC workflows &amp; log analysis</li>
          <li>CTFs &amp; write-ups</li>
        </ul>
      </div>

      <div class="grid2" style="margin-top:10px;">
        <div class="findme">
          <div class="lbl">FIND ME ON</div>
          <div class="icons">
            <a href="https://github.com/amritaa1603" title="GitHub"><svg viewBox="0 0 24 24"><path d="M12 .5C5.73.5.5 5.74.5 12.02c0 5.02 3.29 9.28 7.86 10.79.57.1.79-.25.79-.55v-2.1c-3.2.7-3.87-1.36-3.87-1.36-.53-1.33-1.29-1.69-1.29-1.69-1.05-.72.08-.71.08-.71 1.17.08 1.78 1.2 1.78 1.2 1.03 1.77 2.71 1.26 3.37.97.1-.75.4-1.26.73-1.55-2.55-.29-5.24-1.28-5.24-5.69 0-1.26.45-2.29 1.19-3.09-.12-.29-.52-1.47.11-3.06 0 0 .97-.31 3.18 1.18a10.98 10.98 0 0 1 5.79 0c2.2-1.49 3.17-1.18 3.17-1.18.64 1.59.24 2.77.12 3.06.74.8 1.19 1.83 1.19 3.09 0 4.42-2.7 5.39-5.27 5.68.42.36.78 1.07.78 2.16v3.2c0 .3.21.66.8.55 4.56-1.52 7.85-5.78 7.85-10.8C23.5 5.74 18.27.5 12 .5Z"/></svg></a>
            <a href="https://www.linkedin.com/in/amrita-jadhav-3ba11728a/" title="LinkedIn"><svg viewBox="0 0 24 24"><path d="M20.45 20.45h-3.55v-5.57c0-1.33-.02-3.03-1.85-3.03-1.85 0-2.14 1.45-2.14 2.94v5.66H9.36V9h3.41v1.56h.05c.47-.9 1.63-1.85 3.36-1.85 3.6 0 4.27 2.37 4.27 5.45v6.29ZM5.34 7.43a2.06 2.06 0 1 1 0-4.12 2.06 2.06 0 0 1 0 4.12ZM7.12 20.45H3.56V9h3.56v11.45Z"/></svg></a>
            <a href="mailto:amritajdhv16033@gmail.com" title="Email"><svg viewBox="0 0 24 24"><path d="M2 5.5A1.5 1.5 0 0 1 3.5 4h17A1.5 1.5 0 0 1 22 5.5v13a1.5 1.5 0 0 1-1.5 1.5h-17A1.5 1.5 0 0 1 2 18.5v-13Zm2.2.5 7.8 6.1L19.8 6H4.2Zm15.8 2.1-7.4 5.8a1 1 0 0 1-1.2 0L4 8.1V18h16V8.1Z"/></svg></a>
            <a href="https://amrita1603-portfolio.vercel.app" title="Portfolio"><svg viewBox="0 0 24 24"><path d="M12 2 1 12l3 3 8-8 8 8 3-3L12 2Zm-7 9v9h4v-6h6v6h4v-9l-7-7-7 7Z"/></svg></a>
          </div>
        </div>
        <div class="terminal">
          <div class="brand">SEC://TERMINAL</div>
          <pre>▄▄▄▄▄▄▄▄▄▄▄
█ nmap -sV █
█ status:  █
█  scanning█
▀▀▀▀▀▀▀▀▀▀▀</pre>
          <div class="caption">running recon...</div>
        </div>
      </div>

      <div class="speech" style="margin-top:10px;">
        <div class="face"></div>
        <div>
          <div class="txt">"time to check the CVE feed."</div>
          <div class="sub">last commit: 2 hours ago</div>
        </div>
      </div>

    </div>
  </div>

  <div class="footer">( built by amrita · themed profile page )</div>
</div>

<script>
const canvas = document.getElementById('rain');
const ctx = canvas.getContext('2d');
const container = canvas.parentElement;

function resize(){
  canvas.width = container.clientWidth;
  canvas.height = container.clientHeight;
}
resize();
window.addEventListener('resize', resize);

const chars = "01ABCDEFアイウエオカキクケコ$#@&%".split("");
const fontSize = 12;
let columns = Math.floor(canvas.width / fontSize);
let drops = new Array(columns).fill(1);

function draw(){
  ctx.fillStyle = "rgba(5,8,5,0.15)";
  ctx.fillRect(0,0,canvas.width,canvas.height);
  ctx.fillStyle = "#3ef23e";
  ctx.font = fontSize + "px monospace";
  for(let i=0;i<drops.length;i++){
    const text = chars[Math.floor(Math.random()*chars.length)];
    ctx.fillText(text, i*fontSize, drops[i]*fontSize);
    if(drops[i]*fontSize > canvas.height && Math.random() > 0.975){
      drops[i] = 0;
    }
    drops[i]++;
  }
}
setInterval(draw, 60);
</script>

</body>
</html>
