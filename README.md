<img src="https://i.pinimg.com/originals/42/b4/22/42b4229a9ec3145edaa895b2415dd720.gif" alt="Banner" width="100%" />

<!doctype html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <meta name="theme-color" content="#08090b" />
  <title>Lionell — Interactive Space</title>
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
  <link href="https://fonts.googleapis.com/css2?family=DM+Mono:wght@400;500&family=Manrope:wght@400;500;600;700;800&display=swap" rel="stylesheet" />
  <style>
    :root { --bg:#08090b; --panel:rgba(20,22,27,.72); --line:rgba(255,255,255,.13); --muted:#8f96a3; --text:#f3f5f7; --accent:#b8c8ff; --accent2:#849aff; }
    * { box-sizing:border-box; margin:0; }
    html { scroll-behavior:smooth; }
    body { min-height:100vh; overflow-x:hidden; color:var(--text); background:var(--bg); font-family:Manrope,system-ui,sans-serif; }
    body:before { content:""; position:fixed; inset:0; z-index:-3; background:radial-gradient(circle at 75% 22%,rgba(99,118,255,.16),transparent 30%), radial-gradient(circle at 15% 80%,rgba(62,78,122,.15),transparent 28%), linear-gradient(135deg,#08090b 0%,#12151b 48%,#07080a 100%); }
    body:after { content:""; position:fixed; inset:0; z-index:-2; opacity:.24; pointer-events:none; background-image:linear-gradient(rgba(255,255,255,.04) 1px,transparent 1px),linear-gradient(90deg,rgba(255,255,255,.04) 1px,transparent 1px); background-size:72px 72px; mask-image:linear-gradient(to bottom,black,transparent 80%); }
    a { color:inherit; text-decoration:none; }
    button { font:inherit; }
    .topbar { position:fixed; top:0; left:0; right:0; z-index:20; display:flex; justify-content:space-between; align-items:center; padding:22px 5vw; pointer-events:none; }
    .brand,.topbar button { pointer-events:auto; }
    .brand { display:flex; align-items:center; gap:12px; font-size:12px; font-weight:800; letter-spacing:.18em; text-transform:uppercase; }
    .brand-mark { width:29px; height:29px; display:grid; place-items:center; border:1px solid var(--line); border-radius:50%; color:#0b0d11; background:linear-gradient(145deg,#fff,#a5b5ff); box-shadow:0 0 24px rgba(141,163,255,.4); }
    .topbar button,.pill,.control,.social-card { border:1px solid var(--line); background:rgba(9,11,15,.54); color:var(--text); backdrop-filter:blur(18px); -webkit-backdrop-filter:blur(18px); }
    .topbar button { display:flex; align-items:center; gap:9px; padding:10px 14px; border-radius:999px; cursor:pointer; font-size:12px; color:var(--muted); transition:.25s ease; }
    .topbar button:hover { color:var(--text); border-color:rgba(255,255,255,.3); }
    .sound-dot { width:7px; height:7px; border-radius:50%; background:#7dffbe; box-shadow:0 0 14px #7dffbe; }
    .hero { min-height:100vh; max-width:1400px; margin:auto; padding:130px 5vw 72px; display:grid; grid-template-columns:minmax(0,.84fr) minmax(430px,1.16fr); align-items:center; gap:2vw; }
    .eyebrow { display:inline-flex; align-items:center; gap:10px; color:var(--muted); font-family:'DM Mono',monospace; font-size:11px; letter-spacing:.1em; text-transform:uppercase; }
    .eyebrow:before { content:""; width:27px; height:1px; background:var(--accent); box-shadow:0 0 12px var(--accent); }
    h1 { max-width:680px; margin:22px 0 23px; font-size:clamp(3.4rem,7vw,7rem); line-height:.94; letter-spacing:-.075em; font-weight:800; }
    h1 span { color:var(--accent); text-shadow:0 0 35px rgba(132,154,255,.42); }
    .lede { max-width:480px; color:var(--muted); font-size:16px; line-height:1.8; }
    .actions { display:flex; flex-wrap:wrap; gap:12px; margin-top:30px; }
    .pill { display:inline-flex; align-items:center; gap:9px; padding:13px 17px; border-radius:10px; cursor:pointer; font-size:12px; transition:.25s ease; }
    .pill.primary { color:#0b0d12; border:0; background:linear-gradient(135deg,#f0f3ff,#aebeff); box-shadow:0 8px 28px rgba(132,154,255,.25); font-weight:800; }
    .pill:hover { transform:translateY(-2px); }
    .metrics { display:flex; gap:28px; margin-top:52px; }
    .metric strong { display:block; margin-bottom:4px; font-size:18px; }
    .metric small { color:var(--muted); font-family:'DM Mono',monospace; font-size:10px; text-transform:uppercase; letter-spacing:.08em; }
    .scene-shell { position:relative; min-height:590px; border:1px solid var(--line); border-radius:28px; overflow:hidden; background:linear-gradient(145deg,rgba(255,255,255,.06),rgba(255,255,255,.015)); box-shadow:0 30px 100px rgba(0,0,0,.42),inset 0 1px rgba(255,255,255,.11); }
    #scene { display:block; width:100%; height:590px; cursor:grab; }
    #scene:active { cursor:grabbing; }
    .scene-label { position:absolute; top:22px; left:24px; color:var(--muted); font-family:'DM Mono',monospace; font-size:10px; letter-spacing:.12em; text-transform:uppercase; pointer-events:none; }
    .scene-label b { color:#dce4ff; font-weight:400; }
    .scene-hint { position:absolute; bottom:22px; left:24px; color:rgba(255,255,255,.5); font-family:'DM Mono',monospace; font-size:10px; }
    .scene-hint kbd { padding:3px 5px; border:1px solid var(--line); border-radius:4px; color:var(--text); }
    .controls { position:absolute; right:20px; bottom:18px; display:flex; gap:8px; }
    .control { width:34px; height:34px; display:grid; place-items:center; border-radius:9px; color:var(--muted); cursor:pointer; transition:.2s; }
    .control:hover { color:var(--text); border-color:rgba(255,255,255,.35); }
    .swatches { display:flex; gap:6px; margin-top:24px; }
    .swatch { width:17px; height:17px; border-radius:50%; border:1px solid rgba(255,255,255,.35); cursor:pointer; transition:.2s; }
    .swatch:hover,.swatch.active { transform:scale(1.22); box-shadow:0 0 0 3px rgba(255,255,255,.12); }
    .social-section { max-width:1100px; margin:auto; padding:90px 5vw 120px; }
    .section-head { display:flex; justify-content:space-between; align-items:end; gap:20px; margin-bottom:26px; }
    .section-head h2 { font-size:clamp(2rem,4vw,3.7rem); letter-spacing:-.06em; }
    .section-head p { max-width:350px; color:var(--muted); font-size:13px; line-height:1.7; }
    .social-grid { display:grid; grid-template-columns:repeat(4,1fr); gap:12px; }
    .social-card { position:relative; min-height:150px; display:flex; flex-direction:column; justify-content:space-between; padding:18px; border-radius:16px; overflow:hidden; transition:.25s; }
    .social-card:after { content:""; position:absolute; width:150px; height:150px; right:-65px; bottom:-90px; border-radius:50%; background:var(--card-accent,#94a8ff); filter:blur(35px); opacity:.22; }
    .social-card:hover { transform:translateY(-5px); border-color:rgba(255,255,255,.32); background:rgba(34,37,47,.72); }
    .social-top { display:flex; justify-content:space-between; color:var(--muted); font-family:'DM Mono',monospace; font-size:11px; }
    .social-card strong { font-size:16px; }
    .social-card small { color:var(--muted); font-size:11px; }
    footer { padding:30px 5vw 42px; border-top:1px solid var(--line); color:#696f7c; font-family:'DM Mono',monospace; font-size:10px; letter-spacing:.1em; text-transform:uppercase; }
    @media (max-width:900px) { .hero { grid-template-columns:1fr; padding-top:120px; } .scene-shell,#scene { min-height:500px; height:500px; } .social-grid { grid-template-columns:repeat(2,1fr); } }
    @media (max-width:560px) { .topbar { padding:18px 20px; } .hero,.social-section { padding-left:20px; padding-right:20px; } h1 { font-size:clamp(3.15rem,16vw,5rem); } .hero { padding-top:105px; } .scene-shell,#scene { min-height:420px; height:420px; border-radius:20px; } .metrics { gap:18px; margin-top:38px; } .social-grid { grid-template-columns:1fr 1fr; } .social-card { min-height:135px; padding:14px; } .section-head { display:block; } .section-head p { margin-top:12px; } }
    @media (prefers-reduced-motion:reduce) { *,*:before,*:after { scroll-behavior:auto!important; transition:none!important; animation:none!important; } }
  </style>
</head>
<body>
  <header class="topbar">
    <a class="brand" href="#top"><span class="brand-mark">L</span> Lionell</a>
    <button id="soundToggle" type="button" aria-pressed="false"><span class="sound-dot"></span>online</button>
  </header>

  <main id="top">
    <section class="hero">
      <div class="intro">
        <h1>Website<br /><span>lionell.</span></h1>
        <p class="lede">aku lionell shawn manik, aku dari medan indonesia, aku suka it makanya aku buat web ini, dm aku di ig kalau mau buat web.</p>
        <div class="actions"><a href="#connect" class="pill primary">Explore the links <span>↗</span></a><button class="pill" id="randomize" type="button">ganti warna <span>✦</span></button></div>
        <div class="metrics"><div class="metric"><strong></strong><small></small></div><div class="metric"><strong></strong><small></small></div><div class="metric"><strong></strong><small></small></div></div>
      </div>
      <div class="scene-shell">
        <div class="scene-label">Object 001 <b>/ chrome bloom</b></div>
        <canvas id="scene" aria-label="Interactive 3D chrome object. Drag to rotate, scroll to zoom."></canvas>
        <div class="scene-hint"><kbd>drag</kbd> rotate &nbsp; <kbd>scroll</kbd> zoom</div>
        <div class="controls"><button class="control" id="reset" title="Reset view" aria-label="Reset view">↺</button><button class="control" id="spin" title="Toggle auto rotation" aria-label="Toggle auto rotation">◌</button></div>
      </div>
    </section>

    <section class="social-section" id="connect">
      <div class="section-head"><div><div class="eyebrow">Find me elsewhere</div><h2>Let’s connect.</h2></div><p></p></div>
      <div class="social-grid">
        <a class="social-card" style="--card-accent:#ff6fae" href="https://instagram.com/eltenze" target="_blank" rel="noopener noreferrer"><div class="social-top"><span>01</span><span>↗</span></div><div><strong>Instagram</strong><br /><small>@eltenze</small></div></a>
        <a class="social-card" style="--card-accent:#78efff" href="https://tiktok.com/@eltenze" target="_blank" rel="noopener noreferrer"><div class="social-top"><span>02</span><span>↗</span></div><div><strong>TikTok</strong><br /><small>@eltenze</small></div></a>
        <a class="social-card" style="--card-accent:#ff4d60" href="https://youtube.com/@eltenze" target="_blank" rel="noopener noreferrer"><div class="social-top"><span>03</span><span>↗</span></div><div><strong>YouTube</strong><br /><small>@eltenze</small></div></a>
        <a class="social-card" style="--card-accent:#ffe04d" href="https://snapchat.com/add/l99cz" target="_blank" rel="noopener noreferrer"><div class="social-top"><span>04</span><span>↗</span></div><div><strong>Snapchat</strong><br /><small>l99cz</small></div></a>
      </div>
    </section>
  </main>
  <footer>© Lionell Shawn Manik <span></span></footer>

  <script src="https://cdn.jsdelivr.net/npm/three@0.160.0/build/three.min.js"></script>
  <script>

    const canvas = document.querySelector('#scene');
    const shell = document.querySelector('.scene-shell');
    const scene = new THREE.Scene();
    scene.add(new THREE.HemisphereLight(0xb8c7ff, 0x080a10, 2.2));
    const keyLight = new THREE.DirectionalLight(0xffffff, 4.5); keyLight.position.set(3, 4, 5); scene.add(keyLight);
    const rimLight = new THREE.PointLight(0x8096ff, 28, 12); rimLight.position.set(-3, 1, 2); scene.add(rimLight);
    const camera = new THREE.PerspectiveCamera(35, 1, .1, 100);
    camera.position.set(0, .2, 5.2);
    const renderer = new THREE.WebGLRenderer({ canvas, antialias:true, alpha:true });
    renderer.setPixelRatio(Math.min(devicePixelRatio, 2));
    renderer.toneMapping = THREE.ACESFilmicToneMapping;
    renderer.toneMappingExposure = 1.25;
    renderer.outputColorSpace = THREE.SRGBColorSpace;
    const controls = { autoRotate:true, autoRotateSpeed:.65, target:new THREE.Vector3(), update(){} };
    let drag=false, lastX=0, lastY=0, distance=5.2;
    canvas.addEventListener('pointerdown', e=>{ drag=true; lastX=e.clientX; lastY=e.clientY; canvas.setPointerCapture(e.pointerId); });
    canvas.addEventListener('pointerup', e=>{ drag=false; canvas.releasePointerCapture(e.pointerId); });
    canvas.addEventListener('pointermove', e=>{ if(!drag) return; group.rotation.y += (e.clientX-lastX)*.008; group.rotation.x += (e.clientY-lastY)*.008; lastX=e.clientX; lastY=e.clientY; });
    canvas.addEventListener('wheel', e=>{ e.preventDefault(); distance=Math.max(3.3,Math.min(7,distance+e.deltaY*.004)); camera.position.z=distance; }, {passive:false});

    const group = new THREE.Group(); scene.add(group);
    const material = new THREE.MeshPhysicalMaterial({ color:0xa9b9ff, metalness:1, roughness:.17, clearcoat:1, clearcoatRoughness:.08, iridescence:.55, iridescenceIOR:1.3 });
    const core = new THREE.Mesh(new THREE.IcosahedronGeometry(1.13, 5), material); group.add(core);
    const ringMat = new THREE.MeshBasicMaterial({ color:0x99a9ff, transparent:true, opacity:.34, blending:THREE.AdditiveBlending });
    const rings = [1.54,1.79,2.02].map((r,i)=>{ const ring = new THREE.Mesh(new THREE.TorusGeometry(r,.008 + i*.004,8,128), ringMat.clone()); ring.rotation.set(i*.7,.3+i*.55,i*.2); group.add(ring); return ring; });
    const points = new THREE.Points(new THREE.SphereGeometry(2.2,38,20), new THREE.PointsMaterial({ color:0xc7d0ff, size:.012, transparent:true, opacity:.5 })); group.add(points);
    const clock = new THREE.Clock(); let pointer={x:0,y:0};
    function resize(){ const rect=shell.getBoundingClientRect(); const w=rect.width,h=rect.height; renderer.setSize(w,h,false); camera.aspect=w/h; camera.updateProjectionMatrix(); }
    new ResizeObserver(resize).observe(shell); resize();
    canvas.addEventListener('pointermove',e=>{ const r=canvas.getBoundingClientRect(); pointer.x=(e.clientX-r.left)/r.width-.5; pointer.y=(e.clientY-r.top)/r.height-.5; });
    function animate(){ const t=clock.getElapsedTime(); if(controls.autoRotate && !drag) group.rotation.y += .0065*controls.autoRotateSpeed; core.rotation.x = Math.sin(t*.45)*.08 + pointer.y*.16; group.rotation.x += (-pointer.y*.12-group.rotation.x)*.018; rings.forEach((r,i)=>{r.rotation.x += (.001+i*.0005); r.rotation.z -= (.0012+i*.0005);}); points.rotation.y-=.00025; controls.update(); renderer.render(scene,camera); requestAnimationFrame(animate); } animate();
    const palettes=[0xa9b9ff,0xff9bd2,0x7dffd4,0xffd27d,0xd7d7ff]; let paletteIndex=0;
    function setColor(hex){ material.color.setHex(hex); ringMat.color.setHex(hex); rings.forEach(r=>r.material.color.setHex(hex)); document.querySelectorAll('.swatch').forEach((s,i)=>s.classList.toggle('active',i===paletteIndex)); }
    document.querySelector('#randomize').addEventListener('click',()=>{ paletteIndex=(paletteIndex+1)%palettes.length; setColor(palettes[paletteIndex]); controls.autoRotate=true; });
    document.querySelector('#reset').addEventListener('click',()=>{ camera.position.set(0,.2,5.2); distance=5.2; group.rotation.set(0,0,0); controls.autoRotate=true; });
    document.querySelector('#spin').addEventListener('click',()=>{ controls.autoRotate=!controls.autoRotate; });
    document.querySelector('#soundToggle').addEventListener('click',()=>{ const btn=document.querySelector('#soundToggle'); const on=btn.getAttribute('aria-pressed')!=='true'; btn.setAttribute('aria-pressed',on); document.querySelector('#soundText').textContent=on?'Ambient ready':'Ambient off'; });
  </script>
</body>
</html>

<div align="center">
  <h3>🌐 Connect with eltenze</h3>

  <p>
    <a href="https://instagram.com/eltenze">
      <img src="https://img.shields.io/badge/Instagram-%23E4405F.svg?style=for-the-badge&logo=Instagram&logoColor=white" style="border-radius: 16px; margin: 4px;" />
    </a>
    <a href="https://tiktok.com/@eltenze">
      <img src="https://img.shields.io/badge/TikTok-%23000000.svg?style=for-the-badge&logo=TikTok&logoColor=white" style="border-radius: 16px; margin: 4px;" />
    </a>
    <a href="https://youtube.com/@eltenze">
      <img src="https://img.shields.io/badge/YouTube-%23FF0000.svg?style=for-the-badge&logo=YouTube&logoColor=white" style="border-radius: 16px; margin: 4px;" />
    </a>
  </p>
</div>
