# qwertyuiooiuytrsasrtyuiopoiuytrewertyui543ertyuicvbnmnbvdtyujnbvcdtyujhvcdrtyujnbvfrtyuydsxcvbnmjhgfdertyuytrsxcvbnjhgfdrtyuhgfvbnmmcxdftygfdsw4rdszzdfbvcdrtyhjkliuhgfdserthjkiuytfdsert
be calm
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Midnight Desktop - Fixed Volume Edition</title>
    <style>
        :root {
            --monitor-frame: #1a1a1a;
            --screen-idle: #050505;
            --accent-glow: #bc13fe; 
        }

        @keyframes rgb-cycle {
            0% { --accent-glow: #bc13fe; }
            20% { --accent-glow: #ff0055; }
            40% { --accent-glow: #ffaa00; }
            60% { --accent-glow: #00ff88; }
            80% { --accent-glow: #00d4ff; }
            100% { --accent-glow: #bc13fe; }
        }

        body {
            margin: 0; height: 100vh; background-color: #050505;
            display: flex; justify-content: center; align-items: flex-end;
            font-family: 'Segoe UI', sans-serif; overflow: hidden;
            user-select: none; animation: rgb-cycle 10s infinite linear;
        }

        .room {
            position: relative; width: 100%; height: 100%;
            display: flex; justify-content: center; align-items: center;
            background-image: 
                radial-gradient(circle at 50% 50%, rgba(0,0,0,0) 20%, #050505 100%),
                radial-gradient(circle at 50% 50%, var(--accent-glow) 0%, transparent 60%),
                linear-gradient(30deg, #0f0f1a 12%, transparent 12.5%, transparent 87%, #0f0f1a 87.5%, #0f0f1a),
                linear-gradient(150deg, #0f0f1a 12%, transparent 12.5%, transparent 87%, #0f0f1a 87.5%, #0f0f1a),
                linear-gradient(60deg, #161625 25%, transparent 25.5%, transparent 75%, #161625 75%, #161625);
            background-size: 100% 100%, 100% 100%, 80px 140px, 80px 140px, 80px 140px;
        }

        .desk-surface {
            position: absolute; bottom: 0; width: 100%; height: 60px;
            background: #080808; border-top: 3px solid var(--accent-glow);
            box-shadow: 0 -10px 30px var(--accent-glow); opacity: 0.8;
        }

        .monitor-container { position: relative; z-index: 10; display: flex; flex-direction: column; align-items: center; }
        .monitor-frame { width: 650px; height: 400px; background: var(--monitor-frame); padding: 15px; border-radius: 12px; border: 2px solid #333; }
        .screen { width: 100%; height: 100%; background: var(--screen-idle); border-radius: 4px; position: relative; overflow: hidden; display: flex; flex-direction: column; }
        
        .desktop-area { flex: 1; position: relative; background: linear-gradient(to bottom, #0a0b1e, #16213e); background-size: cover; background-position: center; }

        .folder-icon { position: absolute; top: 30px; right: 30px; display: flex; flex-direction: column; align-items: center; cursor: pointer; color: white; transition: 0.2s; z-index: 5; }
        .folder-emoji { font-size: 50px; }
        .folder-text { font-size: 14px; font-weight: bold; margin-top: 5px; text-shadow: 0 0 10px var(--accent-glow), 0 2px 4px black; }

        .taskbar { height: 40px; background: rgba(0,0,0,0.9); display: flex; align-items: center; padding: 0 15px; gap: 15px; border-top: 1px solid rgba(255,255,255,0.1); z-index: 1000; }
        .app-icon { width: 28px; height: 28px; cursor: pointer; transition: 0.2s; display: flex; align-items: center; justify-content: center; font-size: 20px; }
        .app-icon:hover { transform: scale(1.2) translateY(-3px); }

        .window { position: absolute; top: 10px; left: 10px; right: 10px; bottom: 10px; background: #000; border-radius: 8px; display: none; flex-direction: column; border: 1px solid #444; box-shadow: 0 15px 40px rgba(0,0,0,0.9); z-index: 500; }
        .win-header { padding: 8px 15px; background: #1a1a1a; display: flex; justify-content: space-between; font-size: 12px; color: #eee; border-bottom: 1px solid #333; align-items: center; }
        .close-btn { cursor: pointer; color: #ff5f56; font-weight: bold; font-size: 14px; }
        .win-body { flex: 1; padding: 15px; color: white; overflow-y: auto; }

        #system-tray { margin-left: auto; display: flex; flex-direction: column; align-items: flex-end; gap: 2px; }
        #live-clock { font-size: 11px; color: #fff; font-family: monospace; font-weight: bold; }
        #live-date { font-size: 9px; color: #aaa; }

        .btn { background: #4ea8de; border: none; color: white; padding: 8px 15px; border-radius: 5px; cursor: pointer; font-weight: bold; }
        
        /* HELP STYLING */
        .help-section { background: rgba(255,255,255,0.05); padding: 10px; border-radius: 6px; margin-bottom: 10px; border-left: 3px solid var(--accent-glow); }
        .help-section h4 { margin: 0 0 5px 0; color: #4ea8de; font-size: 14px; }
        .help-section p { margin: 0; font-size: 12px; color: #ccc; line-height: 1.4; }

        /* GARDEN GAME UI */
        .garden-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 20px; padding: 20px; justify-items: center; }
        .pot { width: 80px; height: 80px; background: #2b1d0e; border-radius: 50%; border: 4px solid #3d2b1f; cursor: pointer; display: flex; align-items: center; justify-content: center; font-size: 40px; transition: 0.3s; position: relative; }
        .pot:hover { transform: scale(1.1); border-color: var(--accent-glow); }
        .water-bar { position: absolute; bottom: -10px; width: 100%; height: 5px; background: #555; border-radius: 5px; overflow: hidden; }
        .water-fill { height: 100%; background: #4ea8de; width: 0%; transition: width 0.3s; }

        .game-canvas { flex: 1; background: #000; position: relative; overflow: hidden; }
        canvas { display: block; width: 100%; height: 100%; }
        .star { position: absolute; width: 2px; height: 2px; background: white; border-radius: 50%; }
        .drop { position: absolute; background: rgba(255,255,255,0.4); width: 1px; height: 12px; }
        .leaf { position: absolute; font-size: 18px; pointer-events: none; transition: 2.5s ease-out; }

        .monitor-stand { width: 60px; height: 50px; background: #111; }
        .monitor-base { width: 220px; height: 12px; background: #000; border-radius: 20px 20px 0 0; box-shadow: 0 -2px 20px var(--accent-glow); }
        #file-input { display: none; }
    </style>
</head>
<body onload="checkSavedWallpaper()">

<audio id="bgMusic" loop><source src="https://www.soundhelix.com/examples/mp3/SoundHelix-Song-1.mp3" type="audio/mpeg"></audio>

<div class="room">
    <div class="monitor-container">
        <div class="monitor-frame">
            <div class="screen">
                <div class="desktop-area" id="desktop">
                    
                    <div class="folder-icon" onclick="openApp('wallpaper-win')">
                        <span class="folder-emoji">📁</span>
                        <span class="folder-text">Wallpapers</span>
                    </div>

                    <div id="settings-win" class="window">
                        <div class="win-header"><span>Settings & Manual</span><span class="close-btn" onclick="closeApp('settings-win')">✖</span></div>
                        <div class="win-body">
                            <h3 style="margin-top:0;">⚙️ System Controls</h3>
                            <div style="display:flex; align-items:center; gap:10px; margin-bottom:10px;">
                                <button class="btn" onclick="toggleMusic()" id="musicBtn">Play Music</button>
                                <span style="font-size:12px;">Vol:</span>
                                <input type="range" min="0" max="1" step="0.05" value="0.5" oninput="updateVolume(this.value)" style="cursor:pointer;">
                            </div>
                            <button class="btn" style="background:#e63946" onclick="resetWallpaper()">Reset Wallpaper</button>
                            
                            <hr style="border:0; border-top: 1px solid #333; margin: 20px 0;">
                            
                            <h3>📖 How To Play</h3>
                            
                            <div class="help-section">
                                <h4>🌻 Midnight Garden</h4>
                                <p>Click empty brown pots to plant. Click growing plants to water. Harvest when they turn into <b>Gold Sunflowers</b>!</p>
                            </div>

                            <div class="help-section">
                                <h4>🎨 Midnight Sketch</h4>
                                <p>Click and drag your mouse to draw neon lines.</p>
                            </div>

                            <div class="help-section">
                                <h4>🧩 Logic Tiles</h4>
                                <p>Click tiles to cycle colors and make your own patterns.</p>
                            </div>
                        </div>
                    </div>

                    <div id="garden-win" class="window">
                        <div class="win-header"><span>Midnight Garden</span><span class="close-btn" onclick="closeApp('garden-win')">✖</span></div>
                        <div class="win-body">
                            <div style="text-align: center; margin-bottom: 10px;">
                                <span style="font-size: 18px; font-weight: bold;">Score: <span id="gardenScore">0</span></span>
                            </div>
                            <div class="garden-grid">
                                <div class="pot" onclick="handleGarden(0)" id="pot0"></div>
                                <div class="pot" onclick="handleGarden(1)" id="pot1"></div>
                                <div class="pot" onclick="handleGarden(2)" id="pot2"></div>
                                <div class="pot" onclick="handleGarden(3)" id="pot3"></div>
                                <div class="pot" onclick="handleGarden(4)" id="pot4"></div>
                                <div class="pot" onclick="handleGarden(5)" id="pot5"></div>
                            </div>
                        </div>
                    </div>

                    <div id="wallpaper-win" class="window">
                        <div class="win-header"><span>Wallpapers</span><span class="close-btn" onclick="closeApp('wallpaper-win')">✖</span></div>
                        <div class="win-body" style="text-align:center;">
                            <label for="file-input" class="btn">📁 Choose Image</label>
                            <input type="file" id="file-input" accept="image/*" onchange="uploadWallpaper(event)">
                        </div>
                    </div>

                    <div id="star-win" class="window"><div class="win-header"><span>StarWeave.sys</span><span class="close-btn" onclick="closeApp('star-win')">✖</span></div><div class="game-canvas" onclick="addStar(event)"></div></div>
                    <div id="neon-win" class="window"><div class="win-header"><span>NEON_GROW.app</span><span class="close-btn" onclick="closeApp('neon-win')">✖</span></div><div id="neon-game" class="game-canvas" onclick="growNeon(event)"></div></div>
                    <div id="rain-win" class="window"><div class="win-header"><span>RAIN_CHILL.exe</span><span class="close-btn" onclick="closeApp('rain-win')">✖</span></div><div id="rain-game" class="game-canvas" onclick="toggleRain()"></div></div>
                    <div id="sketch-win" class="window"><div class="win-header"><span>MidnightSketch.pad</span><span class="close-btn" onclick="closeApp('sketch-win')">✖</span></div><div class="game-canvas"><canvas id="sketchCanvas"></canvas></div></div>
                    <div id="logic-win" class="window"><div class="win-header"><span>LogicTiles.bin</span><span class="close-btn" onclick="closeApp('logic-win')">✖</span></div><div id="logic-game" class="game-canvas" style="padding:20px; text-align:center;"></div></div>
                    <div id="breeze-win" class="window"><div class="win-header"><span>Breeze.toy</span><span class="close-btn" onclick="closeApp('breeze-win')">✖</span></div><div id="breeze-game" class="game-canvas" onclick="spawnLeaf(event)"></div></div>
                </div>

                <div class="taskbar">
                    <span class="app-icon" onclick="openApp('settings-win')">⚙️</span>
                    <span class="app-icon" onclick="openApp('garden-win')">🌻</span>
                    <span class="app-icon" onclick="openApp('star-win')">✨</span>
                    <span class="app-icon" onclick="openApp('neon-win')">🌵</span>
                    <span class="app-icon" onclick="openApp('rain-win')">🌧️</span>
                    <span class="app-icon" onclick="openApp('sketch-win')">🎨</span>
                    <span class="app-icon" onclick="openApp('logic-win')">🧩</span>
                    <span class="app-icon" onclick="openApp('breeze-win')">🍃</span>
                    <div id="system-tray">
                        <div id="live-clock">12:00:00 AM</div>
                        <div id="live-date">Jan 01, 2026</div>
                    </div>
                </div>
            </div>
        </div>
        <div class="monitor-stand"></div><div class="monitor-base"></div>
    </div>
    <div class="desk-surface"></div>
</div>

<script>
    const music = document.getElementById('bgMusic');
    let isPlaying = false;
    let gardenScore = 0;
    let pots = Array(6).fill().map(() => ({ state: 'empty', water: 0, stage: 0 }));

    // GARDEN LOGIC
    function handleGarden(idx) {
        let p = pots[idx];
        let el = document.getElementById('pot' + idx);
        if (p.state === 'empty') {
            p.state = 'growing'; p.water = 100; p.stage = 1;
            el.innerHTML = '🌱<div class="water-bar"><div class="water-fill" id="w'+idx+'" style="width:100%"></div></div>';
        } else if (p.state === 'growing') {
            p.water = Math.min(p.water + 30, 100);
        } else if (p.state === 'ready') {
            gardenScore += 10;
            document.getElementById('gardenScore').innerText = gardenScore;
            p.state = 'empty'; p.water = 0; p.stage = 0;
            el.innerHTML = ''; el.style.filter = 'none';
        }
    }

    setInterval(() => {
        pots.forEach((p, idx) => {
            if (p.state === 'growing') {
                p.water -= 1.5;
                if (p.water <= 0) {
                    p.state = 'empty'; p.stage = 0;
                    document.getElementById('pot'+idx).innerHTML = '';
                } else {
                    document.getElementById('w'+idx).style.width = p.water + '%';
                    p.stage += 0.02;
                    let el = document.getElementById('pot' + idx);
                    if (p.stage > 5) {
                        p.state = 'ready'; el.innerHTML = '🌻'; el.style.filter = 'drop-shadow(0 0 10px gold)';
                    } else if (p.stage > 3) { el.firstChild.textContent = '🌿'; }
                }
            }
        });
    }, 1000);

    // TIME
    function updateDateTime() {
        const now = new Date();
        let h = now.getHours(), m = now.getMinutes(), s = now.getSeconds(), ampm = h >= 12 ? 'PM' : 'AM';
        h = h % 12 || 12;
        m = m < 10 ? '0' + m : m; s = s < 10 ? '0' + s : s;
        document.getElementById('live-clock').innerText = `${h}:${m}:${s} ${ampm}`;
        document.getElementById('live-date').innerText = now.toLocaleDateString('en-US', { month: 'short', day: '2-digit', year: 'numeric' });
    }
    setInterval(updateDateTime, 1000); updateDateTime();

    // SYSTEM
    function uploadWallpaper(e) {
        const file = e.target.files[0];
        if (file) {
            const reader = new FileReader();
            reader.onload = ev => {
                document.getElementById('desktop').style.backgroundImage = `url('${ev.target.result}')`;
                localStorage.setItem('userWallpaper', ev.target.result);
            };
            reader.readAsDataURL(file);
        }
    }
    function checkSavedWallpaper() {
        const saved = localStorage.getItem('userWallpaper');
        if (saved) document.getElementById('desktop').style.backgroundImage = `url('${saved}')`;
    }
    function resetWallpaper() {
        localStorage.removeItem('userWallpaper');
        document.getElementById('desktop').style.backgroundImage = "linear-gradient(to bottom, #0a0b1e, #16213e)";
    }
    function toggleMusic() {
        if (isPlaying) { music.pause(); document.getElementById('musicBtn').innerText = "Play Music"; }
        else { music.play(); document.getElementById('musicBtn').innerText = "Stop Music"; }
        isPlaying = !isPlaying;
    }
    function updateVolume(val) { music.volume = val; }

    function openApp(id) {
        document.querySelectorAll('.window').forEach(w => w.style.display = 'none');
        document.getElementById(id).style.display = 'flex';
        if(id === 'sketch-win') initSketch();
        if(id === 'logic-win') initLogic();
    }
    function closeApp(id) { document.getElementById(id).style.display = 'none'; }

    // TOYS
    function addStar(e) {
        const s = document.createElement('div'); s.className = 'star';
        s.style.left = e.offsetX + 'px'; s.style.top = e.offsetY + 'px';
        e.currentTarget.appendChild(s);
        setTimeout(() => s.remove(), 5000);
    }
    function growNeon(e) {
        const p = document.createElement('div'); p.style.position = 'absolute'; p.style.bottom = '0';
        p.style.left = e.offsetX + 'px'; p.style.width = '3px'; p.style.height = '0px';
        const c = `hsl(${Math.random()*360}, 80%, 60%)`;
        p.style.background = c; p.style.boxShadow = `0 0 15px ${c}`; p.style.transition = 'height 1.5s';
        e.currentTarget.appendChild(p);
        setTimeout(() => p.style.height = (Math.random()*180 + 40) + 'px', 50);
    }
    let rainInterval = null;
    function toggleRain() {
        const container = document.getElementById('rain-game');
        if(rainInterval) { clearInterval(rainInterval); rainInterval = null; container.innerHTML = ""; }
        else { rainInterval = setInterval(() => {
            const d = document.createElement('div'); d.className = 'drop';
            d.style.left = Math.random()*100+'%'; d.style.top = '-20px';
            container.appendChild(d);
            const anim = d.animate([{ top: '-20px' }, { top: '400px' }], { duration: 500 });
            anim.onfinish = () => d.remove();
        }, 40); }
    }
    function initSketch() {
        const canvas = document.getElementById('sketchCanvas'); const ctx = canvas.getContext('2d');
        const rect = canvas.parentElement.getBoundingClientRect();
        canvas.width = rect.width; canvas.height = rect.height;
        let drawing = false;
        canvas.onmousedown = (e) => { drawing = true; ctx.beginPath(); ctx.moveTo(e.offsetX, e.offsetY); };
        canvas.onmouseup = () => drawing = false;
        canvas.onmousemove = (e) => {
            if(!drawing) return; ctx.lineWidth = 3; ctx.lineCap = 'round'; 
            ctx.strokeStyle = getComputedStyle(document.body).getPropertyValue('--accent-glow');
            ctx.lineTo(e.offsetX, e.offsetY); ctx.stroke();
        };
    }
    function initLogic() {
        const g = document.getElementById('logic-game'); g.innerHTML = "";
        const colors = ['#bc13fe', '#4ea8de', '#00f2ff', '#ff00ff', '#00ff88'];
        for(let i=0; i<15; i++) {
            const t = document.createElement('div'); t.className = 'tile';
            t.style.backgroundColor = colors[Math.floor(Math.random()*colors.length)];
            t.onclick = () => t.style.backgroundColor = colors[Math.floor(Math.random()*colors.length)];
            g.appendChild(t);
        }
    }
    function spawnLeaf(e) {
        const l = document.createElement('div'); l.className = 'leaf';
        l.innerText = '🍃'; l.style.left = e.offsetX + 'px'; l.style.top = e.offsetY + 'px';
        e.currentTarget.appendChild(l);
        setTimeout(() => { l.style.transform = `translate(400px, 100px) rotate(180deg)`; l.style.opacity = '0'; }, 50);
        setTimeout(() => l.remove(), 2600);
    }
</script>

</body>
</html>
